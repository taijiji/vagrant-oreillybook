# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :debian11 do |debian11|
    debian11.vm.box = "boxomatic/debian-11"
    debian11.vm.hostname = "bullseye"
    debian11.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.70", netmask: "255.255.255.0"
  end

  config.vm.define :debian10 do |debian10|
    debian10.vm.box = "debian/buster64"
    debian10.vm.box_version = "10.4.0"
    debian10.vm.hostname = "buster"
  end
  
  config.vm.define :ubuntu20 do |ubuntu|
    ubuntu.vm.box = "ubuntu/focal64"
    ubuntu.vm.hostname = "focal"
    ubuntu.vm.network :forwarded_port, guest: 22, host: 2223
    # enp0s3 = dhcp = vagrant ssh target
    # enp0s8
    ubuntu.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.10",netmask: "255.255.255.0"
    # enp0s9
    ubuntu.vm.network "private_network", virtualbox__intnet: "link_2", ip: "192.168.100.10",netmask: "255.255.255.0"

    #ubuntu.vm.provider "virtualbox" do |vb|
    #  vb.memory = "2048" 
    #end
  end
  
  config.vm.define :ubuntu14 do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-14.04"
    ubuntu.vm.hostname= "trusty"
  end

  config.vm.define :stream8 do |stream8|
    stream8.vm.box = "centos/stream8"
    stream8.vm.hostname = "centos"
    stream8.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.29",netmask: "255.255.255.0"
  end
  
  config.vm.define :centos8 do |centos|
    centos.vm.box = "centos/8"
    centos.vm.network :forwarded_port, guest: 22, host: 2224
    centos.vm.hostname = "centos"
    centos.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.20",netmask: "255.255.255.0"
    centos.vm.network "private_network", virtualbox__intnet: "link_2", ip: "192.168.100.20",netmask: "255.255.255.0"
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
    csr.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.11",netmask: "255.255.255.0"
  end

  config.vm.define :eos do |eos|
    eos.vm.box = "arista/veos"
    # Do not try to insert new SSH key
    eos.ssh.insert_key = false

    # Create Ethernet1
    #eos.vm.network "private_network", virtualbox__intnet: true,
    #  ip: "192.168.99.12", auto_config: false
    eos.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.12",netmask: "255.255.255.0"
    eos.vm.network "private_network", virtualbox__intnet: "link_2", ip: "192.168.100.12",netmask: "255.255.255.0"
    #eos.vm.network "private_network", ip: "192.168.99.12"
    
    #eos.vm.provider :virtualbox do |vb|
      # nic1 is always Management1 which is set to dhcp in the basebox.

      # Patch Ethernet1 to a particular internal network
      # vb.customize ['modifyvm', :id, '--nic2', 'intnet',
      #  '--intnet2', 'vEOS-intnet1']
      #vb.gui = true
    #end
  end

  config.vm.define :srx do |srx|
    srx.vm.box = "juniper/ffp-12.1X47-D15.4-packetmode"
    srx.vm.hostname = "vsrx01"
    srx.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.13",netmask: "255.255.255.0"
  end

  config.vm.define :srx2 do |srx2|
    srx2.vm.box = "juniper/ffp-12.1X47-D15.4-packetmode"
    srx2.vm.hostname = "vsrx02"
    srx2.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.14",netmask: "255.255.255.0"
  end

  #config.vm.define :st2 do |st2|
  #  st2.vm.box = "stackstorm/st2"
  #  st2.vm.hostname = "st2vagrant"
  #  st2.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.9",netmask: "255.255.255.0"
  #  st2.vm.provider :virtualbox do |vb|
  #    vb.gui = false
  #    vb.memory = 4096
  #    vb.cpus = 2
  #  end
  #end

  #config.vm.define :salt do |salt|
  #  salt.vm.box = "ubuntu/focal64"
  #  salt.vm.hostname = "salt"
  #  salt.vm.synced_folder "salt/roots/", "/srv/salt/"
  #  salt.vm.network "private_network", virtualbox__intnet: "link_1", ip: "192.168.99.60",netmask: "255.255.255.0"
  #  salt.vm.provision :salt do |salt|
  #    salt.minion_config = "salt/minion"
  #    salt.run_highstate = true
  #  end
  #end
end
