Vagrant.configure("2") do |config|

  config.ssh.private_key_path =  ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
  config.ssh.insert_key = false


  config.ssh.forward_agent = true

  config.vm.box_check_update = false
  config.vm.box = "generic/centos7" 
  config.vm.define "srv1" do |srv1|
    srv1.vm.hostname = 'srv1.example.com'
    srv1.vm.network :"private_network", ip: "10.0.0.10"
    srv1.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
    srv1.vm.provider :virtualbox do |vb|
      vb.name = "srv1"
      vb.linked_clone = true
    end
  end
  config.vm.box_check_update = false
  config.vm.box = "generic/centos7" 
  config.vm.define "srv2" do |srv2|
    srv2.vm.hostname = 'srv2.example.com'
    srv2.vm.network :"private_network", ip: "10.0.0.20"
    srv2.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
    srv2.vm.provider :virtualbox do |vb|
      vb.name = "srv2"
      vb.linked_clone = true
    end
  end

end