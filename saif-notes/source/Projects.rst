Notes / hypothesis / questions about the projcets I am working on
==================================================================

Palm
************


Test-Summurization App
**************************
- ``TORTOISE_ORM``?
- ``aerich init -t app.db.TORTOISE_ORM``: Init config file and generate root migrate location. ``-t, --tortoise-orm [TEXT]`` Tortoise-ORM config module dict variable.
- ``aerich init-db``: Create the first migration. Generate schema and generate app migrate location.
- What is WebSockets?
- **Starlette**: a lightweight ASGI framework/toolkit
- What is meant by generating the schema? __ 1:7
- ``fastapi.testclient.TestClient``: comes directly from starlette.testclient
- In every run of ``pytest`` the data in the ``response.json()`` is increased! What is the Idea of that? __ 1:8.. So I made ``function`` the scope of ``TestClient``, but the problem sills. all post operation in all test functions save data in the ``TestClient``. What if I need to delete these newly created record? 
- ``Path``?
- Keep getting ``307`` status code temporary redirection: because of the mismatch between the api calls and the routes one of the use ``/`` at the end of the url: use regex in the ``@route`` to match the existance or inexistance of the ``/``: ``summaries/?``
- ``...`` Ellipsis: used by fastapi and pydantic to explicitly declare that a value is required. Or use ``Required`` from pydantic. Remember that in most of the cases, when something is required, you can simply omit the default parameter, so you normally don't have to use ``...`` nor ``Required``.
- Query Parameter List/ Multiple values: ``?q=foo&q=bar`` = ``q: list[str] | None = Query(default=None)``. in a Python ``list`` inside your path operation function, in the function parameter ``q``.
- Query Parameter MetaData: in the ``Query()``, name and description parameters.
- Query Parameter Alias: ``?item-query=foobaritems`` -> invalid python variable -> use Alias in the ``Query()``: ``alias="item-query"``
- Exclude from OpenAPI: ``Query(, deprecated=True)``. Deprecated query parameter: ``Query(, include_in_schema=False)``. 