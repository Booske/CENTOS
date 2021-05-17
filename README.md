<img src = "logoCentos.png"><br>
# Boschetto Pedro Henrique - CentOS LAMPP


## Macchina virtuale - Installazione Servizi
La macchina virtuale CentOS 7 deve essere stata installata e configurata con:
- Connessione di rete.
- Utente con privilegi amministrativi.

Installazione dei servizi:
- SSH
- HTTP
- MariaDB
- PHP
- phpMyAdmin


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


### Servizio MariaDB
Installazione del servizio (`mariadb-server`) e del client CLI (`mariadb`)

`yum install mariadb-server mariadb`<br/>
`systemctl start mariadb`<br/>
`systemctl enable mariadb`<br/>
`mysql_secure_installation`<br/><br/>

<img src = "MariaDB.png"><br>
<img src = "MariaDB2.png"><br>

### Servizio PHP
Installazione della versione default di PHP
`yum install php`<br/>
`systemctl restart httpd`<br/>
`php -v`<br/>

<img src = "php.png"><br>
Per verificare il funzionamento del servizio PHP appena installato seguire il seguente procedimento:
Eseguire il comando
`info.php`, nella **DocumentRoot**<br/>

<img src = "php2.png"><br>

Andare su un qualsiasi browser da host remoto e inserire il seguente link:
`http://<ip_macchina_virtuale>/info.php`<br/><br/>


### Servizio phpMyAdmin
##### File di configurazione del servizio
`/etc/httpd/conf.d/phpMyAdmin.conf`<br/><br/>

Repo aggiuntivo: `EPEL repo` <br/>

`yum install epel-release`<br/><br/>

<img src = "phpA.png"><br>

Installazione phpMyAdmin:<br/>

`yum install phpmyadmin`<br/><br/>

<img src = "phpA2.png"><br>
Con un qualsiasi browser verificare il funzionamento del servizio.<br/>
`http://<ip_macchina_virtuale>/phpmyadmin` e accedere con le credenziali dell'utente root.<br/>

<img src = "PHPA4.png"><br>
