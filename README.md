TACACS+
=======

TACACS+ daemon from the Shrubbry Networks project, based on Cisco tac_plus reference implementation.  Config managed by Ansible.


Setup Steps
===========

1. Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
1. Install [Vagrant](http://www.vagrantup.com/downloads.html)
1. (if not already done) Add your public key to account settings on github.com
1. Clone this repo
  `git clone git@github.com:gsfjohnson/vagrant-tac_plus.git`
1. Change directory to cloned repo
  `cd vagrant-tac_plus`
1.  Start the environment
  `vagrant up`
1. Enter the environment / make changes
  `vagrant ssh`
1. Send patches or pull requests!

