# Logmanager
Logmanagement und Monitoringtool geschrieben in PHP

## Installation

1. Folgende Packete müssen installiert werden:
	- apache2
	- mysql-server
	- php5
	- php5-cli
	- php5-rrd
	- php5-mysql
	- libssh2-php
	- php5-snmp
	- php5-gd
	- nmap
	- arping

2. Entpacken und kopieren Sie den Logmanagerordner ins Apache Rootverzechnis.
   Meistens ist es das /var/www.
	2.1 Setzen Sie die Berechtigungen
		- Gehen Sie ins Apache Rootverzeichnis
		- sudo chmod -R 777 logmanagerV1.0

3. Begeben Sie sich ins Verzeichnis vom logmanagerV1.0

5. Aufsetzen der Mysql Datenbank
	5.1 Kopieren Sie den Befehl in die Kommandozeile und passen Sie die Parameter an.
		- echo "create database logmanager" | mysql -u  "<<USERNAME>>" -p
		- cat logmanager.sql | mysql -u <<USERNAME>> -p logmanager
		- Tragen Sie folgende Angaben im config/mysql_conf.php ein.
			- Host (default:localhost)
			- Benutzername
			- Passwort
			- Datenbank (default:logmanager)
6. Starten Sie den Apache neu.
	- sudo /etc/init.d/apache2 restart

7. Rufen Sie im Browser den Logmanager.
	7.1 Login
		- Benutzernamen: loguser
		- Passwort: passi123

Herzlichen Glückwunsch Sie haben den LogmanagerV1.0 erfolgreich installiert.

## SYSLOG-NG Konfiguration

1. Starten Sie das folgende Script: sudo bash configure_syslog-ng.sh
2. Befolgen Sie die Anweisungen des Script outputs.

## Extras

1. Kopieren Sie auf einem Ziel System "get_data.sh" ins /usr/bin
2. chmod 755 /usr/bin/get_data.sh
3. Kopieren Sie folgende Linie ins /etc/snmp/snmpd.conf
	exec echotest /usr/bin/get_data.sh
4. Install sudo apt-get install lm-sensors
5. Folgendes Kommando ausfuehren un alle mit YES beantworten
	sensors-detect
6. Install sudo apt-get install acpi
7. Starten Sie den SNMP Daemon neu.
	sudo /etc/init.d/snmpd restart

# Lizenz
Alle Rechte sind dem Eigentümer Simon Kaspar vorbehalten.
Diese Software darf nicht für kommerzielle Zwecke gebraucht werden.
Das Vertreiben oder Verkaufen der Software ist dem Eigentümer vorbehalten.

Siehe license.txt
