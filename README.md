# nopy

[![PyPi version](https://badgen.net/pypi/v/nope/)](https://pypi.python.org/pypi/nope/)
[![Documentation Status](https://readthedocs.org/projects/nope/badge/?version=latest)](http://nope.readthedocs.io/?badge=latest)
[![PyPi license](https://badgen.net/pypi/license/nope/)](https://pypi.python.org/pypi/nope/)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

Python has a `None` object that is often used as a placeholder or a default value. This works nice, except that `None` has a very limited number of attributes, can not be called, and you can not subscript it. This means that if a function does something with `None`, you typically get an `AttributeError` or `TypeError`.

We introduce `None`s little brother `Nope`. `Nope` is an object where all attributes (except a few) all return `Nope`, and you can subscript with any key to get `Nope`. `Nope` even arises when you call `Nope` with whatever parameters available. It is thus meant to make long useless chains of attributes, items, and method calls, like:

```
from nopy import Nope

Nope.foo.bar['qux'][1].bla(None)  # Nope
```

This is often not a good idea: exceptions should be silenced explicitly, not implicitly. But `Nope` is used as some sort of placeholder or a parameter, if the code where we use it will fetch attributes, make method calls, or subscript, and we don't want this to have any effect.
