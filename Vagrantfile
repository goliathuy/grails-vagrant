# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "puppetlabs/ubuntu-16.04-64-puppet"
  #config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  #config.vm.box_version = "1.0.1"

  config.vm.network :forwarded_port, guest: 8080, host: 8181
  config.vm.network :private_network, ip: "192.168.222.222"

  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  #config.vm.synced_folder "grails-app", "/vagrant"

  config.vm.provision :puppet, :module_path => "modules" do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file  = "default.pp"
  end

  config.vm.provision :shell, :path => "bootstrap.sh"
end
