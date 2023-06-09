1. Dodać instancje <instancja> do inventory/hosts
2. Dodać plik <instancja>.yml do host_vars z specyfikacją instancji
3. Odpalić ansible komendą: ansible-playbook 1-pg-add-instance.yml --inventory inventory --limit <instancja> --ask-vault-password



TO-DO:
e)	Kernel resources – ustawiamy zgodnie ze skryptem:
#!/bin/bash
# simple shmsetup script
page_size=`getconf PAGE_SIZE`
phys_pages=`getconf _PHYS_PAGES`
shmall=`expr $phys_pages / 2`
shmmax=`expr $shmall \* $page_size`
echo kernel.shmmax = $shmmax
echo kernel.shmall = $shmall


i wpisujemy:
kernel.shmmax = wynik skryptu
kernel.shmall = wynik skryptu
fs.aio-max-nr = 1048576
fs.file-max = 6815744
kernel.shmmni = 4096
kernel.sem = 250 32000 100 128
net.ipv4.ip_local_port_range = 9000 65500
net.core.rmem_default = 262144
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
net.core.wmem_max = 1048576
vm.swappiness = 1

wyniki do /etc/sysctl.conf i wykonujemy:
		    sysctl -p

yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install libzstd-devel
