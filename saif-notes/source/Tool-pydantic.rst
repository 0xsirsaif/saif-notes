Pydantic
=========

- Pydantic is primarily a parsing library, not a validation library. In other words, pydantic guarantees the types and constraints of the output model, not the input data.

Models
********
- You can think of models as similar to types in strictly typed languages, or as the requirements of a single endpoint in an API.


Validation decorator
*********************
- ``validate_arguments``: allows the arguments passed to a function to be parsed and validated using the function's annotations before the function is called. Argument types are inferred from type annotations on the function, arguments without a type decorator are considered as ``Any``
- Validate without calling the function: To do that you can call the ``validate`` method bound to the decorated function.
- Raw Function: The raw function which was decorated is accessible, this is useful if in some scenarios you trust your input arguments and want to call the function in the most performant way

Settings management
********************
- ``BaseSetttings`` Model: the model initialiser will attempt to determine the values of any fields not passed as keyword arguments by reading from the environment.
- ``env_perfix`` a ``Config`` calss attribute: no perfix is the defaut.
- You can still name environment variables anything you like through ``Field(..., env=...)``
- env vars are passed as strings by defaut. 
- Complex types like ``list``, ``set``, ``dict``, and sub-models are populated from the environment by treating the environment variable's value as a JSON-encoded string.
- ``env_nested_delimiter``: to populate nested complex variables. What it does is simply explodes your variable into nested models or dicts. So if you define a variable. can be configured via the ``Config`` class as shown above, or via the ``_env_nested_delimiter`` keyword argument on instantiation.
- JSON is only parsed in top-level fields, if you need to parse JSON in sub-models, you will need to implement validators on those models.
- Locating ``.env`` file [python-dotenv]: (1) in the ``Config`` set ``env_file`` and/or ``env_file_encoding``. (2) instantiating a ``BaseSettings`` derived class with the ``_env_file`` keyword argument and/or the ``_env_file_encoding``. 
- environment variables will always take priority over values loaded from a dotenv file.
- ``settings = Settings(_env_file=None)``: tell Pydantic not to load any file at all (even if one is set in the ``Config`` class)
- A secret file follows the same principal as a dotenv file except it only contains a single value and the file name is used as the key
- Loading Secrets: (1) ``secrets_dir`` in ``Config``. (2) instantiating a ``BaseSettings`` derived class with the ``_secrets_dir`` keyword argument
- a dotenv file and environment variables will always take priority over values loaded from the secrets directory.
-  