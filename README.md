# Werkstattauftrag W7 Webmin


# 1. Autoren, Versionierung des Dokumentes

**Autoren:** Elia Garzi, Sebastian Gruber

**Datum:** 29.09.2021

**Version:** 1.0

# 2. Einfuehrung

**1. Was ist Webmin?**
   - Beschreibung: Welche Funktionen wird der Service erfuellen

      Webmin ist ein interface welches dir erlauft viele features und Funktionen zentral im Webmingui zu verwalten. Ohne Webmin müsste man alles manuell auf der Konsole eintippen.

   - Vorgesehener Zeitaufwand für die Realisierung


      Für die Konfiguration und Einrichtung des Webin und VNC solte man ungefähr 15 min einberechnen

   - Stolpersteine

 Die Konfiguration des Raspberry-Pi's lief bei uns relativ glatt. Unser Raspi image konnten wir ohen Probleme auf den Pi spielen. Daseinzige Problem dases gab war das wir kein Adapter für den Bildschirm hatten. Zum Glück hatte unser Lehrer die passeneden Adapter dabei.




# 3. Benoetigte Hard- und Software

**Hardware** 
   -  Raspberry-pi 3
   -  Bildschirm
   -  mini HDMI Kabel und Adapter
   -  Externe Tastatur
   -  SD Speicherkarte (Raspi Image)
   -  Stromkabel USB-C (Raspberry Pi)


