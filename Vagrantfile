# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'capitanh/basebox'
  config.vm.hostname = 'kinvm'
  config.vm.network "forwarded_port", host:9000,  guest:30777    # Portainer
  config.vm.network "forwarded_port", host:8080,  guest:80       # ArgoCD
  config.vm.network "forwarded_port", host:8443,  guest:443      # ArgoCD
  config.vm.network "forwarded_port", host:16443, guest:16443    # k8s API
  config.vm.network "forwarded_port", host:30003, guest:30003    # k8s API

  config.vm.provider "virtualbox" do |vb|
    vb.name = 'kinvm'
    vb.memory = 8192
    vb.cpus = 2
    vb.gui = false
  end
  #config.ssh.insert_key = false
  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = '2.0'
    ansible.playbook = 'site.yml'
    #ansible.verbose = "vvv"
    ansible.galaxy_role_file = 'requirements.yml'
    ansible.galaxy_roles_path = '~/.ansible/roles'
    ansible.galaxy_command = 'ansible-galaxy install --role-file %{role_file} --roles-path=%{roles_path} --force --ignore-certs --disable-gpg-verify'    
  end
end
