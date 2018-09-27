# LAMP for yii2 using SaltStack

## Connect minion

This way you can connect minion to the master running on localhost.

```
sudo salt '*' test.ping
```

## Install package by applying configuration file from the master to all minions

```
sudo salt '*' state.apply mydev
```

## Ideas for how to build DO instances and configure them

https://www.digitalocean.com/community/tutorials/saltstack-infrastructure-configuring-salt-cloud-to-spin-up-digitalocean-resources

## Great Vagrant example:

https://github.com/UtahDave/salt-vagrant-demo/blob/master/Vagrantfile