**Software**
- Pi OS 
- Pi OS Imager 
- Webmin Repository (http://download.webmin.com/download/repository)
- Webmin Packages (apt install webmin)

# 4. Installationsanleitung

## **1. Pi-OS installieren**
Bevor man das Raspberry Pi nutzen kann, muss darauf ein Betriebssystem installiert werden.
Dazu gibt das offizielle Pi OS, welches auf Debian basiert.

Zur einfachen Installation des Betriebessystemes nutzen wir den Pi Imager, der von der offiziellen Website heruntergeladen werden kann:

https://www.raspberrypi.org/software/


### **2. Pi-Hole Image auf SD Karte installieren**
Nach der Installation startet man den Pi Imager und wählt als Betriebssystem Pi OS (32-Bit) aus und als SD-Karte die SD-Karte die man mit dem Raspberry Pi bekommen hat. 

## **2. Grundkonfiguration vornehmen**
Für diesen Schritt braucht man: 
- Einen Bildschirm 
- WLAN oder LAN-Kabel


Sobald man das Pi OS installiert hat, kann man die SD-Karte in den Raspberry Pi stecken und das Pi starten. Anschliessend kommt eine einfache Grundkonfiguration. Hier muss man die Sprache und das Passwort setzen. Es ist wichtig, dass die Zeitzone richtig auf Zurich konfiguriert ist. 

Wir haben unser Raspberry Pi mit einem TBZ Access Point verbunden. Dafür wählt man oben Rechts das WLAN-Icon aus. 

![Den TBZ-WLAN Access Point auswählen für eine Netzwerkverbindung](https://user-images.githubusercontent.com/62818267/135052323-5dcdb100-6dda-405a-a4b8-f963bef7c092.png)


## **3 Remoteverbindung mit Raspberry Pi herstellen**
Um das Raspberry Pi einfacher zu verwalten nutzt man eine Remoteverbindung. Dies ermöglicht, dass man über das Netzwerk mit dem Raspberry Pi arbeiten kann. 

### **1. VNC und SSH aktivieren**

VNC und SSH sind beides Protokolle für die Remote-Verwaltung von Linux-Servern.

Im Raspberry Pi Desktop geht man oben Links auf Einstellungen > Raspberry-Pi-Konfiguration > Schnittstellen

![Verbindung mit ssh und vnc](https://user-images.githubusercontent.com/62818267/135980313-4ade90ff-8970-4c72-b515-f6ff9014baa2.png)

Damit die Verbindung funktioniert, braucht man die IP-Adresse. Hierfür öffnet man die Konsole auf dem Raspberry Pi und gibt den Befehl 

      ip a

![Ip Adresse](https://user-images.githubusercontent.com/62818267/135597364-169c4601-91f3-4f94-884e-76bfd55f4312.png)

### **2. Sich über VNC verbinden**
Für VNC braucht man einen VNC-Client. Ein VNC-Client kann von hier heruntergeladen werden: 

https://www.realvnc.com/download/viewer/

Anschliessend installiert man den Client und verbindet sich mit dem Raspberry Pi mit der IP-Adresse.

### **3. Sich über SSH verbinden**
Um sich über SSH zu verbinden braucht man eine SSH-Konsole. Z.B. Putty. Putty kann von hier heruntergeladen werden: 

https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

Anschliessend startet man Putty und gibt die IP-Adresse vom Raspberry Pi ein

![Putty](https://user-images.githubusercontent.com/62818267/135974827-71e1a721-2e2d-4174-9a6e-218f597886ce.png)



## **3 Webmin auf dem Raspberry Pi installieren**

### **1. Alle Updates installieren**

Bevor man Webmin installiert, sollte man sicherstellen, dass alle Updates installiert sind.

Dazu öffnet man die Konsole auf dem Raspberry Pi und gibt folgenden Befehl ein:

         sudo apt-get update && sudo apt-get upgrade -y



### **2. Webmin Repository hinzufügen**

**Was ist ein Repository?**
Bevor wir diesen Schritt machen, ist es wichtig zu verstehen, was ein Repository ist und welche Aufgabe es hat. 

Für die Installation von Webmin braucht man ein spezielles Repository. Man braucht das Webmin Repository. In diesem Repository werden alle Packages für die Installation und Updates bereitgestellt. Dieses Repository muss manuell zur Repository-Liste hinzugefügt werden. 

Dazu editiert man die sources.list Datei, in welcher alle Repositorys gespeichert werden, welche z.B. bei einem apt-get update abgefragt werden. 

         sudo nano /etc/apt/sources.list

In der sources.list fügt man nun das Webmin-Repository hinzu, indem man folgende Zeile am Ende der Datei einfügt.

         deb http://download.webmin.com/download/repository sarge contrib

Am Ende sollte dies so aussehen. 

Bild von Sources.list


### **3. Webmin installieren**
Nun ist alles bereit für die Installation. Das Webmin-Repository kann erreicht werden. 

Um das neue Repository nutzen zu können, muss man den PGP Key hinzufügen:

         wget -q -O- http://www.webmin.com/jcameron-key.asc | sudo apt-key add

Nun kann die Linux Paketlisten updaten:

         sudo apt update

Nun kann man Webmin insallieren:

         sudo apt install webmin
         
Anschliessend kann man sich mit dem Webinterface per Browser verbinden:

         https://IP-Adresse:10000

### **5. Webmin administrieren**
Hier noch einige Befehle für das Arbeiten mit Pi Os und Webmin

- Paketlisten aktualisieren: sudo apt-get update
- Pi Os updaten: sudo apt-get upgrade
- Webmin starten: sudo systemctl start webmin.service
- Webmin stoppen: sudo sytemctl stop webmin.service
- Webmin neustarten: sudo systemctl restart webmin.service

# 5. Qualitaetskontrolle

# 6. Error-Handling

# 7. Quellen

**Bilder:** Von uns

**Pi-Imager:** https://www.raspberrypi.org/software/

**Putty:** https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

**VNC Viewer:** https://www.realvnc.com/de/connect/download/viewer/

**Webmin:** https://webmin.com/

# 8. OpenSource Lizenz
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/3.0/ch/88x31.png" /></a><br />Dieses Werk ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/">Creative Commons Namensnennung - Nicht-kommerziell - Weitergabe unter gleichen Bedingungen 3.0 Schweiz Lizenz</a>
