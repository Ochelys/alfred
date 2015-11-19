# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = 'alfred.dev'

  config.vm.box = 'ubuntu/trusty64'
  config.vm.network 'private_network', ip: '192.168.3.10'

  config.vm.network "forwarded_port", guest: 443, host: 10443

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'playbook.yml'
    ansible.sudo = true
  end

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end
end
