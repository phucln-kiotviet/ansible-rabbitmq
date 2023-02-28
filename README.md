# Ansible and rabbitMQ

- My first practice on ansible to install rabbitMQ


## Add user
- With user/pass:

```sh
ansible-playbook -vvv -i inventory.yml playbook.yml --user ubuntu --extra-vars "ansible_sudo_pass=12345678"

# OR WITHOUT log
ansible-playbook -i inventory.yml playbook.yml --user ubuntu --extra-vars "ansible_sudo_pass=12345678"
```


## Run rabbitMQ cluster
```sh
ansible-playbook -i inventory.yml playbook-install-rabbitmq.yml --user ubuntu --extra-vars "ansible_sudo_pass=12345678"
```
