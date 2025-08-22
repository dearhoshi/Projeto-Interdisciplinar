# Projeto Interdisciplinar 2° período

No segundo período configurei um servidor do zero, utilizando máquinas virtuais (utilizei sistema operacional linux, mais especificadamente o debian e sem interface gráfica). Os arquivos de máquinas virtuais são grandes e por isso o acesso a eles estão no drive. Aqui irei deixar apenas nomes das pastas, caminhos e arquivos que foram acessados para configurar o servidor e fazer com que ele funcione. Isso não é um tutorial.

A Aimirim foi empresa que visitei junto com meu grupo, portanto foi a escolhida para servir de inspiração na criação desse projeto de redes. Por isso, o site e alguns aquivos estão configurados com o nome da empresa.

## Para configuração de hostname e IP

- nano /etc/hostname (utilizei para alterar o nome do servidor)
- nano /etc/default/grub
- nano /etc/network/interfaces (configuração do ip)

## Para o SSH (conexão remota)

- nano -l /etc/ssh/sshd_config

## Para configuração do DHCP 

- 2 primeiros ip's são dos servidores e foram reservados os 10 primeiros ip's da rede. A faixa de distribuição está entre 10-100.
- nano /etc/default/isc-dhcp-server
- cd /etc/dhcp
- nano -l dhcpd.conf

## Para o DNS

- cd /etc/bind
- nano named.conf.local
- nano db.aimirim
- nano db.192
- nano /etc/rc.local (usei chmod 755 /etc/rc.local para dar as devidas permissões, para que assim o arquivo seja executado com ./rc.local)

## Para configurar o site utilizei o servidor apache

- cd /var/www
- cd aimirim/public_html
- nano index.html
- nano aimirim.conf

## Para o acesso via FTP

- nano /etc/passwd
- nano -l /etc/vsftpd.conf
- nano /etc/liberado

## Para controlador de domínio foi utilizado o Samba

- samba-tool domain provision
- smbclient -L localhost -U administrator (logando com admin do samba para verficar se está funcionando)
- após isso foi utilizado o windows 11 para acessar o AD que foi instalado no linux
- configurei o DNS no windows 11

## caminho onde os bancos de dados criados no MySQL dentro do Debian ficam disponíveis

- /var/lib/mysql

## Para o PHP

- nano -l /etc/php/8.2/apache2/php.ini

## Para o Gateway (NAT)

- nano rc.local
