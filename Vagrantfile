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
    # enp0s3 = dhcp = vagrant ssh target
    # enp0s8
    ubuntu.vm.network "private_network", virtualbox__intnet: true, ip: "192.168.99.10"
    #ubuntu.vm.provider "virtualbox" do |vb|
    #  vb.memory = "2048" 
    #end
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

  config.vm.define :csr do |csr|
    csr.vm.box = "cisco/csr1000v"
    # Turn off shared folders
    csr.vm.synced_folder ".", "/vagrant", id: "vagrant-root", disabled: true
    # Do not try to insert new SSH key
    csr.ssh.insert_key = false
    # GigabitEthernet1 = dhcp = vagrant ssh target
    # GigabitEthernet2
    csr.vm.network "private_network", ip: "192.168.99.11"
  end

  config.vm.define :eos do |eos|
    eos.vm.box = "arista/veos"
    eos.vm.hostname = "eos"
    # Create Ethernet1
    eos.vm.network "private_network", virtualbox__intnet: true,
      ip: "192.168.99.12", auto_config: false
    #eos.vm.network "private_network", ip: "192.168.99.12"
    
    eos.vm.provider :virtualbox do |vb|
      # nic1 is always Management1 which is set to dhcp in the basebox.

      # Patch Ethernet1 to a particular internal network
      #vb.customize ['modifyvm', :id, '--nic2', 'intnet',
      #  '--intnet2', 'vEOS-intnet1']
    end
  end

end
