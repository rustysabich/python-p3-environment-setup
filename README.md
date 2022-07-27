# Environment Setup

## Learning Goals

- Use pyenv to use different python versions
- Set up virtual environment using pipenv

***

## Key Vocab

- **Virtual Environment**: A virtual environment is a directory tree which
 contains Python executable files and other files which
 indicate that it is a virtual environment.

- **Dependency**: A software dependency is a code library or package that
 is reused in a new piece of software.

***

## Introduction

In this lesson we will talk about environment tools like pyenv and pipenv.
 These tools allows us to separate different python environments for all
 kinds of use cases. This is useful when we need an isolated environment
 with libraries and specific versions of python.

## Pyenv

Use the following instructions to install pyenv for your operating system.

[pyenv install instructions](https://github.com/pyenv/pyenv#installation)

Run the following command to see if pyenv has installed.

```bash
$ pyenv versions
* system (set by /Users/username/.pyenv/version)
```

We can see the different versions of python available to install
using the following command

```bash
$ pyenv install -l
Available versions:
  2.1.3
  2.2.3
  2.3.7
  ...
  ...
```

Lets install a new version of python (3.9.2). We can do this using the
 following command

```bash
pyenv install 3.9.2

```

To set the global python version to the one we have installed

```bash
pyenv global 3.9.2
```

Now we can run python code with the version of python we want to use.

## Pipenv

Pyenv allows us to manage the version of python we are working with.

What if we want to manage dependencies as well?

Pipenv  automatically creates and manages a virtualenv for your projects,
 it also adds/removes packages from your Pipfile as you install/uninstall packages

To install pipenv follow the instructions here [pipenv install](https://pipenv.pypa.io/en/latest/install/)

To create a virtual environment using pipenv we can use the following command.

```bash
pipenv install -python 3.8
```

In the python flag we can define which version of `--python` we want to use.

You will notice a `Pipfile` and a `Pipfile.lock` have been added
to the directory.

The `Pipfile` describes the dependencies we have installed and the python version.

The `Pipfile.lock` describes all the dependencies our dependencies rely on.
The lock file gives us the ability to produce a deterministic and reproducible
project environment.

We can now install a library into the virtual environment.
Lets use the `requests` library as an example

```bash
pipenv install requests
```

if we want to install a specific version of the requests library
we can pin the version in the command

```bash
pipenv install requests==2.28.1
```

Pipenv has created a virtual environment for our project. We can see the location
of this virtual environment by using the command

```bash
$ pipenv --venv
/Users/username/.local/share/virtualenvs/python-p3-environment-setup-6aKrLSzT
```

Pipenv allows us to install dev dependencies. We can do so by adding the `--dev`
argument.

```bash
pipenv install pytest --dev
```

Pytest will be added to the Pipfile as a dev dependency

Dev dependencies are modules which are not needed in production but
they help us develop and test the code.

How do we get into our virtual environment?

Using the following command will allow us to use the virtual environment
and run commands inside of it.

```bash
pipenv shell
```

Now we are in the virtual environment and have access to the dependencies we 
defined in the Pipfile. If we run the following commands in the virtual environment
we will see that we can
import the `requests` module we installed earlier.

```bash
python
>>> import requests
>>>
```

We can see that we have access to the requests module in the python repl.

Now we can write all our code in this directory and run it in the deterministic
virtual environment.
If we have a python file called `program.py` we can use the following command to
run it in the virtual environment.

```bash
pipenv run python program.py
```

## Conclusion

Virtual environments allow us to have a deterministic and predictable runtime
for our python projects. We can define specific versions for python and the 
dependencies we need. We can easily add new virtual environments for multiple
projects we have on our machine.
***

## Resources

- [Python 3 Documentation](https://docs.python.org/3/)
- [pyenv](https://github.com/pyenv/pyenv/)
- [pipenv](https://pipenv.pypa.io/en/latest/)