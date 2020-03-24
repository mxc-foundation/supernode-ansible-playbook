# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "vagrant" do |box|
    box.vm.box = "debian/contrib-buster64"
    # box.vm.box = "debian/contrib-stretch64"
    # box.vm.box = "ubuntu/bionic64"
    # box.vm.box = "ubuntu/xenial64"

    box.vm.network "forwarded_port", guest: 80,   host: 8080, protocol: "tcp"
    box.vm.network "forwarded_port", guest: 1700, host: 1700, protocol: "udp"
    box.vm.network "forwarded_port", guest: 1883, host: 1883, protocol: "tcp"
    box.vm.network "forwarded_port", guest: 1884, host: 1884, protocol: "tcp"

    box.vm.provision "ansible_local" do |ansible|
      ansible.install         = true
      ansible.playbook        = "full_deploy.yml"
      ansible.config_file     = "ansible.cfg"
    end
  end
end
