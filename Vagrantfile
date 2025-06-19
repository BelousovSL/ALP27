ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'
Vagrant.configure(2) do |config|

    
   config.vm.provision "ansible" do |ansible|
      ansible.playbook = "prov.yml"
      ansible.inventory_path = "hosts"
      ansible.host_key_checking = "false"
      ansible.limit = "all"
   end
  
   config.vm.define "DynamicWeb" do |vmconfig| 
      vmconfig.vm.box = 'bento/ubuntu-24.04'
      vmconfig.vm.hostname = 'DynamicWeb'
      vmconfig.vm.network :forwarded_port, host: 2901, guest: 22    
      vmconfig.vm.network "forwarded_port", guest: 9083, host: 9083
      vmconfig.vm.network "forwarded_port", guest: 9081, host: 9081
      vmconfig.vm.network "forwarded_port", guest: 9082, host: 9082
      vmconfig.vm.provider "virtualbox" do |vbx|
         vbx.memory = "2048"
         vbx.cpus = "2"
         vbx.customize ["modifyvm", :id, '--audio', 'none']
      end
   end  
end
