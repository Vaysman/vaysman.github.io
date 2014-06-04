# encoding: utf-8
# This file originally created at http://rove.io/91aa0addc0c4836c66feafefcfb0710c

# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "opscode-ubuntu-12.04_chef-11.4.0"
  config.vm.box_url = "https://opscode-vm-bento.s3.amazonaws.com/vagrant/opscode_ubuntu-12.04_chef-11.4.0.box"
  config.ssh.forward_agent = true

  config.vm.network :forwarded_port, guest: 4000, host: 4040

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]
    chef.add_recipe :apt
    chef.add_recipe 'rvm::vagrant'
    chef.add_recipe 'rvm::system'
    chef.add_recipe 'vim'
    chef.add_recipe 'tmux'
    chef.add_recipe 'git'
    chef.json = {
      :vim => {
        :extra_packages => [
          "vim-rails"
        ]
      },
      :git => {
        :prefix => "/usr/local"
      }
    }
  end
end
