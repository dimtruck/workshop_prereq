# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :forwarded_port, guest: 8080, host: 8080, auto_correct: true
  config.vm.network :forwarded_port, guest: 9000, host: 9000, auto_correct: true
  config.vm.network :forwarded_port, guest: 35729, host: 35729, auto_correct: true
  #config.ssh.forward_agent = true
  #config.ssh.private_key_path = "~/.ssh/id_rsa"

  config.vm.provider "virtualbox" do |v|
      v.name = "WorkshopDemo"
      v.customize ["modifyvm", :id, "--memory", "2048"]
      v.cpus = 2
  end
  config.vm.provision "ansible" do |ansible|
    ansible.sudo = true
    ansible.inventory_path = "ansible/inventory/vagrant"
    ansible.playbook = "ansible/main.yml"
    ansible.verbose = "vvvv"
    ansible.limit = "development"
  end
end
