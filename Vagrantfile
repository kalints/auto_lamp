# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provision "shell", inline: <<-SHELL
  curl -o bootstrap-salt.sh -L https://bootstrap.saltstack.com
  sudo sh bootstrap-salt.sh -M stable
  SHELL
end
