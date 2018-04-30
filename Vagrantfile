# encoding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :
# Modify vagrant_config.yaml to make adjustmets

require 'yaml'

current_dir    = File.dirname(File.expand_path(__FILE__))
configs        = YAML.load_file("#{current_dir}/vagrant_config.yaml")
vagrant_config = configs['configs']
username       = configs['configs']['username']
password       = configs['configs']['encrypted_pass']

Vagrant.configure("2") do |config|
  config.vm.box = vagrant_config['vagrant_box']
  config.vm.define vagrant_config['hostname']
  config.vm.hostname = vagrant_config['hostname']

  # Disable usb - minimal vagrant box had error with usb enabled
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["modifyvm", :id, "--usbehci", "off"]
  end

  # Start with a fresh user profile
  # MUST USE SINGLE QUOTES BELOW DUE TO PASSWORD FIELD
  config.vm.provision "shell", inline: <<-EOC
    sudo userdel -r '#{username}' 2> /dev/null
    sudo useradd -m -p '#{password}' -s /bin/bash '#{username}'
  EOC

  if vagrant_config["sudo"] == true
    config.vm.provision "shell", inline: <<-EOC
      sudo usermod -aG sudo '#{username}' || exit 0
      sudo usermod -aG wheel '#{username}' || exit 0
    EOC
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yaml"
  end


end
