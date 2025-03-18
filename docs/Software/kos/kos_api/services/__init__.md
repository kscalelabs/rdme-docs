---
title: __init__
---

# __init__

Help on module __init__:

NAME
    __init__ - KOS service clients.

CLASSES
    abc.ABC(builtins.object)
        AsyncClientBase

    class AsyncClientBase(abc.ABC)
     |  AsyncClientBase() -> None
     |
     |  Base class for async gRPC clients that automatically adds sync versions of async methods.
     |
     |  Method resolution order:
     |      AsyncClientBase
     |      abc.ABC
     |      builtins.object
     |
     |  Methods defined here:
     |
     |  __init__(self) -> None
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  ----------------------------------------------------------------------
     |  Data descriptors defined here:
     |
     |  __dict__
     |      dictionary for instance variables
     |
     |  __weakref__
     |      list of weak references to the object
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |
     |  __abstractmethods__ = frozenset()

FUNCTIONS
    add_sync_version(async_func: Callable[..., Coroutine[Any, Any, ~T]]) -> Callable[..., ~T]
        Create a synchronous version of an async function.

DATA
    Callable = typing.Callable
        Deprecated alias to collections.abc.Callable.

        Callable[[int], str] signifies a function that takes a single
        parameter of type int and returns a str.

        The subscription syntax must always be used with exactly two
        values: the argument list and the return type.
        The argument list must be a list of types, a ParamSpec,
        Concatenate or ellipsis. The return type must be a single type.

        There is no syntax to indicate optional or keyword arguments;
        such function types are rarely used as callback types.

    Coroutine = typing.Coroutine
        A generic version of collections.abc.Coroutine.

    T = ~T

FILE
    /Users/verdakorzeniewski/kscale/kos/kos-py/pykos/services/__init__.py



