# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "web" do |web|
    web.vm.box = "centos7"
    web.vm.network "private_network", type: "dhcp"
    web.vm.hostname = "vagrant-web"
  end

  config.vm.define "db" do |db|
    db.vm.box = "centos7"
    db.vm.network "private_network", type: "dhcp"
    db.vm.hostname = "vagrant-db"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.groups = {
      "web_servers" => "web",
      "db_servers" => "db"
    }
  end

end
