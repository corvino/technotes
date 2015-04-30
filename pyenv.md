## Managing Python with pyenv

[pyenv](https://github.com/yyuu/pyenv) is the Python
equivalent of [rbenv](https://github.com/sstephenson/rbenv). It's forked
from rbenv and ruby-build, so the install functionality is baked into
the core.

Since the operation is nearly identical to rbenv, see [rbenv notes](rbenv.md)
for usage details.

It also has two [plugins](https://github.com/yyuu/pyenv/wiki/Plugins)&mdash;[pyenv-virtualenv](https://github.com/yyuu/pyenv-virtualenv) and [pyenv-virtualenvwrapper](https://github.com/yyuu/pyenv-virtualenvwrapper)&mdash; for managing [virtualenv](https://virtualenv.pypa.io), which manages python dependency sets.

### Install

On OS X, install pyenv via Homebrew:

```
> brew install pyenv
...
```

Note you now have the equivalent of rbenv and ruby-build.

You have to setup your shell environment. This is a direct paralell to
rbenv; see [rbenv notes](rbenv.md) for details.

### Usage

Refer to [rbenv notes](rbenv.md) for details.

### pip

pip appears to be the preferred package manager for Python. I can't tell
whether it handles dependencies.

pip is installed by default in Python 2.7.9 and 3.4 and later,
[according to wikipedia](http://en.wikipedia.org/wiki/Pip_\(package_manager\)). Before
that easy_install appears to have been the alternative in (some) prior
versions? And you can use easy_install to install pip if you're on an
old version ... that has easy_install.

There is also setuptools, which seem to be installed by default either
way, and seems to relate to easy_install ... somehow.

OS X 10.10 ships with Python 2.7.6, so pip is not installed by
default. But if you install an appropriate Python with pyenv, you will
have pip. Which is apparently good.

None of this is entirely clear .... It's a mess. I would love to make
this section more thorough and accurate, but that's all the time I have
at the moment. Please educate me where I've gone astray.

### virtualenv

Haven't played with this. Seems useful. And overly
complicated&mdash;although possibly only in regards to there being two
pyenv plugins for working with it.
