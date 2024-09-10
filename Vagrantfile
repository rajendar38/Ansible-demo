Vagrant.configure("2") do |config|  
  #Creation of ansiblecontrol VM.
      config.vm.define "ansiblecontrol" do |ansiblecontrol|
          ansiblecontrol.vm.box = "shekeriev/debian-11"
          ansiblecontrol.vm.hostname = "ansiblecontrol"
          ansiblecontrol.vm.network "private_network", ip: "192.168.56.10"
          ansiblecontrol.vm.provider "virtualbox" do |vb|
              vb.name = "ansiblecontrol"
              vb.memory = "2048"
              vb.cpus = 2
          end 
          # Config hosts, Install vim, pip
              ansiblecontrol.vm.provision "shell", path: "script.sh"          
              #ansiblecontrol.vm.provision "shell", inline: "apt -y install git"
              ansiblecontrol.vm.provision "ansible_local" do |ansible|
                ansible.playbook = "playbook.yml"
                ansible.install_mode = "pip"
              # Config hosts, Install vim, pip
               ansiblecontrol.vm.provision "shell", path: "script.sh"                  
          end
              
      end 
      #Creation of AD WIN VM.   
      config.vm.define "adwin" do |adwin|
        adwin.vm.box = "gusztavvargadr/windows-server"
        adwin.vm.hostname = "adwin"        
        
        adwin.winrm.username= "vagrant"
        adwin.winrm.password= "vagrant"
        adwin.vm.guest = :windows
        adwin.vm.communicator = "winrm"

        adwin.vm.network "private_network", ip: "192.168.56.15"

        adwin.vm.network "forwarded_port", guest: 5985, host: 5985, id: "winrm", auto_correct: true
        adwin.vm.network "forwarded_port", guest: 3389, host: 3389, id: "rdp", auto_correct: true

        adwin.windows.set_work_network = true

        adwin.vm.provider "virtualbox" do |vb|
          vb.name = "adwin"
          vb.memory = "8192"
          vb.cpus = 2
        end
        adwin.vm.provision "shell", inline: <<-SHELL
         # Enable ICMP (ping) in Windows Firewall
        netsh advfirewall firewall add rule name="ICMP Allow incoming V4 echo request" protocol=icmpv4:8,any dir=in action=allow
        SHELL
        adwin.vm.provision "shell", path: "ConfigRemoteAnsible.ps1"
      #Creation of Client Windows 11 VM.
      end

    
end


