Vagrant.configure(2) do | config |
    config.vm.define "jenkinsmaster" do | jenkinsmaster |
        jenkinsmaster.vm.box = "ubuntu/impish64"
        jenkinsmaster.vm.network "private_network", ip: "192.168.10.11"
        jenkinsmaster.vm.network "forwarded_port", guest: 8080, host: 8082
        jenkinsmaster.vm.hostname = "jenkinsmaster"
        jenkinsmaster.vm.provider "virtualbox" do | vb |
            vb.cpus = 2
            vb.memory = 2048
            vb.name = "jenkinsmaster"
        end
    end
    %w{agentnode1 agentnode2}.each_with_index do | nodename, index |
        config.vm.define nodename do | agentnode |
            agentnode.vm.box = "ubuntu/impish64"
            agentnode.vm.network "private_network", ip: "192.168.10.#{index+12}"            
						agentnode.vm.network "forwarded_port", guest: 8080, host: "#{index+8083}"
            agentnode.vm.hostname = nodename
            agentnode.vm.provider "virtualbox" do | vb |
                vb.cpus = 2
                vb.memory = 2048
                vb.name = nodename
            end
        end
    end
end















