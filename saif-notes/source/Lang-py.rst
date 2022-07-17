Python
============

   
* ``[somestr]!r`` = repr(somestr) -> returns a printable representation of the given object.
* ``[somestr]!s`` = str(somestr) -> returns the string version of the given object.
* ``[somestr]!a`` = ascii(somestr) -> It escapes the non-ASCII characters in the string using ``\x``, ``\u`` or ``\U`` escapes.

   
* ``#!``: shebang line a shell convention that tells the shell which program can execute the script: ``#!/usr/bin/env python`` > ``#![/the/path/to/the/python]``

pathlib vs os
-------------------
- filename: ``os.path.basename(__file__)`` | ``Path("").name`` name attribute.
- stem (no suffix): ``splitext(basename(''))[0]`` | ``Path('').stem`` stem attribute.  
- suffix: ``os.path.splitext('')[-1]`` | ``Path('').suffix``
- Home: ``os.path.expanduser('~')` | `Path.home()``
- form a path: ``os.path.join("", "", ""..)`` | ``Path.home() / "" / "" ..``, the divison operator
- cwd: ``os.getcwd()`` -> str | ``Path.cwd()`` -> ``PoisxPath`` object.
- exist?: ``os.path.exist("")`` | ``Path("").exist()``
- mkdir: ``os.mkdir()`` | ``Path("").make(exist_ok=True)`` > if exists ignore ``FileExistsError``.
- multi-level depth dirs: 
  
   - ``os.makedirs(os.path.join('test_dir', 'level_1a', 'level_2a', 'level_3a'))``
   - ``Path(os.path.join('test_dir', 'level_1b', 'level_2b', 'level_3b')).mkdir(parents=True)``
   - with file at the end: ``Path(os.path.join('test_dir', 'level_1b', 'level_2b', 'level_3b')).parent.makedir(parents=True, exist_ok=True)``

- list files in dir: ``os.listdir("")`` -> List | ``Path("").iterdir()`` -> generator, it's more efficient if we loop on them, which is the common case.
- Glob: 
  
   - ``from glob import glob; glob(os.path.join('', 'glob-pattern'))``
   - ``Path('').glob('glob-pattern')``, without importing ``glob``

- Read: ``with open(path, 'r') as f; data = f.read()`` don't forget to close it | ``data = Path("").read_text()``
- When utilising pathlib, you no longer need to use the context manager directly if all you want to do is read or write text (or bytes).


Socket Programming
--------------------

- processes can interact with each others via TCP socket, a way to transmit bytes among computer systems. sockets are created by the server and clients send a request that must be accepted.
- see example in the misc repo `0xsirsaif/misc <https://github.com/0xsirsaif/misc>`_
- Resources: `real python socket guide <https://realpython.com/python-sockets>`_ 
- ``socket.AF_INET, socket.SOCK_STREAM``: constants used to specify *the address family* and *socket type*. ``AF_INET`` is the Internet address family for IPv4. ``SOCK_STREAM`` is the socket type for TCP, the protocol that will be used to transport messages in the network.


Zip() function: work just like the physical zipper on a bag or pair of jeans.
-------------------------------------------------------------------------------
- The most common use cases: Looping over multiple iterables. to iterate in parallel over two or more iterables. Since ``zip()`` generates tuples, you can unpack these in the header of a
- Creates an iterator that will aggregate elements from two or more iterables. Returns an iterator (This object yields tuples on demand and can be traversed only once.) of tuples, where the i-th tuple contains the i-th element from each of the argument sequences or iterables.
- Returns an iterator of tuples, **where the i-th tuple contains the i-th element from each of the argument sequences or iterables**.
- ``zip(*iterables).``
- To retrieve the final list object, you need to use ``list()`` to consume the iterator.
- Wierd results when using set objects, which don’t keep their elements in any particular order. This means that the tuples returned by ``zip()`` will have elements that are paired up randomly. If you’re going to use the Python ``zip()`` function with unordered iterables like sets, then this is something to keep in mind.
- Passing one iterables: The result will be an iterator that yields a series of 1-item tuples:
- Passing Arguments of Unequal Length: Always Pay Attention: In these cases, the number of elements that ``zip()`` puts out will be equal to the length of the shortest iterable. The remaining elements in any longer iterables will be totally ignored by ``zip()``. Use ``itertools.zip_longest()`` if you want the longest one. the missing values will be replaced with whatever you pass to the ``fillvalue`` argument (defaults to None).
- Python >= 3.10: the ``strict=Bool`` argument, PEP 618—Add Optional Length-Checking To zip. to make sure that the function only accepts iterables of equal length.
- The opposite of ``zip()`` is… well, ``zip()``: It's a zipper, stupid!: use ``zip()`` along with the unpacking operator ``*``
- Create Dictionary: ``dict(zip(keys, values))``
- 