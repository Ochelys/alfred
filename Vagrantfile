# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = 'alfred.dev'

  config.vm.box = 'phusion/ubuntu-14.04-amd64'
  config.vm.network 'private_network', ip: '192.168.3.10'

  config.vm.network "forwarded_port", guest: 443, host: 10443

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'site.yml'
    ansible.sudo = true
  end
end
