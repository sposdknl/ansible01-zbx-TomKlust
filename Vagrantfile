IMAGE_NAME = "bento/ubuntu-24.04"

Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  config.vm.define "bastion" do |bastion|
    bastion.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.name = "Bastion-ansible-2"
    end

    bastion.vm.box = IMAGE_NAME
    bastion.vm.hostname = "bastion"

    # Síť pro komunikaci se Zabbix Appliance
    bastion.vm.network "private_network", ip: "192.168.42.5", virtualbox__intnet: "intnet"

    # Sdílená složka projektu
    bastion.vm.synced_folder ".", "/opt/repo", type: "virtualbox"

    # 🔹 Shell provisioning pro instalaci Ansible
    bastion.vm.provision "shell", inline: <<-SHELL
      apt update
      apt install -y software-properties-common
      add-apt-repository --yes --update ppa:ansible/ansible
      apt install -y ansible
    SHELL

    # 🔹 Ansible provisioning (jen poté, co je Ansible nainstalovaný)
    bastion.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "/opt/repo/ansible_provision.yml"
      ansible.inventory_path = "/opt/repo/inventory.ini"
      ansible.install_mode = "default"
      ansible.verbose = "v"
    end
  end
end