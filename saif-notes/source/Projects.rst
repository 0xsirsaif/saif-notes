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
- **Part1: Recap and Reflection**:

    - 