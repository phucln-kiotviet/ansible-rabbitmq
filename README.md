# Ansible and rabbitMQ

- My first practice on ansible to install rabbitMQ


## Add user
- With user/pass:

```sh
ansible-playbook -vvv -i inventory.yml playbook.yml --user ubuntu --extra-vars "ansible_sudo_pass=12345678"

# OR WITHOUT log
ansible-playbook -i inventory.yml playbook.yml --user ubuntu --extra-vars "ansible_sudo_pass=12345678"

ansible-playbook -i inventory.yml playbook.yml --user root
```


## Run rabbitMQ cluster
```sh
ansible-playbook -i inventory.yml playbook-install-rabbitmq.yml --user root
```


## install vault

```sh
ansible-playbook -vv --user ubuntu --extra-vars "ansible_sudo_pass=12345678" -i inventy-vault.yml playbook-install-vault.yml 
```


- start Vault with docker:

```sh
docker run --cap-add=IPC_LOCK -d --name=dev-vault vault

# docker logs dev-vault 
# to check unseal key and root token
### Unseal Key: aOTUj5jTSlFkeq9keG67bmnoQO0WSkGjhslJivzGkq0=
### Root Token: hvs.qmV0t5bbFzOKIVfevVVqpjej

# docker inspect to check IP of vault
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' dev-vault
```

- Set up vault: 

```sh
   export VAULT_TOKEN='hvs.LIMy21YutkreP3CMuuP1Xj9c'
   export VAULT_ADDR='http://172.17.0.2:8200/'
``` 