# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANT_API_VERSION) do |config|
  config.vm.box = "bento/centos-7.2"

  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "forwarded_port", guest: 22, host: 2201, id: "ssh"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.ssh.forwardagent = true
  config.vm.synced_folder "centos72/", "centos72/"

  config.vm.provider "virtualbox" do |v|
    v.gui = true
    v.name = "centos72"
    v.memory =  3078
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "hosts"
    ansible.limit = all
  end
end
