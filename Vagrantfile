# -*- mode: ruby -*-
# vi: set ft=ruby :

nodes = [
	{ :hostname => 'kube-master', :memory => 3076, :cpu => 2, :boxname => "ubuntu/xenial64" },

]


Vagrant.configure("2") do |config|
  nodes.each do |node|
      config.vm.box_check_update = false
      config.vm.define node[:hostname] do |nodeconfig|
          nodeconfig.vm.box = node[:boxname]
          nodeconfig.vm.hostname = node[:hostname]
          nodeconfig.vm.provider :virtualbox do |vb|
            vb.memory = node[:memory]
            vb.cpus = node[:cpu]
          end
        end
  end

  config.vm.provision "ansible" do |ansible|
     ansible.playbook = "bootstrap.yml"
  end


end
