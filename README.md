# Ansible avec un LAB Docker

Apprendre, tester et se former sur Ansible en construisant un lab Docker.

## Le LAB Docker

Le LAB est composé de 3 conteneurs:

- Docker Ubuntu 20.04 avec Ansible
- Docker Ubuntu 20.04
- Docker Centos 7.9

## Mise en place du LAB:

Pour mettre en place ce tuto: https://github.com/adminimingo/ansible-lab-docker/

- Création des images
- Lancement des containers
- Création et injection des clés ssh RSA pour autoriser Ansible à se connecter sans mot de passe via SSH
- Ansible adhoc et playbook tests

Exemples de tests:

```bash
## TEST 1: adhoc dans Container Ansible
ssh -oStrictHostKeyChecking=no -oUserKnownHostsFile=/dev/null root@172.17.0.2
root@c77ea7487e4d:~#

ansible all -i 172.17.0.3,172.17.0.4, -m ping
172.17.0.3 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
172.17.0.4 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```

```bash
## TEST 2: adhoc avec docker run Ansible
sudo docker run -it --rm -e ANSIBLE_HOST_KEY_CHECKING=False -v `pwd`/ansible-rsa/id_rsa:/root/.ssh/id_rsa lab-ub2204-ansible:1.0 ansible all -i 172.17.0.3,172.17.0.4, -m ping
172.17.0.3 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
172.17.0.4 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```
