# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.hostname = "gitlab.local.dev"
    
    config.vm.network :private_network, ip: "192.168.11.8"
    config.vm.network :forwarded_port, guest: 80, host: 8080

    config.vm.provider "virtualbox" do |vb|
        vb.name = "GitLab Server"
        vb.memory = "8192"
        vb.cpus = "4"

        vb.customize [ "guestproperty", "set", :id, "/VirtualBox/GuestAdd/VBoxService/ — timesync-set-threshold", 10000 ]
    end

    config.vm.provision :docker
    config.vm.provision "shell", path: "install_gitlab.sh"
end
