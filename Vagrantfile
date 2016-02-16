Vagrant.configure("2") do |config|

    config.vm.provider :virtualbox do |v|
        v.name = "php7"
        v.memory = 512
        v.cpus = 2
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--ioapic", "on"]
    end

    config.vm.box = "ubuntu/trusty64"
    config.ssh.insert_key = false

    config.vm.network :private_network, ip: "192.168.11.3"
    config.vm.network "forwarded_port", guest: 80, host: 8080

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/playbook.yml"
        ansible.inventory_path = "ansible/inventory"
        ansible.limit = 'all'
    end

    config.vm.synced_folder "./", "/vagrant", type: "nfs"
    config.vm.synced_folder ".", "/var/www/symfony3ansible", :owner=> 'www-data', :group=>'www-data', :mount_options => ['dmode=777', 'fmode=777']

end
