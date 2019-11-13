Add ip’s of cluster nodes to /etc/ansible/hosts or use 

`ansible_playbook -i %proj_path%/.vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory -b`

```c
[elastic]
192.168.60.10
192.168.60.11
192.168.60.12

[elastic:vars]
ansible_ssh_user=vagrant
ansible_ssh_private_key_file=~/.vagrant.d/insecure_private_key
```

Then go to cloned repo and run `​ vagrant up `

`​`​vagrant will use parallels provider so if you need another, then change provier and box in Vagrantfile.

Vagrant will up 2 centos 7 nodes and provision them with ansible playbook

Check cluster state

```c
curl -X GET http://192.168.60.10/_cluster/health
```

Check logs

```c
ssh -i ~/.vagrant.d/insecure_private_key vagrant@192.168.60.10
tail -f /var/log/elasticsearch/el-cluster.log
```
