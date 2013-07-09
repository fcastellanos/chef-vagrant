# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "lucid32"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  # config.vm.box_url = "http://domain.com/path/to/above.box"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network :forwarded_port, guest: 3000, host: 3000

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #

  # config.vm.provision :shell, :path => 'vagrant_scripts/before_script.sh'

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = 'chef/cookbooks'
    chef.roles_path     = 'chef/roles'
    chef.add_recipe 'apt'
    chef.add_recipe 'git'
    chef.add_recipe 'build-essential'
    chef.add_recipe 'ruby_build'
    chef.add_recipe 'rbenv'

    chef.json = {
      'rbenv' => {
        'global' => '1.9.3-p194',
        'rubies' => [ '1.9.3-p194' ],
        'gems'   => {
          '1.9.3-p194' => [
            { 'name'   => 'bundler' }
          ]
        }
      }
    }

    # chef.add_role 'ruby'
  end

  # config.vm.provision :shell, :path => 'vagrant_scripts/after_script.sh'
end
