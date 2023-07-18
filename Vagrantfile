Vagrant.require_version ">= 2.2.14"

servers = [
    { 
        :box_name => "astralinux",
        :hostname => "astra",
        :ip => "192.168.56.10",
        :ram => 2048,
        :cpu => 2
    }, { 
        :box_name => "base-alt",
        :hostname => "alt",
        :ip => "192.168.56.11",
        :ram => 2048,
        :cpu => 2
    }, { 
        :box_name => "centos7-base",
        :hostname => "centos7",
        :ip => "192.168.56.12",
        :ram => 2048,
        :cpu => 2
    }, { 
        :box_name => "redos73",
        :hostname => "redos73",
        :ip => "192.168.56.13",
        :ram => 2048,
        :cpu => 2
    }
]

Vagrant.configure("2") do |config|
    servers.each do |machine|
        config.vm.box = "centos7-base"
        config.vm.box_check_update = false
        config.vm.define machine[:hostname] do |node|

            node.vm.hostname = machine[:hostname]
            node.vm.network "private_network", ip: machine[:ip]

            # VB provider settings
            node.vm.provider "virtualbox" do |vb|
                vb.memory = machine[:ram]
                vb.cpus = machine[:cpu]
                vb.check_guest_additions = false
                vb.gui = false
                vb.customize ["modifyvm", :id, "--vram", "128"]
                vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
            end           
        end
    end
end