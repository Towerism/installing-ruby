# installing-Ruby

# Mac OSX
Good news, everyone! If you have a Mac, you already have Ruby installed! The bad news is that it's probably an older version unless you have updated it somehow already. The latest macOS has Ruby 2.0.0, I believe. For the course, that will work, but the latest is 2.4.1, and who doesn't want the latest?

There are several ways to get a newer version of Ruby. The easiest is to use Homebrew to just install a version directly. For long-term use it is better to use a "manager" that allows you to use different Ruby versions for different projects. The two most used are rbenv (with ruby-build) and RVM.

## Homebrew Install
If you have a Mac, are a developer, and don't have Homebrew installed: install it. Period. There are far too many useful things that are essentially a single-command to install once you have it. You can find more details [here](https://brew.sh/), but the installation command is just:

```bash
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

That will chug along for a while, and let you know when it is done. Then, you're on to one of the following three options below: homebrew-only, rbenv (+ ruby-build), or RVM.

## Simple: Homebrew-only Ruby Install
If you don't think you will need to have different Ruby projects, you can go simple and just install a single Ruby via Homebrew. To get the latest Ruby version, run

```bash
$ brew install Ruby
```

Then (you may have to open a new console), run:

```bash
$ ruby --version
ruby 2.4.1p111 (2017-03-22 revision 58053) [x86_64-darwin16]
```

If the version number looks good, you are done!

## Recommended: rbenv (+ ruby-build)
**Warning:** RVM and rbenv are not compatible. Do not install both!!!

Rbenv is a tool that makes it easy to run a version of Ruby per project. (Actually per directory.) It is much like RVM in this, but it works significantly differently, and with the advent of Bundler for managing gems (don't worry about that just yet), RVM loses pretty much all its benefits and still has its old costs. See [this page](https://github.com/rbenv/rbenv/wiki/Why-rbenv%3F) for more details if you are interested.

Since we have Homebrew, installing rbenv is easy. So easy, that we will do it all in one chunk here:

```bash
$ brew install rbenv
...
$ rbenv init
[Follow the prompts.]
```

Once you answer the prompts that `rbenv init` gives you, you are ready to install Ruby versions.

```bash
$ rbenv install 2.4.1
...
$ rbenv global 2.4.1
$ ruby --version
ruby 2.4.1p111 (2017-03-22 revision 58053) [x86_64-darwin16]
```

The `rbenv global` command sets your account's default Ruby version. To set a project-specific version, in the project's home directory run:

```bash
$ rbenv local [version-number]
```

This creates a `.ruby-version` file that can be edited to change the version for that project/folder. You should not even have to change to/from that folder to pick up the change.

To remove the local version (and fall back to the global version):

```bash
$ rbenv local --unset
```

This should delete the `.ruby-version` file. Deleting it manually has the same effect.

If you have any problems or just want more information, go to [rbenv on GitHub](https://github.com/rbenv/rbenv). Look for the "doctor" script if you are having problems.

## Popular Other Option: RVM
**Warning:** RVM and rbenv are not compatible. Do not install both!!!

RVM was the first tool that handled the problem of running different Rubies per project. It was (and still is) very popular. However, it has a number of points against it:

  * It is slightly more complex to install.
  * The way that it works is cumbersome at the system level (see the link near the top of the rbenv section of this document).
  * Many factors that led to its design have since changed (Bundler now exists, for example).
  * There are a number of issues that come up when using it with other development tools installed, especially ones that require openssl.
  
That said, if you work on projects that have been around a long time, they may well use RVM, and it is certainly something you will see if you stick around the Ruby world for a while. If you want to kick it old school, the instructions below are cribbed from [RVM's install page](http://rvm.io/rvm/install). Go there if you have any questions or problems.

```bash
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
...
$ \curl -sSL https://get.rvm.io | bash -s stable
...
$ source ~/.rvm/scripts/rvm
```

What is happening there?
  * The `gpg` command gets the keys to ensure a secure download. (If you don't have `gpg`, try to get it from Homebrew.)
  * The `curl` command actually downloads the installation script code.
  * Piping that to the `bash` command runs that downloaded script.
  * The `source` command essentially executes the commands in the `rvm` script. (The same effect could be had by opening a new terminal window and going from there.)

At this point RVM is installed. You can see the list of available ruby versions with this command (along with the corresponding output):

``` bash
$ rvm list known
# MRI Rubies
[ruby-]1.8.6[-p420]
[ruby-]1.8.7[-p374]
...
[ruby-]2.0.0-p353
...
[ruby-]2.4[.1]
ruby-head
...
```

You should install the latest version (e.g. `2.4.1`; the `[.1]` in the version number above indicates that the last `.1` can be optionally specified, but `2.4.1` will be installed either way):

``` bash
$ rvm install 2.4
...
$ rvm use 2.4 --default
Using /home/username/.rvm/gems/ruby-2.4.1
$ ruby --version
ruby 2.4.1p111 (2017-03-22 revision 58053) [x86_64-darwin16]
```

To use a Ruby version for a specific project, go to the project's root folder and:

```bash
$ rvm use 2.1 --default
Using /home/username/.rvm/gems/ruby-2.4.1
$ ruby --version
ruby 2.4.1p111 (2017-03-22 revision 58053) [x86_64-darwin16]
```
This creates a `.ruby-version` file that can be edited to change the version for that project/folder. You might have to move into and out of that folder to pick up the change if you edit the file directly.
