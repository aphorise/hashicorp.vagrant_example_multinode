Vagrant.configure("2") do |config|
  # // NUMBER OF INSTANCES
  iN = 2
  # // ^^ UP TO 9 <= iN > 0
  config.vm.box = "aphorise/ubuntu16-nginx"
  config.vm.box_version = "0.0.1"
  config.vm.provider "virtualbox"

  (1..iN).each do |iX|
    config.vm.define vm_name="nginx#{iX}" do |node|
      node.vm.box = "aphorise/ubuntu16-nginx"
      node.vm.hostname = vm_name
      node.vm.network "forwarded_port", guest: 80, host: "5808#{iX}", id: "nginx#{iX}"
   end
  end
end
