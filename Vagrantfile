# # -*- mode: ruby -*-
# # vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Control Plane Nodes
  (0..2).each do |cp|
    config.vm.define "vk8s-cp#{cp}" do |node|
      node.vm.box = "ubuntu/jammy64"
      
      node.vm.hostname = "vk8s-cp#{cp}"

      node.vm.network "private_network", ip: "192.168.56.2#{cp}"
      node.vm.network "forwarded_port", id: "ssh", guest: 22, host: "220#{cp}"
      
      node.vm.synced_folder ".", "/vagrant", disabled: true

      config.ssh.insert_key = false

      config.vm.provider "virtualbox" do |vb|
        #vb.name   = "vk8s-cp#{cp}"
        vb.memory = "2048"
        vb.cpus   = "2"
      end
    end
  end

  config.vm.define "vk8s-lb" do |node|
  node.vm.box = "ubuntu/jammy64"
  
  node.vm.hostname = "vk8s-lb"

  node.vm.network "private_network", ip: "192.168.56.25"
  node.vm.network "forwarded_port", id: "ssh", guest: 22, host: "2210"
  
  node.vm.synced_folder ".", "/vagrant", disabled: true

  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |vb|
    #vb.name   = "vk8s-w#{w}"
    vb.memory = "2048"
    vb.cpus   = "2"
  end
end

  #Worker Nodes
  (0..2).each do |w|
    config.vm.define "vk8s-w#{w}" do |node|
      node.vm.box = "ubuntu/jammy64"
      
      node.vm.hostname = "vk8s-w#{w}"

      node.vm.network "private_network", ip: "192.168.56.3#{w}"
      node.vm.network "forwarded_port", id: "ssh", guest: 22, host: "222#{w}"
      
      node.vm.synced_folder ".", "/vagrant", disabled: true

      config.ssh.insert_key = false

      config.vm.provider "virtualbox" do |vb|
        #vb.name   = "vk8s-w#{w}"
        vb.memory = "2048"
        vb.cpus   = "2"
      end
    end
  end

end

  
#   # Enable provisioning with a shell script. Additional provisioners such as
#   # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
#   # documentation for more information about their specific syntax and use.
#   # config.vm.provision "shell", inline: <<-SHELL
#   #   apt-get update
#   #   apt-get install -y apache2
#   # SHELL
# #end

