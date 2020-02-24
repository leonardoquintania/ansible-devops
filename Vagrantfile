Vagrant.configure("2") do |config|

  #config.vm.box = "ubuntu/trusty64"
  config.vm.box = "ubuntu/bionic64"

  config.vm.define "wordpress" do |wordpress|

    wordpress.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.name = "ubuntu_wordpress"
    end

    wordpress.vm.network "private_network", ip: "172.17.177.40"
      
    wordpress.vm.provision "shell", inline: "sudo apt-get -y update && sudo apt -y update && sudo apt-get -y upgrade && sudo apt -y upgrade"
    
    wordpress.vm.provision "shell", inline: "sudo apt install -y python3-pip"

    wordpress.vm.provision "shell",
      inline: "cat /vagrant/configs/ssh-keys/vagrant_id_rsa.pub >> .ssh/authorized_keys"

    wordpress.vm.provision "shell",
      inline: "cp /vagrant/configs/ssh-keys/vagrant_id_rsa /home/vagrant/vagrant_id_rsa && \
        chmod 600 /home/vagrant/vagrant_id_rsa && \
        chown vagrant:vagrant /home/vagrant/vagrant_id_rsa"
  end

  config.vm.define "mysql" do |mysql|
    
    mysql.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.name = "mysql_ubunt"
    end

    mysql.vm.network "private_network", ip: "172.17.177.42"
        
    #mysql.vm.provision "shell", inline: "sudo apt-get -y update && sudo apt -y update && sudo apt-get -y upgrade && sudo apt -y upgrade"
    
    #mysql.vm.provision "shell", inline: "sudo apt install -y python3-pip"

    mysql.vm.provision "shell",
      inline: "cat /vagrant/configs/ssh-keys/vagrant_id_rsa.pub >> .ssh/authorized_keys"
      
    mysql.vm.provision "shell",
      inline: "cp /vagrant/configs/ssh-keys/vagrant_id_rsa /home/vagrant/vagrant_id_rsa && \
        chmod 600 /home/vagrant/vagrant_id_rsa && \
        chown vagrant:vagrant /home/vagrant/vagrant_id_rsa"
  end 
  
  config.vm.define "ansible" do |ansible|

    ansible.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.name = "ansible_with"
    end

    ansible.vm.network "private_network", ip: "172.17.177.41"
      
    #ansible.vm.provision "shell", inline: "sudo apt-get -y update && sudo apt -y update && sudo apt-get -y upgrade && sudo apt -y upgrade"
    
    #ansible.vm.provision "shell", inline: "sudo apt install -y python3-pip"

    ansible.vm.provision "shell",
      inline: "cat /vagrant/configs/ssh-keys/vagrant_id_rsa.pub >> .ssh/authorized_keys"
      
    ansible.vm.provision "shell",
      inline: "cp /vagrant/configs/ssh-keys/vagrant_id_rsa /home/vagrant/vagrant_id_rsa && \
        chmod 600 /home/vagrant/vagrant_id_rsa && \
        chown vagrant:vagrant /home/vagrant/vagrant_id_rsa"

    ansible.vm.provision "shell",
      inline: "apt-get update && \
        apt-get install -y software-properties-common && \
        apt-add-repository --yes --update ppa:ansible/ansible && \
        apt-get install -y ansible"
  end


end
