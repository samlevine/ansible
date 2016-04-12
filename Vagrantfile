# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.6.0"
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.hostname = "ansible-test"

  # Always use Vagrant's default insecure key
  #config.ssh.insert_key = false

  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 80, host: 8888
  #config.vm.network "forwarded_port", guest: 3000, host: 3030

  #config.vm.provision "shell",
  #  inline: "sudo apt-get update"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = 'site.yml'
    ansible.extra_vars = "vagrant/group_vars/all/all"
    ansible.groups = {
      "web_servers" => ["default"],
      "nodejs_servers" => ["default"]
    }
  end
end
