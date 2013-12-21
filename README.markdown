## Puppet-cfpropertylist FTW

[The CFPropertyList library for Ruby](https://github.com/ckruse/CFPropertyList/)
is pretty awesome. It handles XML and Binary plists, and does so by federating
backends of LibXML, Nokogiri, and ReXML. Because of this, I like to use it in
Puppet. This repository is a collection of some of the providers I've re-written
to utilize the CFPropertyList gem.

Note that these providers will not be merged into core Puppet - they're just
quick providers that I hack on that I hope others find useful.

## Installation and Usage

In order to use the CFPropertyList library, you'll need the gem on your
system one way or another. If you're using Bundler, I've provided a `Gemfile`
for you already.  If you're not, you're going to have to install the gem
with the `gem` command on the system.  I recommend installing both `CFPropertyList`
as well as `libxml-ruby`. There's one caveat about CFPropertyList, though -
the version we need HAS to be `2.2.5` or greater (as there's a bug with
versions less than `2.2.5`). CFPropertyList comes pre-installed with Mavericks,
but it's an older version that we can't use.

To install these gems using the system `gem` command,
you'll need to do something like this:

```
└(~)▷ sudo gem install CFPropertylist -v 2.2.5
└(~)▷ sudo gem install libxml-ruby
```


To install these providers after the gems are installed, just drop this
repository in the Puppet modulepath (`/etc/puppet/modules` or
`/etc/puppetlabs/puppet/modules` by default) of your Puppet master server and
go to town.  You'll need to set the `provider` attribute of all resources that
need to use the `cfpropertylist` provider instead of the native system
providers.  That looks a little something like this:

```puppet
service { 'org.ntp.ntpd':
  ensure   => running,
  enable   => true,
  provider => cfpropertylist,
}
```
