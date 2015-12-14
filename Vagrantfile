# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_API_VAERSION = 2

Vagrant.configure(VAGRANT_API_VAERSION) do |config|
  config.vm.box = "ubuntu-VAGRANTSLASH-trusty64"
  config.vm.hostname = "elk-vm"

  config.ssh.forward_agent = true

  config.vm.network "forwarded_port", guest: 9200, host: 9200 # service: "elasticsearch"
  config.vm.network "forwarded_port", guest: 5601, host: 5601 # service: "kibana"

  config.vm.network "private_network", type: "dhcp"

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = "2"
    vb.memory = "4096"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "cm/playbook.yml"
  end
end
