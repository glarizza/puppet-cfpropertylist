## Puppet-cfpropertylist FTW

[The CFPropertyList library for Ruby](https://github.com/ckruse/CFPropertyList/)
is pretty awesome. It handles XML and Binary plists, and does so by federating
backends of LibXML, Nokogiri, and ReXML. Because of this, I like to use it in
Puppet. This repository is a collection of some of the providers I've re-written
to utilize the CFPropertyList gem.

Note that these providers will not be merged into core Puppet - they're just
quick providers that I hack on that I hope others find useful.

## Installation and Usage

To install these providers, just drop this repository in the Puppet
modulepath (`/etc/puppet/modules` or `/etc/puppetlabs/puppet/modules` by
default) of your Puppet master server and go to town.  You'll need to set
the `provider` attribute of all resources that need to use the `cfpropertylist`
provider instead of the native system providers.  That looks a little something
like this:

```puppet
service { 'org.ntp.ntpd':
  ensure   => running,
  enable   => true,
  provider => cfpropertylist,
}
```
