## Managing Ruby with rbenv

[rbenv](http://rbenv.org) provides clean-and-simple ruby management. That is, you can switch
between multiple ruby versions on the same machine without pain, and you
don't have to overwrite the system install.

It has a "rich plugin ecosystem"; it is interesting that ruby-build is a
plugin and not core. Thus, the currently interesting moduels are:

* [rbenv](https://github.com/sstephenson/rbenv)
* [ruby-build](https://github.com/sstephenson/ruby-build)
* [rbenv-gemset](https://github.com/jf/rbenv-gemset)

### Install

On OS X, homebrew is easiest...

```
> brew update
...
> brew install rbenv
...
> brew install ruby-build
...
```

You have to setup your shell environment&mdash;see notes.

You may have to run ```rbenv rehash```. You may also have to do this
after installing executables to generate new shims&mdash;like the first
time bundler is installed.

###### Notes

* [rbenv](https://github.com/sstephenson/rbenv)

  Ruby environment manager; allows installing and switching between
  multiple versions of Ruby.

  rbenv works by appending "shims" to the front of the shell path. That
  is, it adds ```~/.rbenv/shims``` to the front of the shell's path, so
  that commands like ruby will fine ```~/.rbenv/shims/ruby``` rather
  than ```/usr/bin/ruby``` and dispatch appropriately.

  rbenv recommends adding ```'eval "$(rbenv init -)"'``` to "your shell"
  to set this up; that is, to .bash_profile or .bash_rc or the
  like. Instead, I add this as the alias rbi, meaning I have to run the
  alias command in each shell session I want to use rbenv see
  ([.bashrc](https://github.com/corvino/tilde/blob/master/.bashrc)). It's
  not clear how this will work in deployment, but this has been
  satisfactory for development.

* [ruby-build](https://github.com/sstephenson/ruby-build)

  rbenv plugin that provides ```rbenv install```, so you don't have
  "download and compile Ruby manually as a subdirectory of
  ```~/.rbenv/versions/```"&mdash;that is, so so you don't have to
  install ruby _like an animal_.

  ruby-build recommends installing through homebrew if that is how you
  have installed rbenv. The way the install section is written this
  could be missed.

### Usage

##### Installing Ruby versions

In order to install, you need to specify a ruby version to install. To
obtain a list of versions, use ```rbenv install -l``` / ```rbenv install
--list```. Then run install specifying the desired version.

```
> rbenv install -l
...
> rbenv install 2.2.2
```

This will install Ruby 2.2.2 in ```~/.rbenv/versions/2.2.2```.

##### Switching Ruby versions

Switch to the newly install version with ```rbenv global```. But first,
you may need to list what's installed (and currently being used) with
```rbenv versions```.

```
> rbenv versions
...
> rbenv global 2.2.2
```

##### Figuring out what gets executed

The which command will report that shims are being executed; that is, ```which ruby``` will report ```~/.rbenv/shims/ruby```.

Use rbenv which <PROGRAM> to find out what the shim will use:

```
> which ruby
/Users/vino/.rbenv/shims/rub
> rbenv which ruby
/Users/vino/.rbenv/versions/2.2.2/bin/ruby
```

Remember, if you haven't run ```'eval "$(rbenv init -)"'``` rbenv which will lie.

##### Gems

Gems will be installed inside the ruby verion; thus, ```gem contents
bundler``` will display something like:

```
> gem contents bundler
/Users/vino/.rbenv/versions/2.2.2/lib/ruby/gems/2.2.0/gems/bundler-1.9.4/CHANGELOG.md
/Users/vino/.rbenv/versions/2.2.2/lib/ruby/gems/2.2.0/gems/bundler-1.9.4/CODE_OF_CONDUCT.md
/Users/vino/.rbenv/versions/2.2.2/lib/ruby/gems/2.2.0/gems/bundler-1.9.4/CONTRIBUTING.md
...
```

There doesn't appear to be anything quite like rmv's gemsets, but
rbenv-gemset might be a replacement. Also, learning more about bundler
will help.

#### rbenv-gemset

Actually haven't used this yet. But it seems promising. So maybe someday

##### Scripts

Use ```#!/usr/bin/env ruby``` to invoke Ruby in scripts. This will use
the ```ruby``` program found in shell's path.

### Details

The shims simply dispatch to the rbenv executable, passing the "program
name"&mdash;ruby, irb, gem, etc.&mdash; and the arguments. rbenv is a
bash script, and homebrew will install it somewhere like
```/usr/local/Cellar/rbenv/0.4.0/libexec/rbenv```.

rbenv looks for a "local file"&mdash;a .ruby-version file in the path of
the current working directory. If one is found, it specifies the ruby
version to use. If one is not found, the version specified in
~/.rbenv/versions.

If local rather than global is used to switch ruby versions, then a
.ruby-version file is created or updated in the current working
directory.

