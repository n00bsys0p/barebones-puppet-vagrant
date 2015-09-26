# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'
cur_dir     = File.dirname(File.expand_path(__FILE__))
env_config  = YAML.load_file("#{cur_dir}/config.yaml")

Vagrant.configure(2) do |config|
  config.vm.box = env_config[:box]

  # Mapped ports from guest to host
  env_config[:port_maps].each do |port_map|
    config.vm.network "forwarded_port",
      guest: port_map[:remote], host: port_map[:local]
  end

  # Memory and CPU settings
  config.vm.provider "virtualbox" do |vb|
    vb.memory = env_config[:memory]
    vb.cpus   = env_config[:cpus]
  end

  # Puppet provisioner
  config.vm.provision "puppet" do |puppet|

    puppet.hiera_config_path = 'puppet/hiera.yaml'
    puppet.environment_path = 'puppet/environments'
    puppet.environment = env_config[:environment]

    if env_config[:debug]
      puppet.options = '--verbose --debug'
    end
  end
end
