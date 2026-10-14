---
layout: page
title: "Sareko zerbitzuak eta internet"
---
### Windows Server-en DHCP Esparru Berria Kureatzea

Gure sareko gailuei IP helbideak automatikoki esleitzeko, urrats hauek eman ditugu Windows Server-eko DHCP zerbitzarian:

1. **DHCP Kudeatzailea ireki dugu:** ORBIS.lan` domeinuko zerbitzarian IPv4 atalean sartu eta esparru berri bat (*Ámbito Nuevo*) sortu dugu.
2. **Esparruaren Izena definitu dugu:** Lehen urratsean **`Langileak`** izena jarri diogu esparruari, sare-tarte hau enpresako langileen gailuetara eta ordenagailuetara bideratuta egongo dela identifikatzeko.

![SEA 6](./img/SEA6.png)

### IP Helbideen Barrutiaren Konfigurazioa

Windows Server-eko DHCP zerbitzarian esparru berria (*Ámbito*) sortzen jarraituz, urrats hau burutu dugu:

1. **IP Tartea eta Maskara ezarri ditugu:** Langileen gailuei esleituko zaien IP helbideen tartea definitu dugu:
   - **Hasierako IP-a:** `192.168.10.50`
   - **Amaierako IP-a:** `192.168.10.150`
   - **Luzera eta Azpisare-maskara:** `24` eta `255.255.255.0`.
2. **Helburua:** Tarte honek bermatzen du sarean konektatzen diren bezeroek automatikoki IP helbide bat jasoko dutela `192.168.10.50` eta `192.168.10.150` artean.

![SEA 7](./img/SEA7.png)

### IP Salbuespenak Konfiguratzea

DHCP esparruaren konfigurazioarekin jarraituz, helbide batzuk banaketatik kanpo uztea erabaki dugu:

1. **IP Salbuespena gehitzea:** Aurretik definitutako tarte orokorren barruan (`192.168.10.50` - `192.168.10.150`), `192.168.10.55` helbidetik `192.168.10.60` helbiderainoko tartea salbuespen gisa erregistratu dugu.


![SEA 8](./img/SEA8.png)

### IP Lagapenaren Denbora-Muga Konfiguratzea 

DHCP esparruaren konfigurazioarekin aurrera jarraituz, helbide bakoitzaren alokairu-denbora zehaztu dugu:

1. **Lagapen-denbora ezartzea:** Urrats honetan, bezero bati IP helbide bat gordeta mantenduko zaion denbora-muga **30 egunetan** utzi dugu.

![SEA 9](./img/SEA9.png)

### Ate Lehenetsiaren Konfigurazioa (Enrutador - Puerta de enlace predeterminada)

DHCP-arekin jarraituz, bezeroei helbide honekin batera bidaliko zaien bideratzailea zehaztu dugu:

1. **Gateway edo Ate Lehenetsia gehitu dugu:** Urrats honetan, sareko bideratzailearen IP helbidea erregistratu dugu (**`192.168.10.254`**).


![SZ 1](./img/SZ1.png)

### DHCP Maileguen Egiaztapena eta Kontrola 

Windows Server-eko DHCP zerbitzariaren konfigurazioa amaituta, maileguen egoera egiaztatu dugu:

1. **Maileguen zerrenda aztertu dugu:** DHCP administratzailean **Concesiones de direcciones** atalean sartu gara. Bertan, sarean aktibo dauden IP helbideen zerrenda ikusten dugu (adibidez, `192.168.10.50`-tik aurrera), bezero bakoitzaren izenarekin (`jitsi.orbis.eus`, `cupsubuntu.orbis.lan`, `Win11_8.orbis.lan`, etab.).

![SZ 2](./img/SZ2.png)

### DHCP Erreserbaren Sorkuntza 

Windows Server-eko DHCP zerbitzarian gailu zehatz bati IP finkoa esleitzeko, urrats hau burutu dugu:

1. **Erreserben atala kudeatu dugu:** DHCP kudeatzailean **Reservas** atalean sartu eta erreserba berri bat sortu dugu. Bertan ikusten denez, **`[192.168.10.77] Bezero`** izeneko erreserba konfiguratu dugu.


![SZ 3](./img/SZ3.png)

### DHCP Esparru-Aukeren Konfigurazioa (Opciones de ámbito)

Windows Server-eko DHCP zerbitzarian `Langileak` esparruari dagozkion aukera nagusiak ezarri ditugu bezeroek sare-konfigurazio osoa jaso dezaten:

1. **Esparru-aukerak (*Opciones de ámbito*) aztertu eta konfiguratu ditugu:**
   - `192.168.10.254` helbidea ezarri dugu ate lehenetsi (Gateway) gisa, sareko trafikoa kanpora bideratzeko.
   - `192.168.10.1` helbidea definitu dugu gure sareko DNS zerbitzari nagusi gisa, domeinu-izenak ebazteko.
   - `orbis.lan` domeinu-izena esleitu dugu, sare barruko gailu guztiek domeinu beraren babespean lan egin dezaten.

![SZ 4](./img/SZ4.png)

### DNS Zuzeneko Bilaketa Zonaldearen Konfigurazioa (orbis.eus)

Windows Server-eko DNS Kudeatzailean (*Administrador de DNS*), gure `orbis.eus` zuzeneko bilaketa-zonan gure zerbitzu nagusien erregistroak (Host A) konfiguratu ditugu:

1. **Host (A) Erregistroak sortu ditugu:**
   - **`cups` (`192.168.10.3`):** Inprimatze-zerbitzari nagusiaren helbidea lotu dugu.
   - **`glpi` (`192.168.10.2`):** Kudeaketa-sistemaren IP helbidea esleitu dugu.
   - **`jitsi` (`192.168.10.2`):** Bideokonferentzia-zerbitzuaren helbide IPa bideratu dugu.
   - **`wordpress` (`192.168.10.3`):** Web atariaren zerbitzariaren helbide IPa lotu dugu.

![SZ 5](./img/SZ5.png)

![SZ 6](./img/SZ6.png)

### DNS Alderantzizko Bilaketa Zonaldearen Konfigurazioa (10.168.192.in-addr.arpa)

1. **Erregistroak sortu ditugu:**
   - **`192.168.10.2`  `glpi.orbis.eus.`:** IP helbide hau GLPI zerbitzuaren izenarekin lotu dugu.
   - **`192.168.10.2`  `jitsi.orbis.eus.`:** IP bera Jitsi bideokonferentzia zerbitzuarekin lotu dugu.
   - **`192.168.10.3`  `cups.orbis.eus.`:** IP helbide hau inprimatze-zerbitzariaren izenarekin lotu dugu.


![SZ 7](./img/SZ7.png)

### DNS Baldintzapeko Birbideratzaileen Konfigurazioa 

Windows Server-eko DNS Kudeatzailean (*Administrador de DNS*), **`google`** izeneko baldintzapeko birbideratzailea ezarri dugu:

1. **Birbideratzailea eta IPa definitu ditugu:**
   - Baldintzapeko birbideratze atalean **`google`** araua sortu eta kanpoko DNS zerbitzari publiko baten IP helbidea (**`8.8.8.8`**) esleitu diogu.

![SZ 8](./img/SZ8.png)

### Jitsi Meet Bideokonferentzia Zerbitzuaren Funtzionamendu Egiaztapena

Gure azpiegituran Jitsi bideokonferentzia-zerbitzaria konfiguratu ondorerik, zerbitzuaren proba praktikoa burutu dugu:

1. **Bideokonferentzia-gelan sartu eta komunikazioa egiaztatu dugu:**
   - **Gela sortzea:** `Orbis` izeneko bilerara konektatu gara.
   - **Erabiltzaileen interakzioa eta Txata:** Argazkian ikusten denez, bi parte-hartzaile sartu dira bilerara. Barne-txataren bidez elkarrizketa probatu dugu.


![SZ 8](./img/SZ9.png)
