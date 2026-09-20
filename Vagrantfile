Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.boot_timeout = 900

  config.vm.provider :virtualbox do |v|
    v.memory = 1512
    v.cpus = 2
  end

  boxes = [
    { :name => "web", :ip => "192.168.56.10" },
    { :name => "log", :ip => "192.168.56.15" }
  ]

  boxes.each do |opts|
    config.vm.define opts[:name] do |node|
      node.vm.hostname = opts[:name]
      node.vm.network "private_network", ip: opts[:ip]

      if opts[:name] == boxes.last[:name]
        node.vm.provision "ansible" do |ansible|
          ansible.playbook = "ansible/provision.yml"
          ansible.inventory_path = "ansible/hosts"
          ansible.host_key_checking = "false"
          ansible.limit = "all"
        end
      end
    end
  end
end
