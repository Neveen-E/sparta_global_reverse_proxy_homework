# Install required plugins
required_plugins = ["vagrant-hostsupdater"]
required_plugins.each do |plugin|
    exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure("2") do |config|

    config.vm.define :main do |main|
    main.vm.box = "ubuntu/xenial64"
    main.vm.network "private_network", ip: "192.168.10.100"
    main.hostsupdater.aliases = ["development.main"]
    main.vm.synced_folder ".", "/home/ubuntu/app"
  end

    config.vm.define :proxy do |proxy|
    proxy.vm.box = "ubuntu/xenial64"
    proxy.vm.network "private_network", ip: "192.168.10.101"
    proxy.hostsupdater.aliases = ["development.proxy"]
    end
  config.vm.provision "shell", path: "provision.sh", privileged: false
end
