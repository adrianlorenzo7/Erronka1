---
layout: page
title: "Sistema eragileak administratzea"
---

# Sarearen IPv4 Konfigurazioa

Windows Server sisteman, **Ethernet 0** sare-txarteleko IPv4 ezarpenak eskuz konfiguratzen ari gara, IP helbide estatiko bat ezartzeko[cite: 1].

### Konfigurazio datuak:
* **IP helbidea:** `192.168.10.1
* **Azpisare-maskara:** `255.255.255
* **Atebide lehenetsia (Gateway):** `192.168.10.254
* **DNS zerbitzari nagusia:** `192.168.10.1

Zerbitzariari IP finko bat ezartzen ari gatzaizkio sarean beti helbide bera izan dezan.
![SEA 1](./img/SEA1.png)

# Ekiporaren Izena eta Lan-Taldea Konfiguratzea

Windows Server sisteman, zerbitzariaren izena (hostname) eta lan-taldea konfiguratzen ari gara.

### Konfigurazio datuak:
* **Ekiporaren izena:** `ORBIS_WINDOWS
* **Lan-taldea (Grupo de trabajo):** `WORKGROUP

Zerbitzariari izen propio bat ezartzen ari gatzaizkio sarean erraz identifikatu ahal izateko.
![SEA 2](./img/SEA2.png)

# Zerbitzariaren Rolak Hautatzea

Windows Server sisteman, **Rolak eta ezaugarriak gehitzeko laguntzailean** zerbitzarirako hiru rol nagusi hautatzen ari gara:

### Hautatutako rolak:
* **Active Directory domeinu-zerbitzuak (AD DS):** Saren erabiltzaileak, taldeak eta gailuak modu zentralizatuan kudeatzeko
* **DHCP zerbitzaria:** Sarekideei IP helbideak automatikoki esleitzeko.
* **DNS zerbitzaria:** Domeinu-izenak eta IP helbideak elkarren artean ebazteko.

Zerbitzaria gure sareko domeinu-kontrolatzaile nagusi gisa prestatzen ari gara.
![SEA 3](./img/SEA3.png)

# Rol eta Ezaugarrien Instalazioaren Jarraipena

Windows Server sisteman, aurreko urratsean hautatutako rolak, ezaugarriak eta kudeaketa-tresnak instalatzen ari gara `ORBIS_WINDOWS` zerbitzarian.

### Instalatzen ari diren osagai nagusiak:
* **Talde-direktiben kudeaketa (GPO):** Sareko politikak kudeatzeko tresnak.
* **AD DS kudeaketa-tresnak:** Active Directory eta PowerShell moduluak kudeatzeko tresnak.
* **DHCP eta DNS zerbitzarien kudeaketa-tresnak:** Zerbitzu hauek administratzeko lanabesak.

Instalazio-prozesua amaitu arte itxaroten ari gara konfigurazioarekin jarraitu ahal izateko.
![SEA 4](./img/SEA4.png)


![SEA 5](./img/SEA5.png)


![SEA 11](./img/SEA11.png)


![SEA 12](./img/SEA12.png)


![SEA 13](./img/SEA13.png)

![SEA 14](./img/SEA14.png)

![SEA 15](./img/SEA15.png)
