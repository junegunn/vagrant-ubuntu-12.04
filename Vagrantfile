# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise"
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network :private_network, ip: "192.168.100.100"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provision :shell, inline: <<-EOF
    sudo apt-get install -y git openjdk-7-jre-headless ruby rubygems vim-nox unzip

    sudo -u vagrant -H sh -c 'cd ~vagrant; git clone https://github.com/junegunn/dotfiles.git; dotfiles/install'
    sudo -u vagrant -H sh -c 'cd ~vagrant; git clone https://github.com/junegunn/vimfiles.git; vimfiles/install'
  EOF

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", 6 * 1024]
    vb.customize ["modifyvm", :id, "--cpus", 4]
  end
end
