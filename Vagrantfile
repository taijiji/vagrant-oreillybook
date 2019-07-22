# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :debian do |debian|
    debian.vm.box = "bento/debian-10.0"
    debian.vm.box_version = "201907.07.0"
    debian.vm.hostname= "bullseye"
  end
  
  config.vm.define :ubuntu do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-18.04"
  end
  
  config.vm.define :centos do |centos|
    centos.vm.box = "bento/centos-7.6"
    centos.vm.hostname = "centos"
  end
  
end
