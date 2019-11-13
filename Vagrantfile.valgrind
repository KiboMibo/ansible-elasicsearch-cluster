# -*- mode: ruby -*- 
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config| config.ssh.insert_key = false
	config.vm.provider :parallels do |prl|
		prl.memory = 2048	
	end

	# First elastic node.
	config.vm.define "el-one" do |els|
		els.vm.hostname = "elastic-one.dev"
		els.vm.box = "bento/centos-7.7"
		els.vm.network :private_network, ip: "192.168.60.10"
	end

	# Second elastic node.
	config.vm.define "el-two" do |els|
		els.vm.hostname = "elastic-two.dev"
		els.vm.box = "bento/centos-7.7"
		els.vm.network :private_network, ip: "192.168.60.11"
	end

	# Third elastic node.
	config.vm.define "el-three" do |els|
		els.vm.hostname = "elastic-three.dev"
		els.vm.box = "bento/centos-7.7"
		els.vm.network :private_network, ip: "192.168.60.12"
	end

	config.vm.provision "ansible" do |ansible| ansible.playbook = "playbook.yml"
		# Run commands as root.
		ansible.become = true
	end 
end
