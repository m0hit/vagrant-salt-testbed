Easy testing with Salt and Reimann
==================================

References
----------

* [Salt](http://docs.saltstack.com/index.html)
* [Vagrant](http://docs.vagrantup.com/v2/)
* [Salty-Vagrant](https://github.com/saltstack/salty-vagrant)

Setup
-----

* Install [vagrant](http://downloads.vagrantup.com/)

* Add a vagrant base box called `base` or edit the `Vagrantfile`

* Install Salty Vagrant
```
vagrant plugin install vagrant-salt
```

* Clone this repo if you're reading this on github

* Add your salt repo. 
```
git submodule add <git@git/salt> salt/roots
```

* For sanity make sure to be working on a branch of your salt repo

* Change config in Vagrantfile as required

  - In accordance to top.sls change config.vm.hostname
  - Change salt.run_highstate 

* `vagrant up`

Specific Scenarios
==================

Testing new states
------------------

- Run vagrant ssh to ssh into the vm. cd /srv/salt and you can start running your state file, e.g.
`salt-call --local state.sls apps.my-awesome-new-app`

Testing a target (see top.sls)
------------------------------

- `vagrant destroy`
- Change `config.vm.hostname` in the `Vagrantfile` to something that matches your target. eg. `logging1.example.com`
- `vagrant up`
