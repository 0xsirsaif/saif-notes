Python Tips
============

1. To run python file as a script
    
    * ``#!`` -> That is called the shebang line
    * This is a shell convention that tells the shell which program can execute the script.
    * ``#!/usr/bin/env python``
    * ``#![/the/path/to/the/python]``

2. ``[somestr]!r``, ``[somestr]!s``, and ``[somestr]!a``
   
   * ``[somestr]!r`` = repr(somestr) -> returns a printable representation of the given object.
   * ``[somestr]!s`` = str(somestr) -> returns the string version of the given object.
   * ``[somestr]!a`` = ascii(somestr) -> It escapes the non-ASCII characters in the string using ``\x``, ``\u`` or ``\U`` escapes.
  
