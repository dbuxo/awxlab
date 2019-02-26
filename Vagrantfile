Vagrant.configure("2") do |config|
  config.vm.define "slave" do |slave|
    slave.vm.box = "centos/7"
    slave.vm.hostname = "s"
    slave.vm.network "private_network", ip: "172.42.42.101"
  end

  config.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
  end

  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/bionic64"
    master.vm.hostname = "m"
    master.vm.network "private_network", ip: "172.42.42.100"

    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end

    master.vm.provision "ansible_local" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "main.yml"
    end
  end
end