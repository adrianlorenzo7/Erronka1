---
layout: page
title: "Datu Baseak kudeatzeko administrazioa"
---

## 1. DATUEN ANALISIA

Orbis dendak bi motor desberdin elkartzen ditu bere datuak gordetzeko; batzuk erlazionalak dira eta besteak ez-erlazionalak, bakoitzari zerbitzu onena emateko. 

### 1.1. DATU ERLAZIONALAK
Egituratutako informazioa, erosketa-salmenten erregistroak, produktuen katalogoa eta barne-kudeaketa gordetzen ditu:

- **Produktuen Katalogoa:** Produktuaren identifikatzailea, marka, modeloa, fabrikazio-urtea, kolorea eta salmenta-prezioa.
- **Ordainketak:** Ordaindutako azken prezioa, aukeratutako ordainketa-metodoa, bezeroaren NAN/NIFa, telefono zenbakia eta bidalketarako helbide fisikoa.
- **Langileen Fitxak:** Barneko identifikazio-zenbakia, esleitutako lan-txandak, NANa, telefono korporatiboa eta helbide pertsonala.

### 1.2. DATU EZ-ERLAZIONALAK
Egituratu gabeko informazioa eta bolumen handiko dokumentuak kudeatzen ditu, atariaren erantzun-denbora optimizatzeko:

- **Eduki Multimedia:** Produktuen ezaugarriak eta funtzionamendua erakusteko kalitate altuko argazkiak zein azalpen-bideoak.
- **Bezeroen Iritziak eta Feedbacka:** Emandako balorazioak, idatzizko iritziak, kexak eta iradokizunak.

---

Hau jakinda, bi datu-base desberdin erabiliko ditugu:
1. **MySQL** → datu erlazionalak kudeatzeko.
2. **MongoDB** → datu ez-erlazionalak kudeatzeko.

---

## AUKERAKETAREN ALDE ONAK ETA TXARRAK

### MySQL (Datu erlazionalak)
* **Alde onak:**
  - Datuak oso ondo zaintzen eta babesten ditu. Akatsik egon ez dadin, informazio guztia seguru eta ondo lotuta gordetzen du beti.
  - Oso egokia da produktuak, langileen datuak eta erosketen erregistroak tauletan ondo antolatuta gordetzeko.
  - SQL lengoaia oso erabilia da, eta arazoren bat izanez gero informazio edo laguntza pila bat aurki daiteke interneten.
* **Alde txarrak:**
  - Datu-kopurua izugarri handitzen denean, zerbitzari bakarrean kudeatzea zailagoa eta astunagoa bihurtzen da.
  - Taula batzuetan eremu berri bat sartu nahi baduzu, aldez aurretik egitura osoa ondo pentsatu behar da; bestela, dena apurtu daiteke.
  - Ez da egokia irudi edo bideo handiak gordetzeko; horrelakoetan asko moteltzen da.

### MongoDB (Datu ez-erlazionalak)
* **Alde onak:**
  - Ez du taula edo zutabe zurrunik behar; nahi duzun informazioa zuzenean gorde dezakezu itxura asko aldatu gabe.
  - Oso azkarra da gure dendako produktuen irudiak, bideoak eta bezeroen iritziak gordetzeko eta erakusteko.
  - Datu asko pilatzen direnean, oso erraz zabaltzen eta handitzen da zerbitzari gehiagoren artean.
* **Alde txarrak:**
  - Ez da egokia taula edo dokumentu desberdinetako datuak elkarrekin nahasteko; ez ditu SQL-ko lotura konplexuak erabiltzen.
  - Ondo eta azkar ibiltzeko, ordenagailuak edo zerbitzariak RAM memoria gehiago behar du.
  - Ordainketa garrantzitsuak egiteko, ez da MySQL bezain fidagarria eta segurua.

---

## HARDWARE-ESKAKIZUNAK ETA BALIABIDE EKONOMIKOAK

- **Hardware-eskakizun estimatuak (Orbis ekoizpen-ingurunea):**
  - *MariaDB zerbitzaria:* 4 vCPU, 16 GB RAM, 200 GB NVMe SSD (gutxienekoa: 2 vCPU, 4 GB RAM).
  - *MongoDB zerbitzaria:* 4 vCPU, 16 GB RAM, 300 GB NVMe SSD (gutxienekoa: 2 vCPU, 4 GB RAM).

- **Baliabide ekonomikoak:**
  - *Software-lizentziak:* 0 € (MariaDB GNU GPL v2 lizentziapean eta MongoDB Community Edition SSPL lizentziapean).
  - *Hodei-azpiegitura (zerbitzari dedikatu edo VPS 2):* hilean 90-140 € inguru.
  - *Babeskopia automatizatuak:* hilean 20 € inguru.

---

