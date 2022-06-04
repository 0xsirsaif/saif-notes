Makefile
=========

* ``#`` comment
* ``.PHONY:`` Bypassing the normal execution model of the `Make`.
* ``$@``: Automatic variable (pattern rules?) that refers to the output of the target.
* ``$>``: The name of the very first prerequisite.
* ``$^``: The name of all prerequisites.
* ``%.o: %.c``: A special wildcard (%) as part of your target: every `.o` file depends on its `.c` file. A generic rule.
* ``@command``: to not show command in the print.

* ``variable_name := value``: Variables in `Makefile`.
* ``variable_name += appended_value``: append to `variable_name`.
* ``$(variable_name)``: to use it in the file. 

* Resources

    * 