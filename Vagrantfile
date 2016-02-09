Vagrant.configure("2") do |config|

    config.vm.provider :virtualbox do |v|
        v.name = "php7"
        v.customize [
            "modifyvm", :id,
            "--name", "php7",
            "--memory", 512,
            "--natdnshostresolver1", "on",
            "--cpus", 2,
        ]
    end

    config.vm.box = "ubuntu/trusty64"

    config.vm.network :private_network, ip: "192.168.11.2"
    config.vm.network "forwarded_port", guest: 80, host: 8080
    config.ssh.forward_agent = true

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/playbook.yml"
        ansible.inventory_path = "ansible/inventories/dev"
        ansible.limit = 'all'
    end

    config.vm.synced_folder "./", "/vagrant", type: "nfs"
    config.vm.synced_folder "/var/www/restabox", "/var/www/restabox", :owner=> 'www-data', :group=>'www-data', :mount_options => ['dmode=777', 'fmode=777']

end
