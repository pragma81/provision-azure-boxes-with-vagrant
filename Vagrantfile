# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box     = 'azure-example'
   config.vm.box_url = 'https://github.com/msopentech/vagrant-azure/raw/master/dummy.box'
    config.vm.network :forwarded_port, guest: 8090, host: 8090
    config.ssh.pty = true

  config.ssh.username = 'vagrant'
 #sconfig.ssh.password = 'changeme1'    
  
 config.ssh.private_key_path = File.expand_path('../ssh/azurevagrant.pem')

    config.vm.provider :azure do |azure,override|
    override.vm.synced_folder ".", "/vagrant", disabled: true
    azure.mgmt_certificate = File.expand_path('../ssh/azurevagrant.pem')
    azure.mgmt_endpoint = 'https://management.core.windows.net'
    azure.subscription_id = 'a64131a4-b176-4a76-8c51-59671e176d86'

      azure.cloud_service_name = 'VagrantProvisionedService'
      azure.storage_acct_name  = 'vagrantstorage'
      azure.deployment_name    = 'VagrantProvisionedDeployment'

    azure.vm_name     = 'azure-vagrant-centos'
    azure.vm_image    = '5112500ae3b842c8b9c604889f8753c3__OpenLogic-CentOS-71-20150410'
    azure.vm_size     = 'Large'
      azure.vm_location = 'West Europe'

    azure.ssh_port             = '22'
    azure.ssh_private_key_file = File.expand_path('../ssh/azurevagrant.pem')
    azure.ssh_certificate_file = File.expand_path('../ssh/azurevagrant.pem')

    azure.tcp_endpoints = '8090:8090'
  end
  
    
   # config.vm.provision 'shell', inline: 'echo OHAI'
   
   
   # Currently vagrant is not able to automaticcally install docker on centos. 
   # So before the docker provisioner I must use a shell provisioner to:
   # 1) Check Docker already installed
   # 2) If not install docker doe centos following this guide https://docs.docker.com/installation/centos/
   
    config.vm.provision 'docker' do |docker|
       docker.run "atlassian-confluence", image: "cptactionhank/atlassian-confluence:latest", args: "-d -v /usr/local/atlassian/confluence -p 8090:8090"
    end
    
end
