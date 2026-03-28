[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/EruK4M2B)
# Zabbix agent a Ansible

Repository pro vyuku na SPOS DK

## První kroky s Ansible a Zabbix agent2

![Zabbix & Ansible](./images/zbx7-ansible.png)

- Zabbix enterprise-class open source distributed monitoring solution - [Zabbix Appliance](https://www.zabbix.com/documentation/7.0/en/manual/appliance)
- Vagrant utility for managing virtual machines - [Vagrant](https://developer.hashicorp.com/vagrant)
- Vagrant box from [bento](https://github.com/chef/bento) - [bento/ubuntu-24.04](https://portal.cloud.hashicorp.com/vagrant/discover/bento/ubuntu-24.04)
- Red Hat Ansible Automation Platform - [Ansible](https://www.redhat.com/en/technologies/management/ansible)
- Linux Ubuntu distribution - [Ubuntu server](https://ubuntu.com/server)
- AlmaLinux distribution - [AlmaLinux OS](https://almalinux.org)

## Example

```console
vagrant up
vagrant ssh
sudo su -
cd /opt/repo/
ansible-playbook -i inventory.ini -l bastion configure_servers.yml
```

# Požadované známkované úkoly

- Zprovozněte si Zabbix Appliance a nastavte druhou síťovou kartu viz /etc/sysconfig/network-scripts/ifcfg-eth1 v AlmaLinux
- Upravte URL Vašeho Github Classroom projektu v souboru ansible_provision.yml v Tasku "Cloning Git repository" pro klonování do VM  Bastion-ansible
- Upravte Ansible playbook pro instalaci Zabbix agenta pro instalaci druhé generace Zabbix Agent2 ve verzi 7.0 LTS
- Upravte Ansible playbook pro instalaci Zabbix agenta, nastavte direktivu HostMetadata ( [dokumetace community.zabbix](https://galaxy.ansible.com/ui/repo/published/community/zabbix/docs/ZABBIX_AGENT_ROLE/) )
- Provedené změny aktualizujte v ve Vašem git repository (git add; git commit -m "zmeny"; git push)
- V Zabbix Appliance vytvoř auto-registrační pravidlo v akcích s HostMetadata a dolož sceenem obrazovky
- Nastartuj připravenou VM Bastion-ansible pomoci Vagrant up - upravte dle svého nastavení síť pro propojení se Zabbix Appliance
- Přihlaš se do VM Bastion-ansible a spusť ansible playbook v adresáři /opt/repo pro instalaci a konfiguraci Zabbix agenta viz example
- Vytvoř složku screenshots a config ve svém projektu
- Do adresáře screenshots udělej snímky s nazvy souboru dokazující pruběh své prace, ansible log, zabbix auto-registrační pravidlo, a registrovaného hosta + průběh funkčního monitorování VM Bastion atd.
- Do adresáře config vykopiruj konfigurační soubor agenta /etc/zabbix/zabbix_agent2.conf který sestavil Ansible

...
