# RubyGems

Sometimes, developers writing code notice that they've written
something that might be useful to others. If they are nice people,
they package that code up into a *gem* (also often called a *library*)
and share it with the world. This can be anything from a few short
methods to a web framework as large as Rails.

Let's see how to find, install and use a gem.

## Finding gems
Two main plaecs to look when searching for a gem are
[RubyGems][ruby-gems] and [Ruby Toolbox][ruby-toolbox].

[ruby-gems]: http://rubygems.org/
[ruby-toolbox]: https://www.ruby-toolbox.com/

I often just simply google around for what I want to do, read
StackOverflow for suggestions, and then look at the gem's github repo
to see if it's what I want.

On github you can see how many people have followed the repository,
and how recently it has been updated. Gems that have >1k follows are
mainstream and can be relied upon to be rock-solid and typically very
well documented. Gems with more than 500 follows are fairly popular,
but it may be harder to find answers to problems by searching
around. Gems with less than 500 follows are not very popular, and
might be poorly maintained.

## Installing gems

Let's check out [Awesome Print][awesome-print], a library that "pretty
prints" Ruby output.

[awesome-print]: https://github.com/michaeldv/awesome_print

The Awesome Print github shows us how to install the gem: `gem install
awesome_print`. That's it!

## `sudo gem install` and rvm

> **This section is OS X and Linux specific**. Windows users cannot
> install rvm: it's only for *nix systems. In any case, I believe that
> Windows users who have installed Ruby through RubyInstaller should
> already be able to install gems without using `sudo` and are already
> using an up-to-date Ruby.

If you aren't using rvm, you will run into an error like

```
~$ gem install awesome_print
Fetching: awesome_print-1.1.0.gem (100%)
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions into the /Library/Ruby/Gems/1.8 directory.
```

This is because the builtin Ruby that comes with OS X installs gems in
a system directory where you need superuser permissions to create
files. The usual answer to this problem is to prefix your command with
`sudo`, which prompts you for your system password, and then executes
your command as superuser.

However, you should be using rvm. OS X comes with Ruby 1.8.7, which is
very out of date; the current version is 1.9.3. 1.8.7 misses a lot of
features, and isn't any more supported by a number of key gems.

### Installing rvm

To install new versions of Ruby, we use a program called rvm (Ruby
version manager). One nice thing about rvm it stores all the newly
installed versions of Ruby and their gems in your own user directory
(/Users/username/.rvm), so you never need to use `sudo`.

Installing rvm is easy. Simply run this command:

    curl -L https://get.rvm.io | bash -s stable --ruby

The curl part downloads an installation script from the rvm
website. It then pipes (`|`) the script into the `bash` interpreter,
which runs it, downloading and installing rvm.

Now lets install a new version of Ruby:

    rvm install 1.9.3

Yay! The last step in the process is to make this our default:

    rvm --default use 1.9.3

All set! You're now using an up-to-date version of Ruby. And you can
also stop installing gems with `sudo`.

## Using gems

We should now be able to require source files provided by the gem:

```ruby
[1] pry(main)> require 'awesome_print'
=> true
[2] pry(main)> ap({:this => "is totally awesome!"})
{
    :this => "is totally awesome!"
}
=> nil
```

You'll need to read up on how to use your newly installed gem. The
github often has examples that show you the most common methods and
how they are used. Well documented libraries like RSpec have whole
websites of [documentation][rspec-docs]. Documentation is normally
linked to on the github page; else I do a quick google search.

Documentation can often be spotty and incomplete. In that case, you'll
have to explore the code itself (either on github, or a local clone of
the repo on your machine) to try to figure out how things work.

[rspec-docs]: https://www.relishapp.com/rspec

**TODO: Code and documentation reading exercises**