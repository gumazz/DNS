Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  config.vm.provider "virtualbox" do |v|
	  v.memory = 256
  end

  config.vm.define "ns01" do |ns01|
    ns01.vm.network "private_network", ip: "192.168.50.10"
    ns01.vm.hostname = "ns01"
   ns01.vm.provision "shell", inline: <<-SHELL
     mkdir -p ~root/.ssh
     cp ~vagrant/.ssh/auth* ~root/.ssh
   SHELL
   ns01.vm.provision "ansible" do |ansible|
     ansible.playbook = "ansible/provision.yml"
     ansible.inventory_path = "ansible/hosts"
   end
  end

  config.vm.define "ns02" do |ns02|
    ns02.vm.network "private_network", ip: "192.168.50.11"
    ns02.vm.hostname = "ns02"
   ns02.vm.provision "shell", inline: <<-SHELL
     mkdir -p ~root/.ssh
     cp ~vagrant/.ssh/auth* ~root/.ssh
   SHELL
   ns02.vm.provision "ansible" do |ansible|
     ansible.playbook = "ansible/provision.yml"
     ansible.inventory_path = "ansible/hosts"
   end
  end

  config.vm.define "client" do |client|
    client.vm.network "private_network", ip: "192.168.50.15"
    client.vm.hostname = "client"
   client.vm.provision "shell", inline: <<-SHELL
     mkdir -p ~root/.ssh
     cp ~vagrant/.ssh/auth* ~root/.ssh
   SHELL
   client.vm.provision "ansible" do |ansible|
     ansible.playbook = "ansible/provision.yml"
     ansible.inventory_path = "ansible/hosts"
   end
  end

  config.vm.define "client2" do |client2|
    client2.vm.network "private_network", ip: "192.168.50.16"
    client2.vm.hostname = "client2"
   client2.vm.provision "shell", inline: <<-SHELL
     mkdir -p ~root/.ssh
     cp ~vagrant/.ssh/auth* ~root/.ssh
   SHELL

   client2.vm.provision "ansible" do |ansible|
     ansible.playbook = "ansible/provision.yml"
     ansible.inventory_path = "ansible/hosts"
   end
  end

end

