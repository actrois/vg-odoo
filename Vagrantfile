# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # Base OS
  config.vm.box = "ubuntu/xenial64"
  config.vm.box_check_update = false
  
  config.vm.provider "virtualbox" do |vb|
    vb.name = 'odoo'
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
  end
  
  # Set machine name
  config.vm.define :odoo do |odoo|
  end

  # Network config
  config.vm.network :private_network, ip: "192.168.100.100"

  # Install python
  config.vm.provision "shell" do |s|
    s.inline = "apt install -y python"
  end

  # Run ansible Playbook
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/odoo.yml"
    ansible.become = true
  end

end
