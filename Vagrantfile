
machines = {
  "control-plane" => {"ip"=>"220", "memory" => "2048", "cpus"=>"2"},
  "worker1" => {"ip"=>"221", "memory" => "2048", "cpus"=>"2"},
  "worker2" => {"ip"=>"222", "memory" => "2048", "cpus"=>"2"},
}

Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  
  machines.each do |name,conf|
    config.vm.define "#{name}" do |machine|
      # Network and Hostname configuration
      machine.vm.network "public_network", bridge: "wlxd03745c35bb7"
      machine.vm.hostname = "#{name}.example.org"
      machine.vm.provider "virtualbox" do |vb|
        vb.cpus = "#{conf["cpus"]}"
	vb.memory = "#{conf["memory"]}"
	vb.name = "#{name}"
	vb.gui = false
      end
      
    end
  end
  
  config.vm.provision "shell",
    run: "always",
    inline: " ip route del default && ip route add default via 192.168.0.1 dev eth1"
  
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = true
    ansible.playbook = "playbook.yaml"
  end
end
