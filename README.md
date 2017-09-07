# installing-Ruby
> Ruby Install guide for Mac OSX.
For the course, we will be installing Ruby >2.0.

# Mac OSX
There are two main ways to get ruby: `homebrew` (the easy way) and installing manually by getting the Ruby version manager (`rvm`) first (the slightly very annoying way)
## If you have Homebrew
If you have `homebrew` installed then that will be the recommended way to install Ruby. To get the latest Ruby version, run

``` bash
brew install Ruby
```

## If you don't have Homebrew
Otherwise, the path to Ruby is by installing the `rvm`, and using it to install the latest Ruby version. Run
the following commands to get `rvm` installed.

``` bash
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
\curl -sSL https://get.rvm.io | bash -s stable
```

After `rvm` is installed, run this command to load it

``` bash
source ~/.rvm/scripts/rvm
```

You can see the list of available ruby versions with this command (along with the corresponding output):

``` bash
$ rvm list known
# MRI Rubies
[ruby-]1.8.6[-p420]
[ruby-]1.8.7[-p374]
[ruby-]1.9.1[-p431]
[ruby-]1.9.2[-p320]
[ruby-]1.9.3[-p545]
[ruby-]2.0.0-p353
[ruby-]2.0.0[-p451]
[ruby-]2.1[.1]
ruby-head
...
```

You should install the latest version (e.g. `2.1.1`; the `[.1]` in the version number above indicates that `.1` be optionally specified, but `2.1.1` will be installed either way):

``` bash
rvm install 2.1
```

## Check your installation
Ensure that Ruby installed successfully

``` bash
$ ruby -v
ruby 2.1.1p76 (2014-02-24 revision 45161) [Mac OS MCMLXXVII Panther]
```
