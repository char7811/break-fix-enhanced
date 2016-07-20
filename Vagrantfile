# -*- mode: ruby -*-

# vi: set ft=ruby :

Vagrant.require_version ">= 1.8"
#groups = {
#  "packstack" => ["BF2", "BF3"]
#  "loadbalancers" => ["ariadne"],
#  "all_groups:children" => ["webservers", "loadbalancers"]
#}

Vagrant.configure(2) do |config|
    config.vm.provider "virtualbox" do |v|
    #    #        #v.customize ["modifyvm", :id, "--name", "BF2"]
        v.customize ["modifyvm", :id, "--cpus", "2"]
        v.customize ["modifyvm", :id, "--memory", "6144"]
    end    
	  config.vm.define :BF2 do |a|
	    a.vm.box = "centos/7"
	    a.vm.network :private_network,  ip: "192.168.56.10"
	    a.vm.hostname = "BF2"
	    a.vm.provision "ansible" do |ansible|
	      ansible.playbook = "playbook2.yml"
	    end
	  end
    

	  config.vm.define :BF3 do |b|
	    b.vm.box = "centos/7"
	    b.vm.network :private_network,  ip: "192.168.56.20"
	    b.vm.hostname = "BF3"
            b.vm.provision "ansible" do |ansible|
              ansible.playbook = "playbook2.yml"
	      ansible.playbook = "playbook2_cont.yml"
	      ansible.groups = { "group1" => ["BF[2:3]"] }
	      #ansible.playbook = "playbook2_cont.yml"
            end
#	    config.vm.provider "virtualbox" do |w|
        #w.customize ["modifyvm", :id, "--name", "BF3"]
#        w.customize ["modifyvm", :id, "--cpus", "2"]
#        w.customize ["modifyvm", :id, "--memory", "6144"]
#        config.vm.provision "ansible" do |ansible|
#            ansible.verbose = "vvv"
#            ansible.playbook = "playbook2.yml"
#            ansible.playbook = "playbook2_cont.yml"
#	    ansible.groups = {
#              "group1" => ["BF[2:3]"]
#	   }
#        end 
#    end
	   end
end
#  config.vm.provision "ansible" do |ansible|
#    ansible.verbose = "vvv"
#    ansible.playbook = "playbook2.yml"
#    ansible.playbook = "playbook2_cont.yml"
#    ansible.groups = {
#        "group1" => ["BF[2:3]"]
#    }
#  end

#  config.vm.provision "ansible" do |ansible|
   #ansible.verbose = "vvv"
#    ansible.playbook = "playbook2.yml"
#  end
#          

#end
