# Process Manager Service

The Process Manager Service provides monitoring and control of system processes, allowing for process management, resource monitoring, and system diagnostics.

## Classes

### ProcessInfo (TypedDict)

Information about a running process.

#### Fields

- **pid**: int - Process ID
- **name**: str - Process name
- **command**: str - Command used to launch the process
- **status**: str - Current process status (e.g., "running", "stopped")
- **cpu_percent**: float - CPU usage percentage
- **memory_percent**: float - Memory usage percentage
- **memory_rss**: int - Resident Set Size in bytes
- **memory_vms**: int - Virtual Memory Size in bytes
- **uptime_seconds**: float - Process uptime in seconds
- **threads**: int - Number of threads

### SystemInfo (TypedDict)

Information about the system resources.

#### Fields

- **cpu_percent**: float - Overall CPU usage percentage
- **memory_total**: int - Total physical memory in bytes
- **memory_available**: int - Available physical memory in bytes
- **memory_used**: int - Used physical memory in bytes
- **memory_percent**: float - Memory usage percentage
- **disk_total**: int - Total disk space in bytes
- **disk_used**: int - Used disk space in bytes
- **disk_free**: int - Free disk space in bytes
- **disk_percent**: float - Disk usage percentage
- **temperatures**: dict[str, float] - Temperature sensors readings in °C
- **boot_time**: float - System boot time (Unix timestamp)
- **uptime_seconds**: float - System uptime in seconds

### ProcessManagerServiceClient (AsyncClientBase)

Client for interacting with the Process Manager Service.

#### Methods

##### `__init__(self, channel: grpc.aio.Channel)`

Initialize the process manager service client with a gRPC channel.

##### `get_system_info(self) -> SystemInfo`

Get information about the system resources.

**Returns:**
- SystemInfo containing system resource information

**Example:**
```python
info = await pm_client.get_system_info()
print(f"CPU usage: {info.cpu_percent}%")
print(f"Memory usage: {info.memory_percent}%")
print(f"Free disk space: {info.disk_free / (1024*1024*1024):.2f} GB")
print(f"System uptime: {info.uptime_seconds / 3600:.1f} hours")
```

##### `list_processes(self) -> list[ProcessInfo]`

Get a list of all running processes.

**Returns:**
- List of ProcessInfo objects for each running process

**Example:**
```python
processes = await pm_client.list_processes()
print(f"Running processes: {len(processes)}")

# Find the top 5 CPU-consuming processes
top_cpu = sorted(processes, key=lambda p: p.cpu_percent, reverse=True)[:5]
for proc in top_cpu:
    print(f"{proc.name} (PID {proc.pid}): {proc.cpu_percent}% CPU")
```

##### `get_process_info(self, pid: int) -> ProcessInfo`

Get detailed information about a specific process.

**Parameters:**
- pid: Process ID to query

**Returns:**
- ProcessInfo object for the specified process

**Example:**
```python
info = await pm_client.get_process_info(1234)
print(f"Process: {info.name} (PID {info.pid})")
print(f"Status: {info.status}")
print(f"Memory usage: {info.memory_rss / (1024*1024):.2f} MB")
print(f"CPU usage: {info.cpu_percent}%")
```

##### `kill_process(self, pid: int) -> ActionResult`

Terminate a process by its process ID.

**Parameters:**
- pid: Process ID to terminate

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
result = await pm_client.kill_process(1234)
if result.success:
    print("Process terminated successfully")
else:
    print(f"Failed to terminate process: {result.error.message}")
```

##### `start_process(self, command: str, args: list[str] = [], env: dict[str, str] = {}, working_dir: str = None) -> ProcessInfo`

Start a new process.

**Parameters:**
- command: Command to execute
- args: Command arguments
- env: Environment variables
- working_dir: Working directory for the process

**Returns:**
- ProcessInfo for the newly created process

**Example:**
```python
process = await pm_client.start_process(
    command="python",
    args=["-m", "http.server", "8000"],
    env={"PYTHONUNBUFFERED": "1"},
    working_dir="/tmp"
)
print(f"Started server with PID {process.pid}")
```

##### `get_logs(self, pid: int, max_lines: int = 100) -> list[str]`

Get log output from a specific process.

**Parameters:**
- pid: Process ID
- max_lines: Maximum number of log lines to retrieve

**Returns:**
- List of log lines

**Example:**
```python
logs = await pm_client.get_logs(1234, max_lines=50)
for line in logs:
    print(line)
```

##### `monitor_system(self, interval_seconds: float = 1.0) -> AsyncIterator[SystemInfo]`

Monitor system resources with periodic updates.

**Parameters:**
- interval_seconds: Interval between updates in seconds

**Returns:**
- Async iterator yielding SystemInfo updates

**Example:**
```python
async for update in pm_client.monitor_system(interval_seconds=2.0):
    print(f"CPU: {update.cpu_percent}%, Mem: {update.memory_percent}%")
    
    # Stop after 10 updates
    if some_condition:
        break
```