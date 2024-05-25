# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/noble"
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 512]
  end

  #
  # 192.168.5.9 is the pgbouncer vip
  # 192.168.5.10 is the postgres vip
  #
  config.vm.define :pg01, primary: true do |pg01_config|
    pg01_config.vm.hostname = 'pg01'
    pg01_config.vm.network :private_network, ip: "192.168.5.11"
    pg01_config.vm.provision :shell, :path => "postgresql-setup.sh"
  end
  config.vm.define :pg02 do |pg02_config|
    pg02_config.vm.hostname = 'pg02'
    pg02_config.vm.network :private_network, ip: "192.168.5.12"
    pg02_config.vm.provision :shell, :path => "postgresql-setup.sh"
  end
  config.vm.define :pg03 do |pg03_config|
    pg03_config.vm.hostname = 'pg03'
    pg03_config.vm.network :private_network, ip: "192.168.5.13"
    pg03_config.vm.provision :shell, :path => "postgresql-setup.sh"
  end
end
