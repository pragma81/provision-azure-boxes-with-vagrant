# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box     = 'azure-example'
  config.vm.box_url = 'https://github.com/msopentech/vagrant-azure/raw/master/dummy.box'

  config.ssh.username         = 'vagrant'
    config.ssh.private_key_path = File.expand_path('../ssh/azurevagrant.pem')

  config.vm.provider :azure do |azure|
      azure.mgmt_certificate = File.expand_path('../ssh/azurevagrant.pem')
    azure.mgmt_endpoint = 'https://management.core.windows.net'
    azure.subscription_id = 'a64131a4-b176-4a76-8c51-59671e176d86'

    azure.cloud_service_name = 'WallgreensRx'
    azure.storage_acct_name  = 'wallgreensrx'
    azure.deployment_name    = 'WallgreensRx'

    azure.vm_name     = 'azurevagrantcentos'
    azure.vm_image    = '5112500ae3b842c8b9c604889f8753c3__OpenLogic-CentOS-71-20150410'
    azure.vm_size     = 'Large'
      azure.vm_location = 'West Europe'

    azure.ssh_port             = '22'
      azure.ssh_private_key_file = File.expand_path('../ssh/azurevagrant.pem')
    azure.ssh_certificate_file = File.expand_path('../ssh/azurevagrant.cer')

    azure.tcp_endpoints = '8000'
  end

  config.vm.provision 'shell', inline: 'echo OHAI'
end
