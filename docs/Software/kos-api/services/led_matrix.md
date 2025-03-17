---
title: led_matrix
---

# led_matrix

Help on module led_matrix:

NAME
    led_matrix - LED Matrix service client.

CLASSES
    builtins.dict(builtins.object)
        ImageData
        MatrixInfo
    pykos.services.AsyncClientBase(abc.ABC)
        LEDMatrixServiceClient

    class ImageData(builtins.dict)
     |  Image data to be written to the LED matrix.
     |
     |  Args:
     |      buffer: Raw image data bytes
     |      width: Image width in pixels
     |      height: Image height in pixels
     |      format: Pixel format specification (e.g. 'RGB888', 'BGR888', 'RGB565', 'MONO8')
     |      brightness: Global brightness level (0-255)
     |
     |  Method resolution order:
     |      ImageData
     |      builtins.dict
     |      builtins.object
     |
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
     |  __annotations__ = {'brightness': <class 'int'>, 'buffer': <class 'byte...
     |
     |  __optional_keys__ = frozenset()
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'brightness', 'buffer', 'format', 'heig...
     |
     |  __total__ = True
     |
     |  ----------------------------------------------------------------------
     |  Methods inherited from builtins.dict:
     |
     |  __contains__(self, key, /)
     |      True if the dictionary has the specified key, else False.
     |
     |  __delitem__(self, key, /)
     |      Delete self[key].
     |
     |  __eq__(self, value, /)
     |      Return self==value.
     |
     |  __ge__(self, value, /)
     |      Return self>=value.
     |
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |
     |  __getitem__(self, key, /)
     |      Return self[key].
     |
     |  __gt__(self, value, /)
     |      Return self>value.
     |
     |  __init__(self, /, *args, **kwargs)
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  __ior__(self, value, /)
     |      Return self|=value.
     |
     |  __iter__(self, /)
     |      Implement iter(self).
     |
     |  __le__(self, value, /)
     |      Return self<=value.
     |
     |  __len__(self, /)
     |      Return len(self).
     |
     |  __lt__(self, value, /)
     |      Return self<value.
     |
     |  __ne__(self, value, /)
     |      Return self!=value.
     |
     |  __or__(self, value, /)
     |      Return self|value.
     |
     |  __repr__(self, /)
     |      Return repr(self).
     |
     |  __reversed__(self, /)
     |      Return a reverse iterator over the dict keys.
     |
     |  __ror__(self, value, /)
     |      Return value|self.
     |
     |  __setitem__(self, key, value, /)
     |      Set self[key] to value.
     |
     |  __sizeof__(...)
     |      D.__sizeof__() -> size of D in memory, in bytes
     |
     |  clear(...)
     |      D.clear() -> None.  Remove all items from D.
     |
     |  copy(...)
     |      D.copy() -> a shallow copy of D
     |
     |  get(self, key, default=None, /)
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  items(...)
     |      D.items() -> a set-like object providing a view on D's items
     |
     |  keys(...)
     |      D.keys() -> a set-like object providing a view on D's keys
     |
     |  pop(...)
     |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
     |
     |      If the key is not found, return the default if given; otherwise,
     |      raise a KeyError.
     |
     |  popitem(self, /)
     |      Remove and return a (key, value) pair as a 2-tuple.
     |
     |      Pairs are returned in LIFO (last-in, first-out) order.
     |      Raises KeyError if the dict is empty.
     |
     |  setdefault(self, key, default=None, /)
     |      Insert key with a value of default if key is not in the dictionary.
     |
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  update(...)
     |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
     |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
     |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
     |      In either case, this is followed by: for k in F:  D[k] = F[k]
     |
     |  values(...)
     |      D.values() -> an object providing a view on D's values
     |
     |  ----------------------------------------------------------------------
     |  Class methods inherited from builtins.dict:
     |
     |  __class_getitem__(...) from typing._TypedDictMeta
     |      See PEP 585
     |
     |  fromkeys(iterable, value=None, /) from typing._TypedDictMeta
     |      Create a new dictionary with keys from iterable and values set to value.
     |
     |  ----------------------------------------------------------------------
     |  Static methods inherited from builtins.dict:
     |
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes inherited from builtins.dict:
     |
     |  __hash__ = None

    class LEDMatrixServiceClient(pykos.services.AsyncClientBase)
     |  LEDMatrixServiceClient(channel: grpc.aio._base_channel.Channel) -> None
     |
     |  Client for the LEDMatrixService.
     |
     |  This service allows controlling an LED matrix display.
     |
     |  Method resolution order:
     |      LEDMatrixServiceClient
     |      pykos.services.AsyncClientBase
     |      abc.ABC
     |      builtins.object
     |
     |  Methods defined here:
     |
     |  __init__(self, channel: grpc.aio._base_channel.Channel) -> None
     |      Initialize the LED matrix service client.
     |
     |      Args:
     |          channel: gRPC channel to use for communication.
     |
     |  async get_matrix_info(self) -> led_matrix.MatrixInfo
     |      Get information about the LED matrix including dimensions and capabilities.
     |
     |      Returns:
     |          MatrixInfo containing:
     |              width: Width in pixels
     |              height: Height in pixels
     |              brightness_levels: Number of brightness levels supported
     |              color_capable: Whether the matrix supports color
     |              bits_per_pixel: Number of bits used to represent each pixel
     |              error: Optional error information
     |
     |  async write_buffer(self, buffer: bytes) -> kos.common_pb2.ActionResponse
     |      Write binary on/off states to the LED matrix.
     |
     |      The buffer should be width * height / 8 bytes long, where each bit
     |      represents one LED's on/off state.
     |
     |      Args:
     |          buffer: Binary buffer containing LED states
     |
     |      Returns:
     |          ActionResponse indicating success/failure of the write operation.
     |
     |  async write_color_buffer(self, **kwargs: Unpack[led_matrix.ImageData]) -> kos.common_pb2.ActionResponse
     |      Write image data to the LED matrix.
     |
     |      Args:
     |          **kwargs: Image data containing the raw bytes, dimensions and format
     |              buffer: Raw image data bytes
     |              width: Image width in pixels
     |              height: Image height in pixels
     |              format: Pixel format specification (e.g. 'RGB888', 'BGR888', 'RGB565', 'MONO8')
     |              brightness: Global brightness level (0-255)
     |
     |      Returns:
     |          ActionResponse indicating success/failure of the write operation.
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |
     |  __abstractmethods__ = frozenset()
     |
     |  ----------------------------------------------------------------------
     |  Data descriptors inherited from pykos.services.AsyncClientBase:
     |
     |  __dict__
     |      dictionary for instance variables
     |
     |  __weakref__
     |      list of weak references to the object

    class MatrixInfo(builtins.dict)
     |  Information about the LED matrix.
     |
     |  Args:
     |      width: Width in pixels
     |      height: Height in pixels
     |      brightness_levels: Number of brightness levels supported (1 for binary on/off)
     |      color_capable: Whether the matrix supports color
     |      bits_per_pixel: Number of bits used to represent each pixel
     |      error: Optional error information
     |
     |  Method resolution order:
     |      MatrixInfo
     |      builtins.dict
     |      builtins.object
     |
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
     |  __annotations__ = {'bits_per_pixel': <class 'int'>, 'brightness_levels...
     |
     |  __optional_keys__ = frozenset({'error'})
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'bits_per_pixel', 'brightness_levels', ...
     |
     |  __total__ = True
     |
     |  ----------------------------------------------------------------------
     |  Methods inherited from builtins.dict:
     |
     |  __contains__(self, key, /)
     |      True if the dictionary has the specified key, else False.
     |
     |  __delitem__(self, key, /)
     |      Delete self[key].
     |
     |  __eq__(self, value, /)
     |      Return self==value.
     |
     |  __ge__(self, value, /)
     |      Return self>=value.
     |
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |
     |  __getitem__(self, key, /)
     |      Return self[key].
     |
     |  __gt__(self, value, /)
     |      Return self>value.
     |
     |  __init__(self, /, *args, **kwargs)
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  __ior__(self, value, /)
     |      Return self|=value.
     |
     |  __iter__(self, /)
     |      Implement iter(self).
     |
     |  __le__(self, value, /)
     |      Return self<=value.
     |
     |  __len__(self, /)
     |      Return len(self).
     |
     |  __lt__(self, value, /)
     |      Return self<value.
     |
     |  __ne__(self, value, /)
     |      Return self!=value.
     |
     |  __or__(self, value, /)
     |      Return self|value.
     |
     |  __repr__(self, /)
     |      Return repr(self).
     |
     |  __reversed__(self, /)
     |      Return a reverse iterator over the dict keys.
     |
     |  __ror__(self, value, /)
     |      Return value|self.
     |
     |  __setitem__(self, key, value, /)
     |      Set self[key] to value.
     |
     |  __sizeof__(...)
     |      D.__sizeof__() -> size of D in memory, in bytes
     |
     |  clear(...)
     |      D.clear() -> None.  Remove all items from D.
     |
     |  copy(...)
     |      D.copy() -> a shallow copy of D
     |
     |  get(self, key, default=None, /)
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  items(...)
     |      D.items() -> a set-like object providing a view on D's items
     |
     |  keys(...)
     |      D.keys() -> a set-like object providing a view on D's keys
     |
     |  pop(...)
     |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
     |
     |      If the key is not found, return the default if given; otherwise,
     |      raise a KeyError.
     |
     |  popitem(self, /)
     |      Remove and return a (key, value) pair as a 2-tuple.
     |
     |      Pairs are returned in LIFO (last-in, first-out) order.
     |      Raises KeyError if the dict is empty.
     |
     |  setdefault(self, key, default=None, /)
     |      Insert key with a value of default if key is not in the dictionary.
     |
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  update(...)
     |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
     |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
     |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
     |      In either case, this is followed by: for k in F:  D[k] = F[k]
     |
     |  values(...)
     |      D.values() -> an object providing a view on D's values
     |
     |  ----------------------------------------------------------------------
     |  Class methods inherited from builtins.dict:
     |
     |  __class_getitem__(...) from typing._TypedDictMeta
     |      See PEP 585
     |
     |  fromkeys(iterable, value=None, /) from typing._TypedDictMeta
     |      Create a new dictionary with keys from iterable and values set to value.
     |
     |  ----------------------------------------------------------------------
     |  Static methods inherited from builtins.dict:
     |
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes inherited from builtins.dict:
     |
     |  __hash__ = None

DATA
    NotRequired = typing.NotRequired
        Special typing construct to mark a TypedDict key as potentially missing.

        For example::

            class Movie(TypedDict):
                title: str
                year: NotRequired[int]

            m = Movie(
                title='The Matrix',  # typechecker error if key is omitted
                year=1999,
            )

    Unpack = typing.Unpack
        Type unpack operator.

        The type unpack operator takes the child types from some container type,
        such as `tuple[int, str]` or a `TypeVarTuple`, and 'pulls them out'.

        For example::

            # For some generic class `Foo`:
            Foo[Unpack[tuple[int, str]]]  # Equivalent to Foo[int, str]

            Ts = TypeVarTuple('Ts')
            # Specifies that `Bar` is generic in an arbitrary number of types.
            # (Think of `Ts` as a tuple of an arbitrary number of individual
            #  `TypeVar`s, which the `Unpack` is 'pulling out' directly into the
            #  `Generic[]`.)
            class Bar(Generic[Unpack[Ts]]): ...
            Bar[int]  # Valid
            Bar[int, str]  # Also valid

        From Python 3.11, this can also be done using the `*` operator::

            Foo[*tuple[int, str]]
            class Bar(Generic[*Ts]): ...

        And from Python 3.12, it can be done using built-in syntax for generics::

            Foo[*tuple[int, str]]
            class Bar[*Ts]: ...

        The operator can also be used along with a `TypedDict` to annotate
        `**kwargs` in a function signature::

            class Movie(TypedDict):
                name: str
                year: int

            # This function expects two keyword arguments - *name* of type `str` and
            # *year* of type `int`.
## Function `foo`

```python
            def foo(**kwargs: Unpack[Movie]): ...
```

        Note that there is only some runtime checking of this operator. Not
        everything the runtime allows may be accepted by static type checkers.

        For more information, see PEPs 646 and 692.

FILE
    /Users/verdakorzeniewski/kscale/kos/kos-py/pykos/services/led_matrix.py



