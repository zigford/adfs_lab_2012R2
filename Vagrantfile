# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.provider :libvirt do |libvirt|
    libvirt.hyperv_feature :name => 'relaxed', :state => 'on'
    libvirt.hyperv_feature :name => 'vapic', :state => 'on'
    libvirt.memory = "1024"
    libvirt.volume_cache = "unsafe"
    libvirt.cpus = 2
  end

  config.vm.box = "peru/windows-server-2012_r2-standard-x64-eval"

  # define dc01
  config.vm.define "dc" do |dc|
    dc.vm.hostname = "dc"
    dc.vm.network "private_network", ip: "192.168.33.10"
    #dc.vm.provision "ansible" do |ansible|
    #  ansible.playbook = "dc-playbook.yml"
    #end
  end
  config.vm.define "adfs01" do|adfs01|
    adfs01.vm.box = "peru/windows-server-2019-datacenter-x64-eval"
    adfs01.vm.provider :libvirt do | lv |
      lv.memory = 2048
      lv.cpus = 4
    end
    adfs01.vm.hostname = "adfs01"
    adfs01.vm.network "private_network", ip: "192.168.33.20"
  end
  
  config.vm.define "adfs02" do|adfs02|
    adfs02.vm.hostname = "adfs02"
    adfs02.vm.network "private_network", ip: "192.168.33.60"
  end

  config.vm.define "app" do|app|
    app.vm.hostname = "app"
    app.vm.network "private_network", ip: "192.168.33.30"
  end

  config.vm.define "workstation" do | workstation |
    workstation.vm.hostname = "workstation"
    workstation.vm.network "private_network", ip: "192.168.33.40"
  end

  config.vm.define "proxy" do | proxy |
    proxy.vm.hostname = "proxy"
    proxy.vm.network "private_network", ip: "192.168.33.50"
  end

  config.vm.define "ext" do | ext |
    ext.vm.hostname = "ext"
    ext.vm.network "private_network", ip: "192.168.33.100"
  end

  config.vm.define "adfs03" do | adfs03 |
    adfs03.vm.box = "peru/windows-server-2019-datacenter-x64-eval"
    adfs03.vm.provider :libvirt do | lv |
      lv.memory = 2048
      lv.cpus = 4
    end
    adfs03.vm.hostname = "adfs03"
    adfs03.vm.network "private_network", ip: "192.168.33.80"
  end

  config.vm.define "proxy02" do | proxy02 |
    proxy02.vm.box = "peru/windows-server-2019-datacenter-x64-eval"
    proxy02.vm.provider :libvirt do | lv |
      lv.memory = 2048
      lv.cpus = 4
    end
    proxy02.vm.hostname = "proxy02"
    proxy02.vm.network "private_network", ip: "192.168.33.55"
  end
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
