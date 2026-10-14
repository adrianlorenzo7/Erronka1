---
layout: page
title: "Segurtasuna eta erabilgarritasun handia"
---
# Kontingentzia-plana eta Aktiboen Azterketa

---


## AURKIBIDEA

1. [KONTINGENTZIA-PLANA ETA AKTIBOEN AZTERKETA](#1-kontingentzia-plana-eta-aktiboen-azterketa)
   - [1.1. Enpresaren Deskribapena eta Banaketa Fisikoa (Orbis)](#11-enpresaren-deskribapena-eta-banaketa-fisikoa-orbis)
   - [1.2. Aktiboen Azterketa](#12-aktiboen-azterketa)
   - [1.3. Arrisku-eszenatokiak](#13-arrisku-eszenatokiak)
   - [1.4. Kontingentzia-plana eta Berreskuratze Denborak](#14-kontingentzia-plana-eta-berreskuratze-denborak)
2. [PASAHITZ POLITIKA OFIZIALA ETA IDENTITATE KUDEAKETA](#2-pasahitz-politika-ofiziala-eta-identitate-kudeaketa)
   - [2.1. Planteamendua](#21-planteamendua)
   - [2.2. Pasahitz Sendoen Baldintza Teknikoak](#22-pasahitz-sendoen-baldintza-teknikoak)
   - [2.3. Araudi Ofiziala](#23-araudi-ofiziala)
3. [SEGURTASUN FISIKOA ETA SARBIDE KONTROLA](#3-segurtasun-fisikoa-eta-sarbide-kontrola)
   - [3.1. Justifikazio Teknikoa](#31-justifikazio-teknikoa)
   - [3.2. Sarbide Mekanismoak eta Biometria Baztertzeko Arrazoiak](#32-sarbide-mekanismoak-eta-biometria-baztertzeko-arrazoiak)
   - [3.3. Zones araberako Murrizketa Politika](#33-zones-araberako-murrizketa-politika)
4. [BABES-KOPIEN SOFTWAREA, EDR-A ETA SIEM MONITORIZAZIOA](#4-babes-kopien-softwarea-edr-a-eta-siem-monitorizazioa)
   - [4.1. Software Zerrenda eta Kokapen Logikoa](#41-software-zerrenda-eta-kokapen-logikoa)
   - [4.2. Babes-kopien Estrategia (3-2-1 Araua)](#42-babes-kopien-estrategia-3-2-1-araua)
5. [SARE DISEINUA, IP HELBIDERATZEA ETA DHCP KONFIGURAZIOA](#5-sare-diseinua-ip-helbideratzea-eta-dhcp-konfigurazioa)
   - [5.1. Sare Egitura eta Exekuzio Teknikoa](#51-sare-egitura-eta-exekuzio-teknikoa)
   - [5.2. Konfigurazio eta IP Helbideratze Taula](#52-konfigurazio-eta-ip-helbideratze-taula)
6. [URRUNEKO SARBIDE SEGURUKO AUKERAK (VPN)](#6-urruneko-sarbide-seguruko-aukerak-vpn)
   - [6.1. Mekanismoen Ebaluazioa](#61-mekanismoen-ebaluazioa)
   - [6.2. Inplementazio Politika](#62-inplementazio-politika)
7. [SEGURTASUN PERIMETRALA ETA SUEBAKIAREN ARAUAK](#7-segurtasun-perimetrala-eta-suebakiaren-arauak)
   - [7.1. Suebaki Arkitektura](#71-suebaki-arkitektura)
   - [7.2. Trafikoa Iragazteko Arauen Matrizea (Firewall Rules)](#72-trafikoa-iragazteko-arauen-matrizea-firewall-rules)

---

## 1. KONTINGENTZIA-PLANA ETA AKTIBOEN AZTERKETA

### 1.1. Enpresaren Deskribapena eta Banaketa Fisikoa (Orbis)
Orbis e-commerce enpresak sarean saltzen du[cite: 4]. Bere arrakasta hiru gauzaren mende dago: webgunea une oro erabilgarri egotea, erosketak modu seguruan egitea eta bezeroen datu pertsonalak ondo zaintzea[cite: 4].

Asebetetako plano arkitektonikoaren arabera, enpresaren banaketa fisikoa eta teknikoa honela egituratzen da[cite: 4]:
* **CPD / Zerbitzari Eremua:** Segurtasun handiko eremua, rack armairuarekin eta arrisku elektrikoaren seinaletazioduna[cite: 4]. Bertan kokatzen dira hiru zerbitzari nagusiak:
  * **Windows Server 2019 (192.168.10.1):** Active Directory Jabego Domeinuko Zerbitzaria (AD DS), barne DNS zerbitzaria eta DHCP kudeatzaile nagusia[cite: 4].
  * **Ubuntu Server 1 (192.168.10.2):** Nginx web-zerbitzaria, e-commerce ataria eta ordainketa-pasabideak ostatatzen ditu[cite: 4].
  * **Ubuntu Server 2 (192.168.10.3):** Datu-base korporatiboa (PostgreSQL/MySQL), Wazuh SIEM zerbitzari zentrala eta enkriptatutako babes-kopien biltegia[cite: 4].
* **Informatika Saila:** IT kideen lan-eremua[cite: 4]. 3 ekipo ahaltsu ditu (PC POT 1, PC POT 2, PC POT 3), hardwarea konpontzeko mahai espezializatua (esku-eskuturreko antiestatikoaren erabilera nahitaezkoarekin - ESD), larrialdietarako irteera zuzena (EATT) eta RAEE hondakin elektronikoak kudeatzeko eremu propioa[cite: 4].
* **Administrazioa eta Logistika Saila:** Eremu diafano nagusia, 8 bezero-ekiporekin (PC 1etik PC 8/9ra), 2 sareko inprimagailu IP finkoarekin (Sareko Inprimagailua - IP Fija), CO2 suntsitzailea eta birziklapen-puntu integratua (RAEE, papera eta plastikoak)[cite: 4].
* **Harrera eta Eremu Komunak:** Publikoari irekitako harrera-lekua, sukaldea/atsedenlekua eta komunak[cite: 4].

---

### 1.2. Aktiboen Azterketa

| Aktibo Kategoria | Aktibo Zehatza | Kokapen Fisikoa / IPa | Deskribapen Teknikoa | Eragindako Dimentsioak |
| :--- | :--- | :--- | :--- | :--- |
| **[D] Datuak** | Bezeroen eta Transakzioen DBa | CPD / 192.168.10.3 | Informazio pertsonala (PII), eskaerak, ordainketa-erregistroak | Konfidentzialtasuna, Integritatea, Erabilgarritasuna |
| **[S] Softwarea** | Web Ataria (E-Commerce) | CPD / 192.168.10.2 | Nginx bidez ustiatutako aplikazio publikoa | Erabilgarritasuna, Integritatea |
| **[S] Softwarea** | AD DS / DNS / DHCP | CPD / 192.168.10.1 | Identitateen kudeaketa, barne DNSa eta IP esleipena | Autentikotasuna, Konfidentzialtasuna |
| **[H] Hardwarea** | Zerbitzari Rack Armairua | CPD / Zerbitzari Eremua | Cómputo-azpiegitura fisiko nagusia (3 Zerbitzari) | Erabilgarritasuna |
| **[H] Hardwarea** | 12 Bezero-Ekipo | Admin/Logistika eta IT | 8 PC arrunt + 3 PC POT (IT sailean) | Integritatea, Konfidentzialtasuna |
| **[H] Hardwarea** | Sareko Inprimagailuak | Administrazio eta Logistika | IP finkoa duten 2 inprimagailu korporatibo (.55, .56) | Erabilgarritasuna |
| **[COM] Sareak** | Perimetro Suebakia / Routerra | CPD / Perimetroa | pfSense gailua, sareen arteko bideraketa eta babesa | Erabilgarritasuna |

---

### 1.3. Arrisku-eszenatokiak
* **Ransomwarea lan-postu batean:** Administrazio edo Logistikako PC batean (192.168.10.50 - .150) phishing bidez gertatutako infekzioa, SMB protokoloaren bidez rack armairuko zerbitzariei eraso egiteko saiakerarekin[cite: 4].
* **DDoS Erasoa E-Commerce atarian:** Web zerbitzaria (192.168.10.2) trafiko ziztrinaren bidez itotzea, salmentak erabat paralizatuz[cite: 4].
* **SQL Injekzioa / Datu-ihesa:** Web atariko ahultasun bat erabiliz Ubuntu Server 2ko (192.168.10.3) datu-basea erauzteko saiakera[cite: 4].
* **CPDko Ezusteko Fisiko edo Elektrikoa:** Rack armairuko zirkuitulaburrak edo suteak (Arrisku Elektrikoa) 3 zerbitzarien geldialdia eragitea[cite: 4].

---

### 1.4. Kontingentzia-plana eta Berreskuratze Denborak

#### 1. Erasoaren Aurretik (Prebentzioa eta Prestakuntza)
Fase hau oinarrizkoena da, eraso baten eragina ahalik eta gehien murrizteko edo zuzenean ekiditeko balio baitu[cite: 4].
* **Segurtasun-kopiak (Backup-ak):** Zure datu garrantzitsuenen kopiak egin behar dira aldizka[cite: 4]. Urrezko araua 3-2-1 da: gutxienez 3 kopia izan, 2 euskarri ezberdinetan gorderik (adibidez, disko gogor batean eta hodeian), eta kopia bat fisikoki erabat deskonektatuta (eraso batek hodeiko edo sareko kopia ere kaltetu ez dezan)[cite: 4].
* **Kopien egiaztapena:** Askotan kopiak egiten dira, baina gero ez dira funtzionatzen duten egiaztatzen[cite: 4]. Beharrezkoa da aldizka probatzea kopia horietatik datuak berreskuratzea[cite: 4].
* **Eguneratzeak:** Software, sistema eragile eta aplikazio guztiak eguneratuta mantendu behar dira[cite: 4]. Fabrikatzaileek ahulguneak aurkitzen dituztenean adabakiak ateratzen dituzte; beraz, eguneratzeek ateak ixten dizkiote erasotzaileari[cite: 4].
* **Sarbide-kontrolak:** Pertsona guztiek ez dute enpresako datu guztietarako sarbidea izan behar[cite: 4]. "Gutxieneko pribilegioaren" printzipioa aplikatu behar da; hau da, bakoitzari bere lanerako behar-beharrezkoa den sarbidea soilik eman[cite: 4].

#### 2. Erasoan Zehar (Erantzuna eta Isolamendua)
Erasoa gertatzen ari dela konturatzen zarenean (adibidez, pantailan mezu arraroak ateratzen direnean, fitxategiak enkriptatzen hasten direnean edo sistema oso motela dabilenean), azkar eta hotz jokatu behar da[cite: 4].
* **Sare-deskonexioa (Isolamendua):** Berehala deskonektatu kaltetutako ordenagailua saretik[cite: 4]. Kendu kablea (Ethernet) eta desaktibatu Wi-Fi eta Bluetooth-a[cite: 4]. Honek eragozten du birusak sareko beste ekipo batzuetara edo zerbitzarietara pasatzea[cite: 4].
* **Zerbitzu kritikoak etetea:** Beharrezkoa bada, enpresako sistema edo datu-base nagusiak gelditu egin behar dira arriskua mugatzeko[cite: 4].
* **Erasoa identifikatzea:** Saiatu zehazten zer gertatu den: Ransomware bat al da (fitxategiak blokeatu dituztenak), datu-lapurreta bat, sarbide baimenagabe bat… Hori jakiteak asko lagunduko du ondorengo urratsetan[cite: 4].
* **Ez ordaindu berehala:** Erasotzaileek dirua eskatzen badute (ransomware kasuetan), adituek gomendatzen dute ez ordaintzeas, ez baitago segurtasunik datuak itzuliko dituztenik eta, gainera, delinkuentzia finantzatzen delako[cite: 4].

#### 3. Erasoaren Ondoren (Susperketarako eta Analisia)
Behin erasoa geldituta eta sistema isolatuta dagoela, egoera normalera bueltatzeko eta hemendik aurrera berriro ez gertatzeko[cite: 4].
* **Sistemak garbitzea eta birsortzea:** Kaltetutako ekipoak formateatu egin behar dira eta sistemaren instalazio garbi bat egin[cite: 4]. Behin sistema garbi dagoela, lehen fasean prestatutako segurtasun-kopi garbiak erabili datuak berreskuratzeko[cite: 4].
* **Kredentzialak aldatzea:** Aldatu pasahitz guztiak, batez ere konprometituta egon daitezkeen erabiltzaile-kontuenak eta zerbitzarien sarbide-gakoak[cite: 4].
* **Azterketa forentsea:** Garrantzitsua da ikertzea ea nola lortu zuten erasotzaileek sisteman sartzea (adibidez, phishing mezu baten bidez, pasahitz ahul baten bitartez edo sistema zaharkitu baten bidez)[cite: 4]. Hori jakinda, ahulgune hori konponduko da[cite: 4].
* **Txostena eta komunikazioa:** Beharrezkoa bada (eta legediak agintzen badu, datu pertsonalen babesaren ikuspegitik, hala nola Datuak Babesteko Espainiako Agintzaritzan - AEPD), gertakariaren berri eman behar da[cite: 4]. Era berean, barne-txostena osatuko da[cite: 4].

---

## 2. PASAHITZ POLITIKA OFIZIALA ETA IDENTITATE KUDEAKETA

### 2.1. Planteamendua
Identity and Access Management (IAM) egitura zentralizatua ezartzen da Windows Server 2019 (192.168.10.1) Active Directory zerbitzarian Talde Politiken bidez (GPO), eta Linux zerbitzariekin sinkronizatzen da `pam_pwquality` moduluaren bidez[cite: 4].

### 2.2. Pasahitz Sendoen Baldintza Teknikoak
* **Gutxieneko luzera:** 14 karaktere[cite: 4].
* **Konplexutasun-iragazkia:** Hizki maiuskulak, minuskulak, zenbakiak eta ikur bereziak (`!@#$%^&*`)[cite: 4].
* **Berritzeko epea:** 90 egun lan-postu arruntetan eta 45 egun IT saileko administrazio-kontuetan[cite: 4].
* **Kontuaren blokeoa:** 5 saiakera oker jaso ondorerako kontua 30 minutuz automatikoki blokeatzea[cite: 4].
* **MFA (Faktore Anitzeko Autentifikazioa):** Nahitaezkoa TOTP bidez (Google/Microsoft Authenticator) VPN atarietan eta IT kudeaketa-paneletan sartzeko[cite: 4].

### 2.3. Araudi Ofiziala
> **PASAHITZ ETA IDENTITATE SEGUNDOEN ARAUDI KORPORATIBOA - ORBIS**  
> 1. Erabiltzaile bakoitza bere kredentzialen erantzule bakarra da; zeharo debekatuta dago pasahitzak partekatzea edo paperean idaztea[cite: 4].  
> 2. Behin-behineko pasahitzak lehen saio-hasieran aldatu behar dira neurgarriki[cite: 4].  
> 3. IT saileko kideek kontu izendunak erabiliko dituzte administrazio-lanetarako, ohiko nabigaziorako kontu arruntak erabiliz[cite: 4].

---

## 3. SEGURTASUN FISIKOA ETA SARBIDE KONTROLA

### 3.1. Justifikazio Teknikoa
CPD / Zerbitzari Eremuak erakundeko aktibo kritiko guztiak biltzen ditu (rack armairua, 3 zerbitzari nagusiak)[cite: 4]. Babes fisikoko geruzak ezinbestekoak dira baimenik gabeko manipulazioak prebenitzeko[cite: 4].

### 3.2. Sarbide Mekanismoak eta Biometria Baztertzeko Arrazoiak
* **Hautatutako Sistema:** RFID Hurbiltasun-txartela + PIN kode pertsonala (Faktore Bikoitz Fisikoa) CPDko ate nagusiko sarbide-kontrolagailuan[cite: 4].
* **Sistema Biometrikoen Bazterketa eta Kostu-Justifikazioa:** Irakurgailu biometrikoak (hatz-markak edo irisa) baztertu egin dira beren ezarpen- eta mantentze-kostu altuagatik, bai eta Datuen Babeseko Araudi Orokorrak (DBEO/RGPD) datu biometrikoen kudeaketarako ezartzen dituen legezko baldintza konplexuengatik[cite: 4]. 12 langileko azpiegitura baterako, RFID + PIN konbinazioak segurtasun-maila sendoa eta kostu-eraginkortasun optimoa bermatzen ditu[cite: 4].

### 3.3. Zones araberako Murrizketa Politika
* **Informatika Saila eta CPDa:** CPDrako sarbidea IT saileko 2 administratzaileei soilik mugatzen zaie[cite: 4]. Informatika sailera sartzeko ere RFID txartela exijitzen da[cite: 4].
* **Administrazioa eta Logistika:** 12 langileek beren eremuko ateetan txartel bidezko baimena dute[cite: 4].
* **Publikoa eta Bisitariak:** Harreratik barnera igotzea guztiz debekatuta dago[cite: 4]. Harrera-eremuan ez dago LAN sareko RJ45 konexio aktiborik eta Gonbidatuen Wi-Fi isolatua bakarrik dago erabilgarri (VLAN 40)[cite: 4].

---

## 4. BABES-KOPIEN SOFTWAREA, EDR-A ETA SIEM MONITORIZAZIOA

### 4.1. Software Zerrenda eta Kokapen Logikoa
* **SIEM / EDR Zentralizatua (Wazuh):**
  * **Wazuh Server:** Ubuntu Server 2 (192.168.10.3) zerbitzarian kokatuta[cite: 4].
  * **Wazuh Agent:** 3 zerbitzarietan eta 12 bezero-ekipoetan (IT saileko PC POT 1-3 barne) instalatuta, gertaerak denbora errealean analizatzeko[cite: 4].
* **Babes-kopien Tresnak:**
  * **Veeam Backup Agent:** Windows Server 2019 (192.168.10.1) zerbitzarirako[cite: 4].
  * **BorgBackup / Restic:** Linux zerbitzarientzako (192.168.10.2 eta .3) gidoi automatizatuak, AES-256 enkriptatzearekin[cite: 4].

### 4.2. Babes-kopien Estrategia (3-2-1 Araua)
1. **1. Kopia (Tokikoa):** Eguneroko snapshot-ak zerbitzari bakoitzean bertan gordetzen dira[cite: 4].
2. **2. Kopia (Sare Lokala / NAS):** Gaueko kopia osoa sare barruko NAS gailu batera igortzen da[cite: 4].
3. **3. Kopia (Hodei Immutagarria):** Asteroko kopia enkriptatua AWS S3 Cloud biltegiratze immutagarrira bidaltzen da (Object Lock teknologiarekin ransomwarearen aurka)[cite: 4].

---

## 5. SARE DISEINUA, IP HELBIDERATZEA ETA DHCP KONFIGURAZIOA

### 5.1. Sare Egitura eta Exekuzio Teknikoa

Planoko atalak eta IP helbide-eskema berria kontuan hartuz, sarearen topologia honela definitzen da[cite: 4]:

* **Zerbitzariak (CPD - IP Estatiko Finkoak):**
  * **Windows Server 2019:** 192.168.10.1 (DNS, DHCP zerbitzaria)[cite: 4].
  * **Ubuntu Server 1:** 192.168.10.2 (Web Nginx, E-Commerce)[cite: 4].
  * **Ubuntu Server 2:** 192.168.10.3 (Datu-basea, Wazuh SIEM, Backups)[cite: 4].
* **DHCP Zerbitzariaren Konfigurazioa (Windows Server 2019 - 192.168.10.1):**
  * **Banaketa-tartea (DHCP Scope):** `192.168.10.50` - `192.168.10.150` (12 langileen lan-postuei IPa dinamikoki esleitzeko)[cite: 4].
  * **Salbuespen-tartea (Excluded Range / Ez Banatu):** `192.168.10.55` - `192.168.10.60`[cite: 4].
  * **Justifikazio Teknikoa:** Administrazio eta Logistika sailean 2 Sareko Inprimagailu IP Finko daude (Sareko Inprimagailua - IP Fija)[cite: 4]. Gailu horiei IP finko estatikoak esleitzen zaizkie tarte baztertu honen barruan (adibidez, `192.168.10.55` eta `192.168.10.56`), DHCP bidezko IP gatazkak erabat saihestuz[cite: 4].

---

### 5.2. Konfigurazio eta IP Helbideratze Taula

| Eremua / Ekipoa | Kokapena Planoan | IP / Tartea | Maskara | Mota / Funtzio Nagusia |
| :--- | :--- | :--- | :--- | :--- |
| **Windows Server 2019** | CPD / Rack Armairua | 192.168.10.1 | 255.255.255.0 | Estatikoa (DNS, DHCP Zerbitzaria) |
| **Ubuntu Server 1** | CPD / Rack Armairua | 192.168.10.2 | 255.255.255.0 | Estatikoa (Nginx Web / E-commerce) |
| **Ubuntu Server 2** | CPD / Rack Armairua | 192.168.10.3 | 255.255.255.0 | Estatikoa (PostgreSQL/MySQL, Wazuh SIEM) |
| **Sareko Inprimagailua 1** | Admin / Logistika | 192.168.10.55 | 255.255.255.0 | Estatikoa (IP Fija - Salbuetsia) |
| **Sareko Inprimagailua 2** | Admin / Logistika | 192.168.10.56 | 255.255.255.0 | Estatikoa (IP Fija - Salbuetsia) |
| **DHCP Salbuespen Tartea** | Erreserba / Inprimagailuak | 192.168.10.55 - .60 | 255.255.255.0 | DHCP Zerbitzarian baztertutako tartea (Ez Banatu) |
| **12 Bezero LAN Ekipoak** | Admin, Logistika eta IT | 192.168.10.50 - .54<br>192.168.10.61 - .150 | 255.255.255.0 | Dinamikoa (DHCP bidez banatutako IPak) |

---

## 6. URRUNEKO SARBIDE SEGURUKO AUKERAK (VPN)

### 6.1. Mekanismoen Ebaluazioa
* **RDP (192.168.10.1) zuzenean Internetera zabaltzea:** Baztertua[cite: 4]. Indar gordinaren eta Shodan bezalako bilatzaileen erasoen aurrean ahultasun kritikoa da[cite: 4].
* **SSH (192.168.10.2 / .3) ataka estandarrean uztea:** Baztertua[cite: 4]. Botnet-en etengabeko proben mende geratzen da[cite: 4].
* **VPN SSL/TLS (WireGuard / OpenVPN):** Aukeratua[cite: 4]. Muturrez muturreko tunel enkriptatua bermatzen du, ziurtagiri digital eta MFA autentifikazioarekin[cite: 4].

### 6.2. Inplementazio Politika
Perimetroko suebakian VPN zerbitzaria gaitzen da[cite: 4]:
* **Autentifikazio Geruzak:** Erabiltzaile bakoitzaren X.509 ziurtagiri digitala + Windows Server 2019ko domeinu-pasahitza + TOTP 2FA kodea[cite: 4].
* **Bideraketa eta Segurtasuna:** Etxetik lan egiten duten langileek edo IT kideek barne-sareko (10.8.0.0/24) baimendutako baliabideetara soilik sartzeko aukera izango dute, rolen araberako iragazketa ezarrita[cite: 4].

---

## 7. SEGURTASUN PERIMETRALA ETA SUEBAKIAREN ARAUAK

### 7.1. Suebaki Arkitektura
* **Perimetro Suebakia:** pfSense / OPNSense gailua, Interneteko WAN konexioaren eta barne-sarearen arteko mugan kokatua[cite: 4].
* **Ostalari Suebakiak (Host Firewalls):**
  * `ufw` modulu aktibatua Ubuntu Server 1 (192.168.10.2) eta Ubuntu Server 2 (192.168.10.3) zerbitzarietan[cite: 4].
  * Windows Defender Firewall GPO bidez kudeatua Windows Server 2019 (192.168.10.1) eta 12 bezero-ekipoetan[cite: 4].

---

### 7.2. Trafikoa Iragazteko Arauen Matrizea (Firewall Rules)

**Politika orokorra:** Eskatu gabeko trafiko guztiaren ukatze esplizitua (*Default Deny All*)[cite: 4].

| Zk. | Jatorria | Jatorrizko IPa | Helburua | Helburuko IPa | Ataka / Protokoloa | Ekintza | Justifikazioa / Zerbitzua |
| :---: | :--- | :--- | :--- | :--- | :--- | :---: | :--- |
| **1** | Internet (WAN) | * | Ubuntu Server 1 | 192.168.10.2 | TCP 80, 443 | **PASS** | Orbis atarirako web-trafiko publikoa (HTTP/HTTPS) |
| **2** | Ubuntu Server 1 | 192.168.10.2 | Ubuntu Server 2 | 192.168.10.3 | TCP 5432 / 3306 | **PASS** | Web aplikazioak datu-baseari egindako kontsultak |
| **3** | Lan-postuak (DHCP) | 192.168.10.50-150 | WinServer 2019 | 192.168.10.1 | UDP 53, 67, 68 | **PASS** | 12 ekipoentzako DNS eta DHCP zerbitzuak |
| **4** | Lan-postuak (DHCP) | 192.168.10.50-150 | WinServer 2019 | 192.168.10.1 | TCP 88, 389, 445 | **PASS** | Active Directory autentifikazioa (Kerberos, LDAP, SMB) |
| **5** | VPN Sarea | 10.8.0.0/24 | Zerbitzariak | 192.168.10.1 - .3 | TCP 22, 3389 | **PASS** | IT sailaren kudeaketa urrunetik MFA bidez |
| **6** | LAN Ekipoak | 192.168.10.50-150 | Inprimagailuak | 192.168.10.55 - .56 | TCP 9100, 631 | **PASS** | Lana inprimatzeko trafikoa IP finkoa duten gailuetara |
| **7** | Gonbidatu Wi-Fi | 192.168.40.0/24 | Internet / WAN | * | TCP 80, 443 | **PASS** | Nabigazio publikoa barne-saretik erabat isolatuta |
| **8** | Edonor | * | Edonor | * | ANY | **DENY** | Gainerako trafiko guztia ukatzea (*Default Deny*) |
