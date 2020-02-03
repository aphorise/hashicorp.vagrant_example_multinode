# hashicorp.vagrant-multinode
This is a simple demo of a multi node [Vagrant](https://github.com/hashicorp/vagrant) setup running locally using an [Ubuntu http-server](https://app.vagrantup.com/aphorise/boxes/ubuntu16-nginx) image from [vagrantcloud](https://app.vagrantup.com/boxes/search); server instances are expected to **port-forwarded** to your local host on the ranges of **58081..N**

```
vagrant up ; # or 'vagrant reload' when adjusting Vagrantfile.

vagrant global-status ; should show running nodes
# id       name   provider   state   directory
# --------------------------------------------------------------------------------
# 4ca664a  nginx1 virtualbox running /home/auser/hashicorp.vagrant_multinode
# 1434b42  nginx2 virtualbox running /home/auser/hashicorp.vagrant_multinode

vagrant port nginx1 ; # to see ports forwarded.

curl -v 127.0.0.1:58081 ; # check node1 with headers
curl -v 127.0.0.1:58082 ; # check node2 with headers
# ... should output default NGiNX home page.

# when done:
vagrant destroy nginx1 nginx2 ; # ... destroy al
vagrant box aphorise/ubuntu16-nginx ; # ... deleting vbox images
```

Documentation may be found at [the following link & tips section](https://www.vagrantup.com/docs/vagrantfile/tips.html).


**SETUP NOTE**: Newly setup & first time executors should consider setting the environment variable defining default providers - else the download images may occure.
```
VAGRANT_DEFAULT_PROVIDER='virtualbox' ;
# good to set global / export else no default image may be attempted.
```
