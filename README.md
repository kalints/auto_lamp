# LAMP for yii2 using SaltStack

## Connect minion

This way you can connect minion to the master running on localhost.

```
echo 'master: 127.0.0.1' >> /etc/salt/minion
systemctl restart salt-minion.service
sudo salt-key -A -y
sudo salt '*' test.ping
```

## Install package by applying configuration file from the master to all minions

```
sudo ln -s /vagrant/saltstack/srv /srv/salt
sudo cp -r /vagrant/saltstack/etc_salt/* /etc/salt/
sudo salt '*' state.apply mydev
```

## Ideas for how to build DO instances and configure them

https://www.digitalocean.com/community/tutorials/saltstack-infrastructure-configuring-salt-cloud-to-spin-up-digitalocean-resources