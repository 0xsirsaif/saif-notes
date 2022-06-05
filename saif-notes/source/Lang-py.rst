Python
============

1. ``[somestr]!r``, ``[somestr]!s``, and ``[somestr]!a``
   
   * ``[somestr]!r`` = repr(somestr) -> returns a printable representation of the given object.
   * ``[somestr]!s`` = str(somestr) -> returns the string version of the given object.
   * ``[somestr]!a`` = ascii(somestr) -> It escapes the non-ASCII characters in the string using ``\x``, ``\u`` or ``\U`` escapes.

2. To run python file as a script
   
   * ``#!`` -> That is called the shebang line
   * This is a shell convention that tells the shell which program can execute the script.
   * ``#!/usr/bin/env python``
   * ``#![/the/path/to/the/python]``

3. **pathlib vs os**

   * filename: `os.path.basename(__file__)` | `Path("").name` name attribute.
   * stem (no suffix): `splitext(basename(''))[0]` | `Path('').stem` stem attribute.  
   * suffix: `os.path.splitext('')[-1]` | `Path('').suffix`
   * Home: `os.path.expanduser('~')` | `Path.home()`
   * form a path: `os.path.join("", "", ""..)` | `Path.home() / "" / "" ..`, the divison operator
   * cwd: `os.getcwd()` -> str | `Path.cwd()` -> `PoisxPath` object.
   * exist?: `os.path.exist("")` | `Path("").exist()`
   * mkdir: `os.mkdir()` | `Path("").make(exist_ok=True)` > if exists ignore `FileExistsError`.
   * multi-level depth dirs: 
  
      * `os.makedirs(os.path.join('test_dir', 'level_1a', 'level_2a', 'level_3a'))`
      * `Path(os.path.join('test_dir', 'level_1b', 'level_2b', 'level_3b')).mkdir(parents=True)`
      * with file at the end: `Path(os.path.join('test_dir', 'level_1b', 'level_2b', 'level_3b')).parent.makedir(parents=True, exist_ok=True)`

   * list files in dir: `os.listdir("")` -> List | `Path("").iterdir()` -> generator, it's more efficient if we loop on them, which is the common case.
   * Glob: 
  
      * `from glob import glob; glob(os.path.join('', 'glob-pattern'))`
      * `Path('').glob('glob-pattern')`, without importing `glob`
  * Read: `with open(path, 'r') as f; data = f.read()` don't forget to close it | `data = Path("").read_text()`
  * When utilising pathlib, you no longer need to use the context manager directly if all you want to do is read or write text (or bytes).