## 2. DEPARTAMENTUEN ARABERAKO BAIMEN-EGITURA ETA SARBIDE-KONTROLA

Orbis lau departamentu nagusitan banatuta dago (IT/Teknologia, Administrazioa, Bezeroen Arreta eta Biltegia/Logistika). Informazioaren segurtasuna eta osotasuna zaintzeko, sarbide-kontrola zehatz-mehatz hierarkizatu da:

| Departamentua | Datuak Aldatzeko Baimena | Datuak Ikusteko Baimena | Rol Teknikoa Orbis Plataforman |
| :--- | :---: | :---: | :--- |
| **IT (Teknologia)** | Bai | Bai | Kudeaketa tekniko osoa, mantentze-lanak eta sistemaren garapena. |
| **Administrazioa** | Ez | Bai | Ordainketen auditoria, fakturazioa eta erregistroen egiaztapena. |
| **Bezeroen Arreta** | Ez | Ez | Ez du sarbide zuzenik datu-basearen taula nagusietara. |
| **Biltegia / Logistika** | Ez | Ez | Ez du sarbide zuzenik datu-basearen taula nagusietara. |

> *Zerbitzari-mailan, Admin erabiltzaile nagusiak pribilegio osoak (kontsulta, aldaketa eta ezabatzea) ditu datu-basearen egitura osoaren gainean.*

---

## 3. DATU-BASEEN ZERBITZARIEN KONFIGURAZIO TEKNIKOA

### A. MySQL Zerbitzaria (Erlazionala)
- **Kudeaketa eta Kokapena:** XAMPP ingurunearen bidez instalatuta `C:\xampp\mysql\bin` bidean eta phpMyAdmin panelaren bidez kudeatuta `localhost/phpmyadmin` helbidean.

---

![Captura de pantalla de la copia de seguridad](./img/DB1.png)

- **Sare-Konexioa:** 3306 ataka lehenetsian entzuten du (`127.0.0.1:3306`) eta socket fitxategia `C:/xampp/mysql/mysql.sock` helbidean ezarrita dago.

![Captura de pantalla de la copia de seguridad](./img/DB2.png)

 
### 4. MariaDB Erabiltzaileen Sorkuntza eta Baimenak (Kapturak)

#### Lehenengo Kaptura (Administratzailearen sorkuntza)
Irudi honetan MariaDB kontsolan sartzen gara root erabiltzaile gisa, eta **`admin_orbis`** administratzaile berria sortzen dugu[cite: 16]:

![Captura de pantalla de la copia de seguridad](./img/DB3.png)

#### Bigarren Kaptura (Langilearen sorkuntza eta amaiera)
Irudi honetan **`langile_orbis`** erabiltzailea sortzen dugu eta baimen mugatuak esleitzen dizkiogu, baita saioa amaitu ere[cite: 16]:

![Captura de pantalla de la copia de seguridad](./img/DB4.png)

#### MongoDB Administratzailearen Sorkuntza
Irudi honetan MongoDB-ko kudeaketa-kontsolan **`AdminOrbis`** administratzaile nagusia sortzen dugu:

![Captura de pantalla de la copia de seguridad](./img/DB5.png)

#### MongoDB Langile Erabiltzailearen Sorkuntza
Irudi honetan MongoDB-n **`LangileOrbis`** langile-erabiltzailea sortzen dugu `orbis_denda` datu-base zehatzerako[cite: 14]:

![Captura de pantalla de la copia de seguridad](./img/BK1.png)

#### MariaDB Datu-Basearen, Taularen eta Datuen Sorkuntza
Irudi honetan MariaDB kontsolan `orbis_db` datu-basea sortu, haren egitura definitu eta lehenengo datuak sartzen dugu[cite: 15]:

![Captura de pantalla de la copia de seguridad](./img/BK2.png)

#### MongoDB Compass Erabilera (Interfaze Grafikoa)
Irudi honetan **MongoDB Compass** interfaze grafikoa erabiltzen ari gara `orbis_denda` datu-basearen eta `productos` bildumaren edukiak ikusteko eta kudeatzeko:

- **Konexioa eta nabigazioa (`localhost:27017`):** Ezkerreko panelean tokiko zerbitzariarekin egindako konexioa ikusten da, eta bertan `orbis_denda` datu-basearen barruan `productos` bilduma hautatuta dago[cite: 16].


![Captura de pantalla de la copia de seguridad](./img/BK3.png)

#### MongoDB Datuak Esportatzea (Export Data)
Irudi honetan MongoDB Compass bidez `orbis_denda.productos` bildumako datuak fitxategi batera esportatzeko prozesua erakusten da, eta berriro database berri batean inportatzea.


![Captura de pantalla de la copia de seguridad](./img/BK4.png)

![Captura de pantalla de la copia de seguridad](./img/BK5.png)


