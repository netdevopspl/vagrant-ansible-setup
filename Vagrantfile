# -*- mode: ruby -*-
# vi: set ft=ruby :

ETH_DEV = "Intel(R) Dual Band Wireless-AC 8265"
BOX_IMAGE = "centos/8"
BOX_VERSION = "2011.0"

Vagrant.configure("2") do |config|
  config.vm.define "cicd", autostart: true do |cicd|
    cicd.vm.box = BOX_IMAGE
    cicd.vm.box_version = BOX_VERSION
    cicd.vm.hostname = "cicd"
    cicd.vm.network :public_network, type: "dhcp", use_dhcp_assigned_default_route: true, bridge: ETH_DEV
    cicd.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "cicd"
      vb.cpus = 1
      vb.memory = 1024
    end
    cicd.vm.provision "ansible" do |ansible|
      ansible.playbook = "init.yml"
    end
    cicd.vm.provision "shell", inline: <<-SHELL
      sudo yum install -y epel-release
      sudo yum install -y ansible git yamllint
      sudo sed -i "s/.*PasswordAuthentication.*/PasswordAuthentication yes/g" /etc/ssh/sshd_config
      sudo systemctl restart sshd
    SHELL
    cicd.vm.post_up_message = "Możesz teraz się zalogować za pomocą SSH: vagrant/vagrant"
  end

  config.vm.define "node1" do |node1|
    node1_name = "node1"
    node1.vm.box = BOX_IMAGE
    node1.vm.box_version = BOX_VERSION
    node1.vm.hostname = "node1"
    node1.vm.network :public_network, type: "dhcp", use_dhcp_assigned_default_route: true, bridge: ETH_DEV
    node1.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "node1"
      vb.cpus = 1
      vb.memory = 1024
    end
    node1.vm.provision "shell", inline: <<-SHELL
      sudo sed -i "s/.*PasswordAuthentication.*/PasswordAuthentication yes/g" /etc/ssh/sshd_config
      sudo systemctl restart sshd
    SHELL
    node1.vm.post_up_message = "Możesz teraz się zalogować za pomocą SSH: vagrant/vagrant"
  end

  config.vm.define "node2" do |node2|
    node2_name = "node2"
    node2.vm.box = BOX_IMAGE
    node2.vm.box_version = BOX_VERSION
    node2.vm.hostname = "node2"
    node2.vm.network :public_network, type: "dhcp", use_dhcp_assigned_default_route: true, bridge: ETH_DEV
    node2.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "node2"
      vb.cpus = 1
      vb.memory = 1024
    end
    node2.vm.provision "shell", inline: <<-SHELL
      sudo sed -i "s/.*PasswordAuthentication.*/PasswordAuthentication yes/g" /etc/ssh/sshd_config
      sudo systemctl restart sshd
    SHELL
    node2.vm.post_up_message = "Możesz teraz się zalogować za pomocą SSH: vagrant/vagrant"
  end
end
