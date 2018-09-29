# LAMP for yii2 using SaltStack

## Docs

### Bootstrap a new master/minion node

- Master

```
curl -L https://bootstrap.saltstack.com | bash -s -- -M
```

- Minion

```
curl -L https://bootstrap.saltstack.com | bash
```

### Configure master/minion node

- Install both master and minion
- Configure minion to use localhost master by adding 'master: 127.0.0.1' to /etc/salt/minion
- Accept key using 'salt-key -A' and restart master and minion using systemd
- Populate /srv with the /srv/pillar and /srv/salt content from the repo.
- Update /srv/salt/top.sls with the server name
- salt '*' state.highstate

### Apply SLS defined state

```
sudo su -
salt '*' test.ping
salt '*' state.highstate
```

### How to rotate keys

#### Stop master and minions via systemd

- On master:

```
systemctl stop salt-master
```

- On minions:

```
systemctl stop salt-minion
```

#### Use salt-key to generate new keys in a temp (current) directory

```
salt-key --gen-keys master
salt-key --gen-keys minion1
salt-key --gen-keys minion2
```

#### Update all files in /etc/salt/pki

Notice that for master you have directory called "master" and for minions a directory called "minion".
You need to update in /etc/salt/pki/master only with the two master keys - master.pem and master.pub.
For the minions you need to update /etc/salt/pki/minion/minion_master.pub with the master.pub content
and then update the minion.pem and minion.pub with the content for each node. Each minion should have
its own unique key pair.

#### Start salt-master on the master node

```
systemctl start salt-master
```

#### Start salt-minion on each minion node

```
systemctl start salt-minion
```

#### On the master node accept the new minion keys

```
salt-key -A
```

#### Test communication from the master node

```
salt '*' test.ping
```

## External

### Ideas for how to build DO instances and configure them

https://www.digitalocean.com/community/tutorials/saltstack-infrastructure-configuring-salt-cloud-to-spin-up-digitalocean-resources

### Great Vagrant example that I used to base on:

https://github.com/UtahDave/salt-vagrant-demo/blob/master/Vagrantfile