# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = ENV['VAGRANT_BOX'] || "precise64-chef-client-omnibus-11.4.0-0.1"
  config.vm.box_url = ENV['VAGRANT_BOX_URL'] || "http://binary.aodn.org.au/static/boxes/precise64-chef-client-omnibus-11.4.0-0.1.box"

  config.ssh.username = ENV['VAGRANT_USER'] || "vagrant"
  config.ssh.private_key_path = "vagrant/ssh/id_rsa"

  config.vm.network :forwarded_port, guest: 5432, host: 15432

  config.vm.provision :chef_solo do |chef|

    chef.roles_path = "roles"
    chef.data_bags_path = "data_bags"
    chef.provisioning_path = "/tmp/vagrant-chef"

    chef.add_recipe 'chef-solo-search'
    chef.add_recipe 'chef-solo-encrypted-data-bags'
    chef.add_recipe 'postgis'

    chef.json = {

      "postgis" => {
        "version" => "1"
      },

      "postgresql" => {
        "config" => {
          "listen_addresses" => "*"
        },
        "server" => {
          "packages" => ["postgresql-contrib"]
        }
      }
    }
  end
end
