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
* 