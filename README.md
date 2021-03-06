vagrant-playground
==================

Sample usage with "thick" box-embedded `Vagranfile` and "thin" project-specific `Vagrantfile`. Target is creating a DRY projects based on a preconfigured box.

Contents:
  - `box/_Vagrantfile` - the Vagrant configuration which gets configured via project-specific `Vagrantfile`. The name is prefixed so it does not get read while building the box
  - `box/prepackage` - used just before building the box on the box template (from withing the VM, assuming CentOS), it is based on a blog post I lost the link to :(
  - `box/package` - used to package the box (from the host machine)
  - `project/Vagrantfile` - sample project-specific config

# Puppet+Hiera config

`/etc/puppet/hiera.yaml` (will auto-load `/vagrant/config.yaml`):
    
    :backends:
      - yaml
    :yaml:
      :datadir: /vagrant             
    :hierarchy:
      - config
      
using [Hiera's automatic parameter lookup](https://docs.puppetlabs.com/hiera/1/puppet.html#automatic-parameter-lookup).