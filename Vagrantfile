# -*- mode: ruby -*-
# vi: set ft=ruby :

RAM = ENV["VM_RAM"]
CPUS = ENV["VM_CPUS"]

Vagrant.configure(2) do |config|
  config.vm.box = "idi/fedora22"

  config.vm.provider :virtualbox do |v|
    v.customize ['modifyvm', :id, '--memory', RAM] if RAM
    v.customize ['modifyvm', :id, '--cpus', CPUS] if CPUS
  end

  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__exclude: ".git/"

  config.vm.provision "shell", inline: <<-SHELL
    sudo dnf -y install gcc yum-utils
  SHELL
  
end
