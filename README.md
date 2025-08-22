# Projeto Interdisciplinar 2° período

No segundo período, configurei um servidor do zero utilizando máquinas virtuais (sistema operacional Linux, especificamente o Debian sem interface gráfica). Como os arquivos das máquinas virtuais são grandes, o acesso a eles está disponível em um drive. Coloquei apenas os nomes das pastas, caminhos e arquivos que foram acessados para configurar o servidor. Este documento não é um tutorial.

A Aimirim foi a empresa que visitei com meu grupo e, portanto, a escolhida para servir de inspiração na criação desse projeto de redes. Por isso, o site e alguns arquivos estão configurados com o nome da empresa.

## Para configuração de hostname e IP

- nano /etc/hostname (utilizado para alterar o nome do servidor)
- nano /etc/default/grub
- nano /etc/network/interfaces (configuração do IP)

## Para o SSH (conexão remota)

- nano -l /etc/ssh/sshd_config

## Para configuração do DHCP

- Os 2 primeiros IPs são dos servidores e foram reservados os 10 primeiros IPs da rede. A faixa de distribuição está entre 10 e 100.
- nano /etc/default/isc-dhcp-server
- cd /etc/dhcp
- nano -l dhcpd.conf

## Para o DNS

- cd /etc/bind
- nano named.conf.local
- nano db.aimirim
- nano db.192
- nano /etc/rc.local (utilizei `chmod 755 /etc/rc.local` para dar as devidas permissões, para que o arquivo seja executado com `./rc.local`)

## Para configurar o site utilizei o servidor Apache

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
- smbclient -L localhost -U administrator (login com o admin do Samba para verificar o funcionamento)
- Após isso, foi utilizado o Windows 11 para acessar o Active Directory instalado no Linux.
- Configurei o DNS no Windows 11.

## Caminho onde os bancos de dados criados no MySQL dentro do Debian ficam disponíveis

- /var/lib/mysql

## Para o PHP

- nano -l /etc/php/8.2/apache2/php.ini

## Para o Gateway (NAT)

- nano rc.local

## Para o firewall

- nano /usr/local/bin/firewall.sh start `(para ativar o firewall)`
- nano /usr/local/bin/firewall.sh stop `(para desativar o firewall)`
- nano /usr/local/bin/firewall.sh restart `(para reiniciar o firewall)`
- nano /usr/local/bin/firewall.sh `(para acessar o script do firewall)`
