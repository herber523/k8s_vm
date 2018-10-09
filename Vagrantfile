VAGRANTFILE_API_VERSION = "2"
BOX = "centos/7"
BASE_IP = "192.168.31.23"

MASTER_CPU = 2
MASTER_MEM = 4096

NODE_CPU = 4
NODE_MEM = 8192
NODE_NUM = 3

Vagrant.configure(VAGRANTFILE_API_VERSION) do | config |
  config.vm.provision "shell", inline: "swapoff -a"
  config.vm.define "master" do | master |
    master.vm.box = BOX
    master.vm.hostname = "master"
    master.vm.network "public_network", ip: "#{BASE_IP}0"
    master.vm.provider :virtualbox do |vb|
      vb.memory = MASTER_MEM
      vb.cpus = MASTER_CPU
    end
  end
  (1..NODE_NUM).each do |n|
    config.vm.define "node#{n}" do | node |
      node.vm.box = BOX
      node.vm.network "public_network", ip: "#{BASE_IP}#{n}"
      node.vm.hostname = "node#{n}"
      node.vm.provider :virtualbox do |vb|
        vb.memory = NODE_MEM
        vb.cpus = NODE_CPU
      end
    end
  end
end
