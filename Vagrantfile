Vagrant.configure("2") do |config|
  config.vm.define "s" do |s|
    s.vm.box = "centos/7"
    s.vm.hostname = "s"
    s.vm.network "private_network", ip: "172.42.42.101"
  end

  config.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
  end

  config.vm.define "m" do |m|
    m.vm.box = "ubuntu/bionic64"
    m.vm.hostname = "m"
    m.vm.network "private_network", ip: "172.42.42.100"

    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end

    m.vm.provision "ansible_local" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "main.yml"
      ansible.inventory_path = "inventory/hosts"
      ansible.config_file = "ansible.cfg"
      ansible.limit = "all"
    end
  end
end