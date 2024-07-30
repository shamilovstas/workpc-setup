Vagrant.configure("2") do |config|
  config.vm.box = "generic/fedora37"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.host_name = "testmachine"
  config.vm.network :private_network, ip: "192.168.56.10"

  config.vm.provision "shell", inline: <<-SHELL
    nmcli conn modify 'Wired connection 1' ipv4.addresses $(cat /etc/sysconfig/network-scripts/ifcfg-eth1 | grep IPADDR | cut -d "=" -f2)/24
    nmcli conn modify 'Wired connection 1' ipv4.method manual
    systemctl restart NetworkManager
  SHELL
end