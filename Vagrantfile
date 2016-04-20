# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.6.0"
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "node" do |node|
    node.vm.hostname = "ansible-test"
    node.vm.box = "ubuntu/trusty64"
    node.vm.network "forwarded_port", guest: 80, host: 8888
    node.vm.provision "ansible" do |ansible|
      ansible.playbook = 'site.yml'
      ansible.extra_vars = "vagrant/group_vars/all/all"
      ansible.groups = {
        "web_servers" => ["node"],
        "nodejs_servers" => ["node"]
      }
    end
  end
end
