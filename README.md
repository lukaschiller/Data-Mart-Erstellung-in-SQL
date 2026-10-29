# Beschreibung des Projekts
Die zur Verfügung gestellte SQL-Datenbank bildet die Grundlage für eine Büchertausch-App für lokale Gemeinschaften. Die Datenbank enthält 34 über Fremdschlüssel miteinander verbundene Tabellen in der dritten Normalform sowie insgesamt 291 künstliche Testdatensätze. Die Datenbank enthält Constraints, Ereignisse und Trigger, um mögliche Fehler in Datenformaten und manuellen Abläufen zu vermeiden. Indizes und Archivierungskonzepte wurden zur Erhöhung die Effizienz implementiert.
Die Umsetzung ist mit dem auf SQL-basierenden Datenbankmanagementsystem MariaDB erfolgt, welches alle benötigten Funktionalitäten wie Trigger, Ereignisse und Indizes unterstützt. Dazu wurde die Oberfläche phpMyAdmin genutzt.

# Installationsanleitung
In der folgenden Installationsanleitung werden die Installation und Einrichtung von XAMPP und phpMyAdmin sowie der Import der Datenbank behandelt.

## Systemvoraussetzungen
XAMPP ist für Linux, Windows und als Web-Anwendung für Chrome-basierte Browser verfügbar. Bei Windows werden die Versionen 2008, 2012, Vista, 7, 8, 10 und 11 unterstützt. Die Web-Anwendung kann durch Sicherheitskonfigurationen des Browsers blockiert sein.

## Installation
Sollten während der Installation Probleme auftreten, sind auf der offiziellen Website von XAMPP FAQs verfügbar.

### XAMPP
Die Windows-Installation kann über einen auf der Webseite https://www.apachefriends.org/download.html zur Verfügung gestellten Installer erfolgen. Während der Installation können falsch-positive Warnungsmeldungen durch Anti-Viren-Programme generiert werden. Für das Testen der bereitgestellten Datenbank können die Stan-dardeinstellungen bei der Installation unverändert übernommen werden.
Nach der Installation sollte das XAMPP-Control-Panel als Admin ausgeführt werden. In der Zeile „MySQL“ kann die Datei „my.ini“ über den Konfig-Button angepasst werden. Um sicherzustellen, dass die Beschränkungen der ENUM-Werte korrekt angewendet werden, sollte der Wert „sql_mode“ um „STRICT_TRANS_TABLES“ ergänzt werden. Anschließend kann erst Apache und dann MySQL im Control Panel gestartet werden.

Bei Linux erfolgt die Installation nicht über eine Datei, sondern stattdessen über die folgenden Befehle:
```
chmod 755 xampp-linux-*-installer.run
sudo ./xampp-linux-*-installer.run
```

### Import der Datenbank
Wenn Apache und MySQL erfolgreich gestartet wurden, ist MariaDB über den Link http://localhost/phpmyadmin/ aufrufbar. In der oberen Leiste ist der Button „Importieren“ zu finden. Als zu importierende Datei sollte die bereitgestellte SQL-Datei ausgewählt werden, die anderen Einstellungen müssen nicht geändert werden. Nach dem Import ist die neu erstellte Datenbank in der linken Seitenleiste unter dem Namen „buechertausch_db“ zu finden. 
