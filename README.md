<img src = "centosLogo.png"><br>
# Boschetto Pedro Henrique - CentOS 7
Macchina virtuale - Installazione Servizi

## Servizi
La macchina virtuale CentOS 7 deve essere stata installata e configurata con:
- Connessione di rete.
- Utente con privilegi amministrativi.

Installazione dei servizi:
- SSH
- HTTP
- MariaDB
- PHP
- phpMyAdmin
- FTP


### Servizio SSH
##### Eseguire le seguenti righe di codice:
`/etc/ssh/sshd_config`<br/>

`yum install sshd`<br/>
  
`systemctl start sshd`<br/>
  
`systemctl enable sshd`<br/><br/>

Questi comandi sono responsabili di installare, avviare e mantenere sempre attivo il servizio.
  
<img src = "ssh.png"><br>

##### Impostazioni di sicurezza
A questo punto impediremo l'accesso da remoto all'utente root della macchina virtuale utilizzando il comando:

`PermitRootLogin no`

<img src = "ssh2.png"><br>

Per rendere effettive le modifiche riavviare il servizio con `systemctl restart sshd`<br/>
<img src = "ssh3.png"><br>

### Servizio HTTP
##### Eseguire le seguenti righe di codice:
`yum install httpd`<br/>

`systemctl start httpd`<br/>

`systemctl enable httpd`<br/><br/>

Questi comandi sono responsabili di installare, avviare e mantenere sempre attivo il servizio.

<img src = "HTTP.png"><br>

**DocumentRoot** di Apache:
`/var/www/html`<br/>

Configurazione delfirewall:<br/>

`firewall-cmd --permanent --add-port=80/tcp`<br/>
`firewall-cmd --reload`<br/><br/>
  
<img src = "HTTP2.png"><br>

<img src = "HTTP3.png"><br>
