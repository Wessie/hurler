Hurler
======

A decorator based filtering mechanism of function calls. Hurler allows you to decorate a function to prevent calling of the function unless all conditions pass.


Example
-------

A simple example showing how our `printer` function is only called when the condition `number < 5` is `True`.

```python
from hurler import filter

@filter
def lower_than_five(number):
    return number < 5

@lower_than_five
def printer(number):
    print("Received: %d" % number)
```

And now we can call `printer` with our filter in place.

```python
>>> printer(0) # 0 < 5 == True
Received: 0
>>> printer(10) # 10 < 5 == False, `printer` doesn't get called.
>>> printer(100) # 100 < 5 == False
>>> printer(4) # 4 < 5 == True
Received: 4
```

Why?
----

Hurler was originally created for inclusion in an IRC library, it fills the role of accompanying the event callback system.

With `hurler` we could keep the basic callback system simple, it only requires registering a function with an `event_name`.

Callbacks for say, a specific message string or nickname is now done through hurler filters. Instead of repeating
ourself in every callback that required it. An alternative to hurler is creating different `register` methods that take extra
arguments to determine your filter on registration, this gets messy quickly in the callback implementation.


Contributing
------------

If you want to contribute to `hurler` you should fork, implement your change, open a pull request.

If you are not sure if a feature belongs in `hurler` please open an issue to discuss it.

Some guidelines for contributing code:
    - Follow PEP8 when submitting code.
    - Write tests for new code and bugs.
    - Run tests often.


Running tests
-------------

We use `py.test` for our testing, installation is done through `pip install pytest`. 

You can run the tests by running `py.test` in the root directory of this repository.
