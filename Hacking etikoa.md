---
layout: page
title: "Hacking etikoa"
---
# HACKING

**SISA3-2 2026-2027**  
**Erronka1 - 4.taldea**

---

## AURKIBIDEA

1. [GURE ENPRESA-SARRERAKO PENTESTING BATEN SAREAK](#gure-enpresa-sarrerako-pentesting-baten-sareak)
   - [1. PLANGINTZA ETA INFORMAZIO-BILAKETA](#1-plangintza-eta-informazio-bilaketa)
   - [2. AHULGUNEEN AZTERKETA ETA ESKANEATZEA](#2-ahulguneen-azterketa-eta-eskaneatzea)
   - [3. USTIAPENA](#3-ustiapena)
   - [4. USTIAPEN OSTEKO FASEA ETA MUGIMENDU LATERALA](#4-ustiapen-osteko-fasea-eta-mugimendu-laterala)
   - [5. TXOSTENKETA ETA KONPONBIDE-GOMENDIOAK](#5-txostenketa-eta-konponbide-gomendioak)
2. [ORBIS ENPRESAREN AHULEZIAK ETA JASO DITZAKEEN ERASOAK](#orbis-enpresaren-ahuleziak-eta-jaso-ditzakeen-erasoak)
   - [1. AHULGUNE TEKNIKOAK](#1-ahulgune-teknikoak-webgunea-eta-aplikazioak)
   - [2. NEGOZIO LOGIKAREN AKATSAK](#2-negozio-logikaren-akatsak)
   - [3. KOMUNIKAZIOEN ETA ZERBITZU PRIBATUEN AHULGUNEAK](#3-komunikazioen-eta-zerbitzu-pribatuen-ahuleziak)
   - [4. GIZA FAKTOREA](#4-giza-faktorea)
3. [KAPTURA PANTAILAK](#kaptura-pantailak)
4. [ZAURGARRITASUNAK](#zaurgarritasunak)

---

## GURE ENPRESA-SARRERAKO PENTESTING BATEN SAREAK

### 1. PLANGINTZA ETA INFORMAZIO-BILAKETA
* **Helburua:** Fase honetan, benetako eraso bat hasi aurretik, "ikerketa" edo "espioitza" lana egiten da. Helburua da enpresari buruz ahalik eta datu gehien lortzea, inor konturatu gabe eta sistemetan kalterik eragin gabe.  
  Adibidez, Interneten begiratzen da enpresak zein zerbitzari edo helbide dituen (DNS bidez), sare sozialetan langileak bilatzen dira gero haiei iruzur egiteko mezuak bidali ahal izateko (phishing), edo programatzaileek akats batez interneten (GitHub bezalako lekuetan) argitaratu dituzten enpresako pasahitz edo kode sekretuen bila ibiltzen dira. 
* **Adibidea:** Pentesters-ek edo zibersegurtasuneko adituek ikertzen dute ea Orbis-en garatzaileek nahigabe utzi duten API baten gako sekretua (tokena) edo pasahitz bat GitHub-en biltegi publiko batean. Gainera, Orbis-en aplikazio mugikorren bertsio zaharrak edo langileen profilak aztertzen dituzte sare sozialetan (adibidez, LinkedIn-en), geroago langileei iruzur egiteko mezuak (phishing) bidali ahal izateko ateak bilatzeko. 

### 2. AHULGUNEEN AZTERKETA ETA ESKANEATZEA
* **Helburua:** Fase honetan, programa edo tresna automatizatu bereziak erabiltzen dira enpresaren webgunean, aplikazioetan eta zerbitzuetan akatsak, portu irekiak edo software zaharkitua modu aktiboan bilatzeko. E-commerce (Amazon estiloko) enpresa bat garenez, gure denda digitalaren eta APIen segurtasuna aztertzea ezinbestekoa da. 
* **Adibidea:** Tresna teknikoak erabiliz, Orbis-en web-plataformaren eta bezeroen arreta-zerbitzurako atariaren eskaneatzea egiten da. Horri esker, ikusten da bezeroen ordainketak kudeatzen dituen APIaren bertsio batek segurtasun-akats ezagun bat duela, sarrerako datuak gaizki balioztatzen direlako. 

### 3. USTIAPENA
* **Helburua:** Hirugarren fasean, behin ahulgune bat aurkituta, benetako erasoa simulatzen da haren ustiapena egiaztatzeko. Helburua da sistemaren segurtasun-hesi pertsonalak gainditzea eta sarbide baimenik gabea lortzea.
* **Adibidea:** Aurkitutako akatsaz baliatuta, adituek eskaera baten parametroak manipulatzen dituzte. Horrela, lortzen dute produktuen prezioak aldatzea edo beste bezero baten kontuko datu pertsonaletara baimenik gabe sartzea.

### 4. USTIAPEN OSTEKO FASEA ETA MUGIMENDU LATERALA
* **Helburua:** Fase honetan, behin sistema batean sartzea lortzen denean, benetako arriskua zein handia den neurtzen da: hau da, zerbitzari horretatik abiatuta enpresaren hodeiko beste sistema batzuetara edo barne-sare osora iritsi eta dena hondatu daitekeen ikusteko.
* **Adibidea:** Web zerbitzari ahul horretatik barnera sartuta, adituek "salto" egiten dute enpresaren barne-sarean zehar, Orbis-ek bezeroen kreditu-txartelak gordetzen dituen hodeiko datu-base zentralera iritsi arte. Gainera, administratzaile nagusi baten pasahitza lapurtzea lortzen dute, eta horrek enpresa osoaren kontrol osoa emango lieke. 

### 5. TXOSTENKETA ETA KONPONBIDE-GOMENDIOAK
* **Helburua:** Prozesu osoa idatziz jaso eta dokumentatzen da (teknikoki zein zuzendaritzarako), aurkitutako arazo bakoitza zein larria den sailkatzeko (kritikoa, larria edo moderatua) eta hauek nola konpondu behar diren azalduz. 
* **Adibidea:** Orbis-en buruzagiei eta programatzaileei txosten argi bat entregatzen zaie. Bertan erakusten zaie nola lortu zuten bezeroen datuetara iristea, eta gomendatzen zaie premiazko adabakiak (patches) eta segurtasun-neurri gogorragoak jartzea etorkizunean eraso errealik ez jasateko.

---

## ORBIS ENPRESAREN AHULEZIAK ETA JASO DITZAKEEN ERASOAK

Proiektu honetan, hainbat ahulgune identifikatu dira, eta horiek eraso mota desberdinak jasotzeko arriskua dakartate: 

### 1. AHULGUNE TEKNIKOAK (Webgunea eta Aplikazioak)
* **Ahulezia:** Sarrerako datuen balidazio eskasa bezeroen erregistroan, bilatzaileetan edo erosketa-formularioetan. 
* **Jaso dezaketen erasoa:** Erasotzaile batek datu-baseko kontsultak aldatzea lortzen du, informazio konfidentziala (erabiltzaileen pasahitzak eta datu pertsonalak) lapurtzeko. 

### 2. NEGOZIO LOGIKAREN AKATSAK
* **Ahulezia:** Pasarela ordainketen eta saskiaren logikaren kontrol eza bezeroek bezeroaren aldetik bidalitako parametroetan fidatzeagatik. 
* **Jaso dezaketen erasoa:** Bezero batek bere saskian dauden produktuen prezioak edo kantitateak eskuz manipulatzea lor dezake, produktu garestiak ia doan erosteko. 

### 3. KOMUNIKAZIOEN ETA ZERBITZU PRIBATUEN AHULEZIAK
* **Ahulezia:** Barneko bilerak eta bideokonferentziak egiteko erabiltzen den zerbitzariaren (adibidez, Jitsi zerbitzariaren) konfigurazio okerrak edo enkripzio faltak sare lokaletik kanpo. 
* **Jaso dezaketen erasoa:** Erasotzaile batek zuzendaritzaren arteko bilera sekretuak edo barne-komunikazioak atzematea lor dezake. 

### 4. GIZA FAKTOREA
* **Ahulezia:** Langileek edo bezeroek zibersegurtasuneko ezagutza urriak izatea eduki maltzurrak hautemateko. 
* **Jaso dezaketen erasoa:** Langileei edo administratzaileei zuzendutako mezu elektroniko faltsuak bidaltzen zaizkie, enpresaren sarbide-kredentzialak (pasahitzak) edo banku-datuak lapurtzeko asmoz. 

---

## KAPTURA PANTAILAK

![HACKING1](./img/HACKING1.png)
*Figura 1: Metasploitable interfazearen eta IP helbidearen konfigurazioa.*

![HACKING2](img/HACKING2.png)
*Figura 2: Kali Linux eth0 interfazearen eta IP helbidearen konfigurazioa.*

![HACKING3](img/HACKING3.png)
*Figura 3: Kali Linux-etik Metasploitable-rako ping proba.*

![HACKING4](img/HACKING4.png)
*Figura 4: Nmap-en bidezko portu eta zerbitzuen analisia.*

![HACKING5](img/HACKING5.png)
*Figura 5: Nmap vulnet gidoien bidezko ahultasun analisia (vsftpd backdoor).*

![HACKING6](img/HACKING6.png)
*Figura 6: HTTP eta RMI zerbitzuen zaurgarritasun analisia.*

![HACKING7](img/HACKING7.png)
*Figura 7: Slowloris DoS eta CSRF ahultasunen analisia.*

![HACKING8](img/HACKING8.png)
*Figura 8: Bide publikoen eta direktorioen analisia (http-enum).*

---

## ZAURGARRITASUNAK

### 1. SSH Zaurgarritasuna
* **ZAURGARRITASUNA:** SSH-ren zaurgarritasun bat `CVE-2008-5161` da.
* **BERTSIOA:** OpenSSH 4.7p1 bertsioari kaltetzen dio. 
* **ARAZOA:** Hurruneko erasotzaile batek sarea oso ondo kontrolatzen badu eta saioa zehatz-mehatz ezagutzen badu, zifratutako datuetatik zati txiki bat irakur lezake.
* **ZER ZERBITZURI AFEKTATU ETA NOLA ERAGIN:** SSH zerbitzuari eragiten dio (zehazki, OpenSSH 4.7p1 bertsioari). Nahiz eta datuak kode bidez babestuta (zifratuta) egon, sekretu edo informazio puska batzuk ezagutzea lortu dezake, eta horrek zifratutako konexioaren segurtasuna eta pribatutasuna kaltetzen ditu.

### 2. Samba Zaurgarritasuna
* **ZAURGARRITASUNA:** Samba-ren zaurgarritasun bat `CVE-2014-3560` da. 
* **BERTSIOA:** Samba 4.0.21 baino lehenagoko 4.0.x bertsioetan eta 4.1.11 baino lehenagoko 4.1.x bertsioetan.
* **ARAZOA:** Datu gehiegi sartzen ziren, eta soberakinak inguruko memoria hondatzen zuen. Erasotzaile batek horretaz aprobetxatu zezakeen bere kodea sartzeko eta programari hura exekutarazteko. 
* **ZER ZERBITZURI AFEKTATU ETA NOLA ERAGIN:** Samba zerbitzuari eragiten dio (Samba 4.0.21 baino lehenagoko 4.0.x bertsioetan eta 4.1.11 baino lehenagoko 4.1.x bertsioetan). Datuak gehiegi betetzean memoria puskatu egiten da, eta erasotzaileak hutsune hori aprobetxatzen du bere kodea sartu eta ordenagailuaren kontrola bereganatzeko. 

### 3. NetKit Zaurgarritasuna
* **ZAURGARRITASUNA:** NetKit-eko zaurgarritasun bat `CVE-2019-7282` da.
* **BERTSIOA:** NetKit 0.17-rarteko bertsioari kaltetzen dio.
* **ARAZOA:** NetKit-en rcp komandoak ez du egiaztatzen zerbitzariak bidaltzen dion fitxategiaren izena. Zerbitzari gaizto batek puntu bat (`.`) edo izen hutsa bidaltzen badu, zure karpetaren baimenak alda ditzake. 
* **ZER ZERBITZUARI AFEKTATU ETA NOLA ERAGIN:** NetKit-eko rcp komandoari eragiten dio. Zerbitzari kaltegarri batek izen bitxi bat bidaltzen dionean, sistemak ez du ondo begiratzen nondik datorren eta fitxategiaren izena ez du egiaztatzen. Horrek bidea ematen dio zerbitzari horri zure karpetaren sarrera-baimenak nahi bezala aldatzeko, segurtasuna hautsiz.

### 4. MySQL Zaurgarritasuna
* **ZAURGARRITASUNA:** MySQL-eko zaurgarritasun bat `CVE-2008-4097` da.
* **BERTSIOA:** MySQL 5.0.51 bertsioari eragiten dio.
* **ARAZOA:** MySQL-k ez du ondo egiaztatzen taula bat non gordeko den. Erabiltzaile batek lasterbide bat (symlink) erabil dezake MySQL-ren karpeta babestuetara iristeko, eta horrela baimenik ez duen lekuan idatzi. 
* **ZER ZERBITZURI AFEKTATU ETA NOLA ERAGIN:** MySQL zerbitzuari eragiten dio (zehazki, MySQL 5.0.51 bertsioari). Erabiltzaile batek lasterbide bat (symlink) erabil dezake MySQL-ren karpeta babestuetara iristeko, eta horrela, normalean baimenik ez duen leku batean idatzi edo datuak gorde ditzake.
