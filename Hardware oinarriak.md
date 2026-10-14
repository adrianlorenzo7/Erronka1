---
layout: page
title: "Hardware oinarriak"
---

# Hardware - Ekipoen Ezaugarri Teknikoak eta Aurrekontua

Proiektuak 3 zerbitzari (1 Windows Server + 2 Ubuntu Server) eta 12 lan-postu biltzen ditu (Informatikako 3 ekipo potente eta erabilera arrunteko 9 ekipo).

---

## AURKIBIDEA

1. [Ekipoen Ezaugarri Teknikoak eta Aurrekontua](#1-ekipoen-ezaugarri-teknikoak-eta-aurrekontua)
   - [Informatika Sailerako 3 Ekipo Potenteak](#1-informatika-sailerako-3-ekipo-potenteak-goi-mailakoak)
   - [Erabilera Normaleko 9 Ekipoak](#2-erabilera-normaleko-9-ekipoak-ofimatika--logistika)
   - [Zerbitzariak eta Azpiegitura](#3-zerbitzariak-eta-azpiegitura-3-zerbitzari--sarea)
   - [Aurrekontu Orokorra](#d-aurrekontu-orokorra-presupuesto-total-orbis)
2. [Ekipoak Manipulatzeko Beharrezko Tresnak](#2-ekipoak-manipulatzeko-beharrezko-tresnak)
3. [Softwarea eta Konfigurazioa](#3-softwarea-eta-konfigurazioa)
4. [Hondakinen Kudeaketa eta Ingurumena](#4-hondakinen-kudeaketa-eta-ingurumena)
5. [Planoaren Antolaketa, Seinaleak eta Edukiontziak](#5-planoaren-antolaketa-seinaleak-eta-edukiontziak)
6. [ORBIS Enpresaren Plano Zehatza](#orbis-enpresaren-plano-zehatza)

---

## 1. Ekipoen Ezaugarri Teknikoak eta Aurrekontua

### 1. Informatika Sailerako 3 Ekipo Potenteak (Goi-Mailakoak)
Ekipo hauek garapen-lanetarako, kode-konpilaziorako, birtualizaziorako eta zerbitzarien simulazioak egiteko diseinatuta daude[cite: 3].

* **PUZ (Prozesadorea):** Intel Core i7-14700K / AMD Ryzen 7 7800X3D (~400 €)[cite: 3]
  * *Zergatik?* 16+ nukleo eta 5.5 GHz-ko maiztasuna dituelako[cite: 3]. Kodea denbora errekorrean konpilatzeko eta Docker nahiz makina birtualak atzerapenik gabe exekutatzeko beharrezkoa da[cite: 3].
* **Oinarrizko plaka:** ATX Z790 / B650 (~200 €)[cite: 3]
  * *Zergatik?* DDR5 memoria, PCIe 4.0/5.0 abiadura eta ataka-kopuru zabala onartzen duelako goi-mailako osagaiak mugarik gabe ustiatzeko[cite: 3].
* **RAM Memoria:** 32 GB / 64 GB DDR5 6000 MHz (~160 €)[cite: 3]
  * *Zergatik?* Visual Studio, PyCharm, datu-base lokalak eta edukiontziak batera exekutatzeko[cite: 3]. DDR5 maiztasun altuak datu-fluxu arina bermatzen du[cite: 3].
* **HDD/SSD:** 2 TB NVMe PCIe 4.0 M.2 SSD (~140 €)[cite: 3]
  * *Zergatik?* 7000 MB/s-ko irakurketa/idazketa abiadura duelako[cite: 3]. Fitxategi handiak, proiektuak eta datu-baseak berehala kargatzen dira[cite: 3].
* **Txartel Grafikoa:** NVIDIA RTX 4070 12 GB GDDR6X (~550 €)[cite: 3]
  * *Zergatik?* Web-interfazearen errendatze grafikorako, adimen artifizialeko eredu lokalen probetarako eta GPU bidez azeleratutako kalkuluetarako[cite: 3].
* **Elikadura Iturria:** 850W 80 Plus Gold (~110 €)[cite: 3]
  * *Zergatik?* Kontsumo altuko osagaiak babesteko eta %90etik gorako eraginkortasun elektrikoa izateko (bero gutxiago sortuz eta elektrizitatea aurreztuz)[cite: 3].
* **Txasisa eta Disipazio Likidoa:** Mid-Tower ATX + AIO 240mm/360mm (~140 €)[cite: 3]
  * *Zergatik?* Prozesadorea karga maximoan tenperatura baxuan mantentzeko (thermal throttling saihesteko) eta lan-ingurune isila lortzeko[cite: 3].

**Prezioa ekipo bakoitzeko:** ~1.400 €  
**Guztira (3 ekipo):** 4.200 €[cite: 3]

---

### 2. Erabilera Normaleko 9 Ekipoak (Ofimatika / Logistika)
Logistika, stock-kudeaketa, fakturazioa eta bezeroen arretarako erabiliko diren lan-postuak[cite: 3].

* **PUZ (Prozesadorea):** Intel Core i5-13400 / AMD Ryzen 5 7600 (~180 €)[cite: 3]
  * *Zergatik?* 10 nukleo eta potentzia orekatua eskaintzen dituelako ERP/CRM kudeaketa-softwarea, Excel fitxategi handiak eta nabigatzailea batera erabilgarri izateko[cite: 3].
* **Oinarrizko plaka:** Micro-ATX B760 / B650 (~110 €)[cite: 3]
  * *Zergatik?* Ofimatikarako beharrezkoak diren konektore guztiak eskaintzen dituelako prezio egokituan[cite: 3].
* **RAM Memoria:** 16 GB DDR4/DDR5 3200/5200 MHz (~50 €)[cite: 3]
  * *Zergatik?* 16 GB dira gaur egun enpresa-mailako ofimatikarako estandarra; multitarea leuna bermatzen du sistema eragilea eta lan-programak batera irekitzean[cite: 3].
* **SSD:** 512 GB NVMe M.2 SSD (~45 €)[cite: 3]
  * *Zergatik?* Disko mekaniko zaharren (HDD) aldean 10 bider azkarragoa delako[cite: 3]. Windows 10/11 eta programak segundotan abiarazten dira[cite: 3].
* **Txartel Grafikoa:** Integratua / iGPU (0 €)[cite: 3]
  * *Zergatik?* Ofimatikarako eta web-kudeaketarako ez delako txartel dedikaturik behar[cite: 3]. Prezioa eta kontsumo elektrikoa nabarmen merkatzen ditu[cite: 3].
* **Elikadura Iturria:** 500W 80 Plus Bronze (~45 €)[cite: 3]
  * *Zergatik?* Kontsumo baxuko ekipoak direnez, 500W-eko iturri eraginkor batekin nahikoa delako modu seguruan elikatzeko[cite: 3].
* **Txasisa eta Aire Disipagailua:** Micro-ATX kaxa + Stock cooler (~40 €)[cite: 3]
  * *Zergatik?* Ekipo sinpleak eta konpaktuak direnez, kaxa estandar batekin eta aire bidezko disipagailu batekin tenperatura egokian mantentzen direlako[cite: 3].

**Prezioa ekipo bakoitzeko:** ~550 €  
**Guztira (9 ekipo):** 4.950 €[cite: 3]

---

### 3. Zerbitzariak eta Azpiegitura (3 Zerbitzari + Sarea)

* **1x Windows Server (Hardwarea + Lizentzia Standard) (~2.500 €):**[cite: 3]
  * **Hardwarea (~1.800 €):** Xeon/EPYC prozesadorea, 64 GB ECC RAM, 2x 1 TB NVMe SSD (RAID 1ean) eta elikadura-iturri erredundantea[cite: 3].
  * **Lizentzia (~700 €):** Windows Server 2022 Standard (16-core)[cite: 3].
  * *Zergatik?* Active Directory (dominioa), GPO direktibak, DHCP eta inprimagailuak zentralizatuta kudeatzeko[cite: 3]. ECC RAMak memoria-akatsak zuzentzen ditu eta RAID 1ak datuak babesten ditu disko bat hondatzen bada zerbitzua gelditu gabe[cite: 3].
* **2x Ubuntu Server (Web Frontend eta Backend/Datu-Basea) (~1.500 € / unitateko = 3.000 €):**[cite: 3]
  * **Hardwarea:** Xeon/EPYC prozesadorea, 32 GB ECC RAM, 1 TB NVMe SSD[cite: 3].
  * *Zergatik?* Linux sistema eragile arina, oso segurua eta doakoa delako (lizentzia-kosturik gabe)[cite: 3].
  * **1. Zerbitzaria (Frontend):** Nginx bidez bezeroen eskaerak kudeatzeko[cite: 3].
  * **2. Zerbitzaria (Backend):** PostgreSQL/MySQL eta Docker bidez stock-a eta datu-basea isolatuta kudeatzeko[cite: 3].

---

### D. Aurrekontu Orokorra (Presupuesto Total Orbis)

| Kontzeptua / Osagaia | Unitateak | Prezioa / Unitateko | Guztira (€) |
| :--- | :---: | :---: | :---: |
| Informatikako Ekipoak (Goi-mailakoak) | 3 | 1.400 € | 4.200 € |
| Erabilera Normaleko Ekipoak | 9 | 550 € | 4.950 € |
| Windows Server (Hardwarea + Lizentzia) | 1 | 2.500 € | 2.500 € |
| Ubuntu Servers (Web + Datu-basea) | 2 | 1.500 € | 3.000 € |
| Sarea eta Azpiegitura (Rack, Switch Gigabit 24-Port, Kableak, Inprimagailua) | 1 | 1.350 € | 1.350 € |
| **GUZTIRA (BEZ gabe / Sin IVA)** | | | **16.000 €** |
| **GUZTIRA BEZarekin (%21 IVA)** | | | **19.360 €** |

---

## 2. Ekipoak Manipulatzeko Beharrezko Tresnak

Lantegian edo muntaia-eremuan segurtasunez lan egiteko lanabes hauek erabiliko dira[cite: 3]:

* **Bihurkina (Destornillador):** Mutur magnetikodun bihurgailu-jokoa (PH1, PH2 eta buru lauak) osagaiak eta torlojuak erraz muntatzeko[cite: 3].
* **Pintzak:** Precisioko pintza antiestatikoak konektore txikiak edo torlojuak leku zorrotzetan kokatzeko[cite: 3].
* **Eskumuturrekoa (Pulsera Antiestática):** Lurrera konektatutako eskumuturreko antiestatiko, osagai elektronikoak deskarga elektrostatikoetatik babesteko[cite: 3].
* **Beste lanabes batzuk:** Kable-brida plastikoak kableak ordenatzeko, elikadura-iturrien probagailua eta pasta termikoa isolatzailearekin[cite: 3].

---

## 3. Softwarea eta Konfigurazioa

* **Sistemak:** Windows Server (Dominioa, Active Directory, GPO), Ubuntu Server (Web eta Datu-base zerbitzuak) eta Windows 10/11 Pro bezeroen 12 ekipoetan[cite: 3].
* **Konfigurazioa:** Antolaketa Unitateak (Informatika, Logistika, Zuzendaritza), Talde Politikoak (GPO), karpeta partekatuen baimenak eta inprimagailuen hedapen automatikoa sarean[cite: 3].

---

## 4. Hondakinen Kudeaketa eta Ingurumena

* **Hondakinen Sailkapena:** RAEE hondakinak (Gailu Elektriko eta Elektronikoen Hondakinak), plastikoak, kartoiak eta pilak bereiztea[cite: 3].
* **Kudeatzaile Baimenduak:** Osagai zaharkitu edo hondatuekin birziklapen-prozesua bermatzeko kudeatzaile baimenduekin lan egitea (adibidez, Indumetal Recycling edo tokiko birziklapen-zentroak)[cite: 3].

---

## 5. Planoaren Antolaketa, Seinaleak eta Edukiontziak

Planoa egitean atal hauek kokatuko dira[cite: 3]:

### Eremuen Kokapena
* **CPD / RACK Armairua:** 3 zerbitzariak (1 Windows Server + 2 Ubuntu) eta sareko gailuak (switches, bideratzailea)[cite: 3].
* **Informatika Saila:** Goi-mailako 3 ekipoak kokatuta dauden mahaia[cite: 3].
* **Administrazioa / Logistika:** Erabilera arrunteko 9 ekipoak kokatutako eremua[cite: 3].

### Edukiontziak Planoan
* **RAEE Edukiontzia (Gorria/Específico):** Osagai elektroniko hautsientzat (plakak, memoria-moduluak, kableak)[cite: 3].
* **Edukiontzi Urdina:** Kartoizko kaxa eta bilgarrientzat[cite: 3].
* **Edukiontzi Horia:** Plastiko eta babesgarrientzat[cite: 3].

### Segurtasun Seinaleak
* **Arrisku Elektrikoa:** RACK armairuan eta koadro elektriko nagusian[cite: 3].
* **Eskumuturreko Antiestatikoaren Erabilera Derrigorrezkoa:** Muntaia edo konponketa mahai gainean[cite: 3].
* **Larrialdietako Irteerak eta CO2 Extintoreak:** Sute elektrikoetarako egokiak[cite: 3].

---

## ORBIS ENPRESAREN PLANO ZEHATZA

![Hardware 1](./img/HARDWARE%201.png)
