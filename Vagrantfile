require 'dotenv'
Dotenv.load

VM_COUNT   = ENV['VM_COUNT'].to_i
VM_BOX     = ENV['VM_BOX']
VM_RAM     = ENV['VM_RAM']
VM_CPU     = ENV['VM_CPU'].to_i
VM_PREFIX  = ENV['VM_PREFIX']
VM_BASE_IP = ENV['VM_BASE_IP']

Vagrant.configure("2") do |config|
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  config.hostmanager.include_offline = true

  (1..VM_COUNT).each do |i|
    hostname = "#{VM_PREFIX}#{i}"
    ip = "#{VM_BASE_IP}.#{10 + i}"

    config.vm.define hostname do |vm|
      vm.vm.box = VM_BOX
      vm.vm.hostname = hostname
      vm.vm.network "private_network", ip: ip

      vm.vm.provider "virtualbox" do |vb|
        vb.memory = VM_RAM
        vb.cpus = VM_CPU
      end

      vm.vm.provision "shell", path: "provision.sh"
    end
  end
end
