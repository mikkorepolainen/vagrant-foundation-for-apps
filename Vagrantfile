Vagrant::Config.run do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  config.vm.forward_port 8079, 8079
  config.vm.provision :shell, :inline => "sudo apt-get update"
  config.vm.provision :shell, :inline => "sudo apt-get -y install curl build-essential software-properties-common python-software-properties"
  config.vm.provision :shell, :inline => "sudo add-apt-repository ppa:brightbox/ruby-ng"
  config.vm.provision :shell, :inline => "sudo apt-get update"
  config.vm.provision :shell, :inline => "sudo apt-get -y install git"
  config.vm.provision :shell, :inline => "curl -sSL https://deb.nodesource.com/setup_5.x | sudo -E bash"
  config.vm.provision :shell, :inline => "sudo apt-get -y install nodejs"
  config.vm.provision :shell, :inline => "sudo apt-get -y install ruby2.2-dev ruby2.2"
  config.vm.provision :shell, :inline => "sudo gem install bundler"
  config.vm.provision :shell, :inline => "sudo npm install -g foundation-cli bower gulp"
  config.ssh.forward_agent = true
end
