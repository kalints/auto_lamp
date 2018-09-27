# LAMP for yii2 using SaltStack

## Apply SLS defined state

```
sudo salt '*' test.ping
sudo salt '*' state.apply mydev
```

## Ideas for how to build DO instances and configure them

https://www.digitalocean.com/community/tutorials/saltstack-infrastructure-configuring-salt-cloud-to-spin-up-digitalocean-resources

## Great Vagrant example:

https://github.com/UtahDave/salt-vagrant-demo/blob/master/Vagrantfile