Vagrant.configure(2) do |config|
  config.vm.define "ansibletower.vagrant", primary: true, autostart: true do |config_machine|
      #Assigning a provider
      config_machine.vm.provider :virtualbox do |virtualbox, override|
        virtualbox.name = "Vagrant AnsibleTower"
	    override.vm.box = "ubuntu/trusty64"
        virtualbox.memory = 1024

        # Configuring network
        override.vm.hostname = 'hrs.web'
        override.vm.network "private_network", ip: "214.0.0.201"        
      end

      # Asinging a provisioner
      config_machine.vm.provision :ansible, run: "always" do |provisioner|
          provisioner.playbook = "playbooks.yml"
          provisioner.extra_vars = "tests/test.yml" if File.file?("tests/test.yml")
          provisioner.verbose = "v"
      end
  end
end
