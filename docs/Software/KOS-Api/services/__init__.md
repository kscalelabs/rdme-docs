# __init__

KOS service clients.

## Classes

### AsyncClientBase (ABC)

Base class for async gRPC clients that automatically adds sync versions of async methods.

#### __init__(self) -> None


## Functions

### add_sync_version(async_func: Callable[..., Coroutine[Any, Any, ~T]]) -> Callable[..., ~T]

Create a synchronous version of an async function.
