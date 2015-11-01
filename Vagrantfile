# Vim
# vim: set filetype=ruby:
# vim: set ft=ruby:
#
# Emacs
# -*- mode: ruby; -*-

VAGRANTFILE_API_VERSION = "2"
MAX_MEMORY = 512

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

    # Vagrant box to build on
    config.vm.box = "ubuntu/trusty64"

    # host to guest port forwarding
    config.vm.network :forwarded_port, guest: 1337, host: 1337

    # settings for VirtualBox provider
    config.vm.provider "virtualbox" do |v, override|
        v.memory = MAX_MEMORY
	v.cpus = 2
        override.vm.synced_folder ".", "/app"
    end

    # call provisioner shell scripts
    config.vm.provision :shell, path: "./enable-swap.sh", run: "always"
    config.vm.provision :shell, path: "./provisioner.sh"
    config.vm.provision :shell, path: "./postinstall.sh", privileged: false
end
