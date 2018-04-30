# Vagrant file to download ubuntu server

Vagrant.configure("2") do |config|
  config.vm.box = "minimal/trusty64"
  config.vm.define "dotfiles-test"
  config.vm.hostname = "dotfiles-test"

  # Add my username instead of default vagrant
  # config.vm.provision "file", source: "files/id_rsa.pub", destination: "~/.ssh/authorized_keys"
  # config.ssh.insert_key = false
  # config.ssh.username = "mreyes"
  # config.ssh.private_key_path = "files/id_rsa"
  # config.vm.provision "shell", inline: "cat files/id_rsa.pub >> ~/vagrant/.ssh/authorized_keys"

  # Start with a fresh user profile
  config.vm.provision "shell", inline: <<-EOC
    sudo userdel -r mreyes
    sudo useradd -m -p '$1$/el/UAqR$RXZeRMg.eVCwCYdMmTTDD.' -s /bin/bash mreyes
  EOC

  # Disable usb - minimal vagrant box had error with usb enabled
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["modifyvm", :id, "--usbehci", "off"]
  end

end
