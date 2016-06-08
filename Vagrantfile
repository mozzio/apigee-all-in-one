VAGRANTFILE_API_VERSION = "2"

edge_host = <<EDGE
echo "127.0.0.1	localhost\n::1		localhost\n192.168.33.10	edge" > /etc/hosts
EDGE

baas_host = <<BAAS
echo "127.0.0.1	localhost\n::1		localhost\n192.168.33.20	baas" > /etc/hosts
BAAS

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "edge" do |edge|
    edge.vm.box = "centos66"
    edge.vm.network "private_network", ip: "192.168.33.10"
    edge.vm.hostname = "edge"
    edge.vm.synced_folder ".", "/vagrant", mount_options: ['dmode=775','fmode=775']
    edge.vm.provision :shell, :inline => edge_host
  end

  config.vm.define "baas" do |baas|
    baas.vm.box = "centos66"
    baas.vm.network "private_network", ip: "192.168.33.20"
    baas.vm.hostname = "baas"
    baas.vm.synced_folder ".", "/vagrant", mount_options: ['dmode=775','fmode=775']
    baas.vm.provision :shell, :inline => baas_host
  end

  config.vm.provider :virtualbox do |vb|
    vb.customize ["setextradata", :id, "VBoxInternal/Devices/VMMDev/0/Config/GetHostTimeDisabled", 0]
    vb.customize ["modifyvm", :id, "--memory", "1536"]
  end

end
