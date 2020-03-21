Vagrant.configure("2") do |config|
  config.vm.define "db" do |db|
	  config.vm.box = "ubuntu/trusty64"
	  db.vm.network "private_network", ip: "192.168.10.102"
	  db.vm.network "forwarded_port", guest: 5432, host: 5432
	  config.vm.provision "ansible_local" do |ansible|
		ansible.playbook = "playbook-db.yml"
		ansible.become = true
	  end
  end
  config.vm.define "web" do |web|
	  config.vm.box = "ubuntu/trusty64"
	  web.vm.network "private_network", ip: "192.168.10.101"
	  web.vm.network "forwarded_port", guest: 8080, host: 8080
	  config.vm.provision "ansible_local" do |ansible|
		ansible.playbook = "playbook-web.yml"
		ansible.become = true
	  end
  end
end