# Lab 2

**Author: Benjamin Medicke**<br>
**Topics: IPS & Anti-Virus**

[lab1](lab1.md) | **lab2** | [lab3](lab3.md) | [lab4](lab4.md)

---

<!-- vim-markdown-toc GFM -->

* [Lab 2.1 IPS](#lab-21-ips)
  * [2.1.3 Topologien einstellen](#213-topologien-einstellen)
  * [2.1.4 IPS Blade aktivieren](#214-ips-blade-aktivieren)
  * [2.1.6 Protected Scope für die Linux Instanz](#216-protected-scope-für-die-linux-instanz)
  * [2.1.7 Profil "Strict" editieren](#217-profil-strict-editieren)
  * [2.1.9 Update](#219-update)
  * [2.1.10 Traffic generieren und Logs prüfen](#2110-traffic-generieren-und-logs-prüfen)
  * [Aufgetretene Probleme](#aufgetretene-probleme)
* [Lab 2.2 Anti-Virus](#lab-22-anti-virus)
  * [2.2.2 Aktivierung Blade: Anti-Virus](#222-aktivierung-blade-anti-virus)
  * [2.2.5 Anpassen des zuvor angelegten Profils](#225-anpassen-des-zuvor-angelegten-profils)
  * [2.2.7 Update Anti-Virus](#227-update-anti-virus)
  * [2.2.8 Testlauf Anti-Virus](#228-testlauf-anti-virus)
* [Lab 2.3 HTTPS Inspection](#lab-23-https-inspection)

<!-- vim-markdown-toc -->

## Lab 2.1 IPS

In diesem Abschnitt wurde das Intrusion Prevention System Blade aktiviert und demonstriert.

### 2.1.3 Topologien einstellen

> ![image](https://user-images.githubusercontent.com/173962/118303243-83ff7700-b4e5-11eb-9738-a4945f31f45f.png)
>
> Topology von eth0 auf "external" stellen.

> ![image](https://user-images.githubusercontent.com/173962/118303483-cb860300-b4e5-11eb-968e-8d70cd016689.png)
>
> Topology von eth1 auf "internal" stellen. Aktivieren von Anti-Spoofing.

### 2.1.4 IPS Blade aktivieren

> ![image](https://user-images.githubusercontent.com/173962/118304190-a5ad2e00-b4e6-11eb-8787-24d5e11f7c53.png)
>
> IPS blade aktiviert

> ![003](https://user-images.githubusercontent.com/173962/116441883-29fa8280-a852-11eb-8233-b5ce5fd76ff8.PNG)
>
> Setzten der "IPS First Time Activation" Einstellung auf "According to the Threat Prevention policy"

### 2.1.6 Protected Scope für die Linux Instanz

> ![image](https://user-images.githubusercontent.com/173962/116443098-87430380-a853-11eb-93a8-dd37cb9475ed.png)
>
> Linux Instanz

> ![image](https://user-images.githubusercontent.com/173962/116443346-d8eb8e00-a853-11eb-9725-46d41451d307.png)
>
> Hinzufügen der Linux Instanz zum Protected Scope

### 2.1.7 Profil "Strict" editieren

> ![image](https://user-images.githubusercontent.com/173962/116444319-e6554800-a854-11eb-95ac-c66604399bbe.png)
>
> Kopie des "Strict" Profiles

> ![image](https://user-images.githubusercontent.com/173962/118305074-ca55d580-b4e7-11eb-875e-30cb60485282.png)
>
> Nur IPS Blade aktivieren, alle Aktivierungs-Szenarien auf "Prevent"

> ![image](https://user-images.githubusercontent.com/173962/116444786-6380bd00-a855-11eb-9815-dac316e523fa.png)
>
> Publish & Install um die Policies anzuwenden

> ![image](https://user-images.githubusercontent.com/173962/116445471-35e84380-a856-11eb-910a-df0847e93d46.png)
>
> Neues Profil und zugewiesene Linux Instanz zum Protected Scope

### 2.1.9 Update

Nach der Installation des Profils wurde ein Update des IPS und des Management Servers durchgeführt.


> ![image](https://user-images.githubusercontent.com/173962/116447220-076b6800-a858-11eb-94e6-e242ad288cb0.png)
>
> Management Update

> ![image](https://user-images.githubusercontent.com/173962/116449247-426e9b00-a85a-11eb-8ec2-7650a48b98ac.png)
>
> IPS Update

> ![image](https://user-images.githubusercontent.com/173962/116450678-dd1ba980-a85b-11eb-9fb1-561fd58be2e3.png)
>
> Alles up to date.

### 2.1.10 Traffic generieren und Logs prüfen

Um das IPS zu testen wurde ein (default) Nmap Script Scan durchgeführt. Die `default` Skripte sind nicht sehr aggressiv, ich hoffe Google vergiebt mir.

> ![image](https://user-images.githubusercontent.com/173962/118308457-3fc3a500-b4ec-11eb-80bd-f06c9ca7a006.png)
>
> Start eines Nmap-Script-Scans

> ![image](https://user-images.githubusercontent.com/173962/118308166-ee1b1a80-b4eb-11eb-8192-1467f8783fc0.png)
>
> Erkannter Nmap-Script-Scan: `sudo nmap -sC google.com`

> ![image](https://user-images.githubusercontent.com/173962/118311190-db0a4980-b4ef-11eb-86c1-4c3fa5b7ef8f.png)
>
> Erkannter Nmap-Script-Scan: Details

### Aufgetretene Probleme

* Das Update hängt endlos.
 * Gelöst durch Beenden der aktuellen Session.

>![image](https://user-images.githubusercontent.com/173962/116446047-dc344900-a856-11eb-9c49-0a6e22d7781e.png)
>
> Das Update blockiert bis die aktuelle Session beendet wird.

>![image](https://user-images.githubusercontent.com/173962/116446180-fc640800-a856-11eb-9845-fa1426b3747c.png)
>
> Was leider übersehen wurde, weswegen sehr lange auf die Fertigstellung gewartet wurde. 

## Lab 2.2 Anti-Virus

Hier wurde das Anti-Virus Blade aktiviert und mit dem [eicar Anti Malware Testfile](https://www.eicar.org/?page_id=3950) erfolgreich getestet.

### 2.2.2 Aktivierung Blade: Anti-Virus

> ![image](https://user-images.githubusercontent.com/173962/118311585-65eb4400-b4f0-11eb-8f0f-52d26200dd10.png)
>
> Anti-Virus Blade aktiviert "According to the Threat Prevention Policy"

### 2.2.5 Anpassen des zuvor angelegten Profils

Die Linux Instanz ist bereits im Protected Scope, dieser wird nun angepasst.

> ![image](https://user-images.githubusercontent.com/173962/118311906-d5613380-b4f0-11eb-8823-405ee8b68dc7.png)
>
> Anti-Virus im vorhandenem Profil aktiviert

> ![image](https://user-images.githubusercontent.com/173962/118312058-122d2a80-b4f1-11eb-9d38-761d788cd410.png)
>
> Anti-Virus Detailseite, hier wurde später auch der Archiv-Scan und Scan aller Datei-Typen aktiviert

> ![image](https://user-images.githubusercontent.com/173962/118312124-2ec96280-b4f1-11eb-8990-476603f7f2fa.png)
>
> Die aktualisierte Security Policy

### 2.2.7 Update Anti-Virus

> ![image](https://user-images.githubusercontent.com/173962/118312766-24f42f00-b4f2-11eb-8a62-b0dcb59c385a.png)
>
> Es gibt keinen manuellen Update-Button, also wurde auf alle 5 Minuten gestellt und kurz gewartet.

### 2.2.8 Testlauf Anti-Virus

> ![image](https://user-images.githubusercontent.com/173962/118392001-7bb75100-b637-11eb-9a9d-b02cebc0bda9.png)
>
> Es wurde der Eicar Download mit `curl` über HTTP versucht.

> ![image](https://user-images.githubusercontent.com/173962/118371195-bf647900-b5ab-11eb-893f-567c0cd1a7b9.png)
>
> Ebenso via Browser

> ![image](https://user-images.githubusercontent.com/173962/118392047-bae5a200-b637-11eb-85ba-b1f94cde8f48.png)
>
> Blockierte Eicar Test-Malware über HTTP

> ![image](https://user-images.githubusercontent.com/173962/118371130-68f73a80-b5ab-11eb-8831-8c1479ff0e1d.png)
>
> Die Eicar Test-Malware wurde auch erfolgreich über HTTPS erkannt und der Download unterbunden. (Nach Aktivierung von HTTPS Inspection)

## Lab 2.3 HTTPS Inspection

Um HTTPS aufzubrechen und zu inspizieren wurde ein selbstsigniertes Zertifikat erstellt und installiert.

> ![image](https://user-images.githubusercontent.com/173962/118316186-cc736080-b4f6-11eb-8bca-2c9fccb91318.png)
>
> Neues Zertifikat erstellt und als `mycert.cer` exportiert

> ![image](https://user-images.githubusercontent.com/173962/118316556-4277c780-b4f7-11eb-880a-e96af84e6c4e.png)
>
> Neue HTTPS-Inspection Policy

> ![image](https://user-images.githubusercontent.com/173962/118318567-dc407400-b4f9-11eb-83e3-dc3b031c78ec.png)
>
> Unterbundener HTTPS Request bei Download von Eicar-Malware Testfile auch  über HTTPS

Das `-k` Flag erlaubt die Verwendung von Self-Signed Certificates. Als Browser wurde Chromium verwendet, welcher mit `apt get install chromium` installiert wurde.

> ![image](https://user-images.githubusercontent.com/173962/118319452-178f7280-b4fb-11eb-99e9-2a3090c07ccb.png)
>
> HTTPS Fehler bei Besuch einer TLS/SSL Seite

> ![image](https://user-images.githubusercontent.com/173962/118320138-1743a700-b4fc-11eb-8c91-a106898088f2.png)
>
> Zertifikatsimport in Chromium

>![image](https://user-images.githubusercontent.com/173962/118319750-7ead2700-b4fb-11eb-9ff3-48baf86561cd.png)
>
> Nach Import des Zertifikates wird keine Warnung generiert

> ![image](https://user-images.githubusercontent.com/173962/118318684-03974100-b4fa-11eb-8f60-0e3ab7b2d69c.png)
>
> Detailansicht: Erkanntes Eicar Testfile, auch über HTTPS

[nächstes Lab](lab3.md)
