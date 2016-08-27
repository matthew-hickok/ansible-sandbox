# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Ansible Control Server
  config.vm.define "control" do |ctl|
    ctl.vm.box = "centos/7"
    ctl.vm.hostname = "ansible-control"
    ctl.vm.synced_folder ".\\ansible_data", "/home/vagrant/ansible_data"
    ctl.vm.network "private_network", ip: "192.168.33.5"
    ctl.vm.provision "shell", inline: <<-SHELL
      sudo yum install epel-release -y
      sudo yum install ansible -y
      sudo yum install tree -y
      SHELL
    ctl.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.gui = false
    end
  end

  # Web Server
  config.vm.define "web" do |web|
    web.vm.box = "centos/7"
    web.vm.hostname = "web"
    web.vm.synced_folder ".\\ansible_data", "/home/vagrant/ansible_data"
    web.vm.network "private_network", ip: "192.168.33.6"
    web.vm.provision "shell", inline: <<-SHELL
      sudo yum install tree -y
      SHELL
    web.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.gui = false
    end
  end

  # Database
  config.vm.define "db" do |db|
    db.vm.box = "centos/7"
    db.vm.hostname = "ansible-control"
    db.vm.synced_folder ".\\ansible_data", "/home/vagrant/ansible_data"
    db.vm.network "private_network", ip: "192.168.33.7"
    db.vm.provision "shell", inline: <<-SHELL
      sudo yum install tree -y
      SHELL
    db.vm.provider "virtualbox" do |vb|
      vb.memory = 512
      vb.gui = false
    end
  end

end
