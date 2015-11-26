# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  # config.vm.box = "gsfjohnson/centos71-m"
  config.vm.box = "gsfjohnson/centos67"

  config.vm.define "tacplus" do |v|
    v.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    v.vm.hostname = "tacplus"
    v.vm.provision "shell", inline: <<-SHELL
      echo
      echo Use \\\'vagrant ssh\\\' to enter client environment and run:
      echo ansible-playbook -i inventory playbook.yml --diff
    SHELL

  end

  config.vm.box_check_update = true

  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provision "shell", inline: <<-SHELL
    echo Disable selinux... [setenforce 0]
    setenforce 0
    cp /vagrant/{*.yml,inventory} .
    cp -a /vagrant/group_vars .
    chmod a-x {*.yml,inventory}
    chown vagrant:vagrant {*.yml,inventory,group_vars}
    echo Install git and ansible w/ yum... [yum -q -y install ansible git yum-utils]
    yum -q -y install ansible git yum-utils
    echo Download ansible roles... [/vagrant/setup_roles.sh]
    /vagrant/setup_roles.sh
    if [ -e /vagrant/gitconfig ]; then
      cp -v /vagrant/gitconfig /home/vagrant/.gitconfig
      chown -v vagrant:vagrant /home/vagrant/.gitconfig
    fi
    if [ -e /vagrant/id_rsa ]; then
      cp -v /vagrant/id_rsa /home/vagrant/.ssh/id_rsa
      chmod -v 0600 /home/vagrant/.ssh/id_rsa
      chown -v vagrant:vagrant /home/vagrant/.ssh/id_rsa
    fi
  SHELL

end
