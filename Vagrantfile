Vagrant.configure(2) do |config|
    config.vm.define "vm" do
      config.vm.box = "debian/bullseye64"
      config.ssh.insert_key = false
      config.vm.network "public_network", ip: "192.168.124.141", :dev => "virbr0", :mode => "bridge", :type => "bridge"
  
      config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.galaxy_role_file = "requirements.yml"
        ansible.inventory_path = "inventories/test/inventory"
        ansible.playbook = "site.yml"
        ansible.become = true
      end
    end
  end
  
  