Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp-education/ubuntu-24-04"
  config.vm.box_version = "0.1.0"

  config.vm.hostname = "match-vm"
  config.vm.network "private_network", ip: "192.168.56.10"

  config.vm.provision "shell", inline: <<-SHELL
    if ! command -v ansible >/dev/null 2>&1; then
      echo "Ansible not found, installing..."
      sudo apt-get update
      sudo apt-get install -y software-properties-common
      sudo apt-add-repository --yes --update ppa:ansible/ansible
      sudo apt-get install -y ansible
    else
      echo "Ansible is already installed."
    fi
  SHELL

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "/vagrant/playbook.yml"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.name = "UNIR Match VM"
    vb.memory = "1024"
    vb.cpus = 1
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
end
