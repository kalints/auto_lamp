# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y salt-api
    apt-get install -y salt-cloud
    apt-get install -y salt-master
    apt-get install -y salt-minion
    apt-get install -y salt-ssh
    apt-get install -y salt-syndic
  SHELL
end
