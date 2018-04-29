# Vagrant file to download ubuntu server

Vagrant.configure("2") do |config|
  config.vm.box = "minimal/trusty64"
  config.vm.define "dotfiles-test"
  config.vm.hostname = "dotfiles-test"
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["modifyvm", :id, "--usbehci", "off"]
  end

end
