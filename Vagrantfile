Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"
  
    config.vm.network "forwarded_port", guest: 8080, host: 12344
  
    config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
  
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y build-essential
  
      gcc -o /vagrant/dummyserv /vagrant/dummy_serv.c
  
      /vagrant/dummyserv 8080
    SHELL
  end
  