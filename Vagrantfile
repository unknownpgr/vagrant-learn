Vagrant.configure("2") do |config|

  # Virtual machine image
  config.vm.box = "ubuntu/focal64"

  # Use bridge mode.
  config.vm.network "public_network", ip: "172.30.1.100"

  # Disable project root folder mounting
  config.vm.synced_folder '.', '/vagrant', disabled: true

  # Set RAM size to 2GB and set 2 cpus
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  # Set default gateway
  config.vm.provision "shell",
    run: "always",
    inline: "ip route add default via 172.30.1.1"

  # Enable ssh via password
  config.vm.provision "shell",
    inline: "sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config;systemctl restart sshd.service"

  # Enable ssh via password
  config.vm.provision "shell",
    inline: "echo 'vagrant:key-for-vagrant-test' | sudo chpasswd"

end
