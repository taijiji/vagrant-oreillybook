# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :debian10 do |debian|
    debian.vm.box = "debian/buster64"
    debian.vm.box_version = "10.4.0"
    debian.vm.hostname= "buster"
  end
  
  config.vm.define :ubuntu20 do |ubuntu|
    ubuntu.vm.box = "ubuntu/focal64"
    ubuntu.vm.hostname= "focal"
  end
  
  config.vm.define :ubuntu14 do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-14.04"
    ubuntu.vm.hostname= "trusty"
  end

  config.vm.define :centos8stream do |centos|
    centos.vm.box = "centos/stream8"
    centos.vm.hostname = "centos"
  end
  
  config.vm.define :centos8 do |centos|
    centos.vm.box = "centos/8"
    centos.vm.hostname = "centos"
  end
  
  config.vm.define :centos71 do |centos|
    centos.vm.box = "bento/centos-7.1"
    centos.vm.hostname = "centos"
  end

end
