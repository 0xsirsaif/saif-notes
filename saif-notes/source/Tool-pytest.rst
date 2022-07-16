Pytest
========

Generic or theory concepts
*****************************
* Testing Pattern:

    * **GIVEN** some precondition(s) for a scenario.
    * **WHEN** we exercise some method of a class
    * **THEN** some state change(s) or side effect(s) will occur that we can confirm
* `Equivalence Partitioning and Boundary Values: Design test cases <https://www.softwaretestinghelp.com/what-is-boundary-value-analysis-and-equivalence-partitioning/>`_ 
* Avoid ``print()`` output suppression: ``pytest --capture=no``



Commands
***********
- ``pytest``: normal run
- ``pytest -p no:warnings``: disable warnings
- ``pytest --lf``: run only the last failed tests
- ``pytest -k "[str-expression]"``: run only the tests with names that match the string expression
- ``pytest -x``: stop the test session after the first failure
- ``pytest -x --pdb``: enter PDB after first failure then end the test session. Add ``assert False`` and get a shell inside the test to interact with various objects and figure out how to best run assertions against them.
- ``pytest --maxfail=2``: stop the test run after two failures
- ``pytest -l``: show local variables in tracebacks
- ``pytest --durations=2``: list the 2 slowest tests