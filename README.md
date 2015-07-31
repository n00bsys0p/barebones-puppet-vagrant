# Barebones Vagrant / Puppet Skeleton

This project provides a trivial way to initialise single-machine,
Puppet-managed development environment projects.

Just change settings in config.yaml to taste, and add your Hiera configuration
data to puppet/hieradata/common.yaml.

Use `vagrant up` to bring the machine up, and `vagrant provision` to re-run the
provisioner as you develop your environment around the skeleton.
