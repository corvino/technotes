### Basic pyenv

The Python equivalent of Ruby's rbenv, forked from [rbenv](https://github.com/sstephenson/rbenv).

See [github.com/yyuu/pyenv](https://github.com/yyuu/pyenv).

* On OS X, install pyenv via Homebrew:
```
> brew install pyenv
==> Downloading https://github.com/yyuu/pyenv/archive/v20140705.tar.gz
Already downloaded: /Library/Caches/Homebrew/pyenv-20140705.tar.gz
==> Caveats
To enable shims and autocompletion add to your profile:
  if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi

To use Homebrew's directories rather than ~/.pyenv add to your profile:
  export PYENV_ROOT=/usr/local/opt/pyenv
==> Summary
/usr/local/Cellar/pyenv/20140705: 287 files, 2.6M, built in 2 seconds
```

* Install shims with ```pyi``` (an alias for ```'eval "$(pyenv init -)"'```).
* Identify latest and greatest, or an alternative, Python  with ```pyenv install -l```.
* Install a Python with ```pyenv install```:
```
> pyenv install 3.4.1
Downloading Python-3.4.1.tgz...
-> http://yyuu.github.io/pythons/8d007e3ef80b128a292be101201e75dec5480e5632e994771e7c231d17720b66
Installing Python-3.4.1...
Installed Python-3.4.1 to /Users/vino/.pyenv/versions/3.4.1
```

* Switch to the newly install version with ```pyenv global```.
* Install packages with pip:
```
> pip install beautifulsoup4
Downloading/unpacking beautifulsoup4
  Downloading beautifulsoup4-4.3.2.tar.gz (143kB): 143kB downloaded
  Running setup.py (path:/private/var/folders/lj/j_1_jjf52pq4j1490x7478700000gn/T/pip_build_vino/beautifulsoup4/setup.py) egg_info for package beautifulsoup4

Installing collected packages: beautifulsoup4
  Running setup.py install for beautifulsoup4
    Skipping implicit fixer: buffer
    Skipping implicit fixer: idioms
    Skipping implicit fixer: set_literal
    Skipping implicit fixer: ws_comma

Successfully installed beautifulsoup4
Cleaning up...
```

* Use ```#!/usr/bin/env``` to write python scripts.
