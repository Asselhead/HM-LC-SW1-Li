# HM-LC-SW1-Li
Homematic AskSin Schaltaktor für LED-Lichterketten mit LiIon Akku Ladefunktion.
- Basierend auf HM-LC-SW1-BA-PCB
![ISO_BATT_V0.2](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/ISO_BATT_V0.2.png)

## **Warnung!!!**

Dies ist ein Hobbyprojekt, welches umfangreiche Kenntnisse im Umgang mit Lithium Akkus erfordert.
Bei Falschbehandlung von Lithium Akkus kann es zu Brand oder Explosionen kommen. Der Entwickler der Schaltung und des Layout kann keine Garantie für die korrekte Funktion übernehmen und kann für evtl. auftretende Folgeschäden keine Haftung übernehmen.
Lithium Akkus nur unter Aufsicht auf einer feuerfesten Unterlage laden! Verwendung auf eigene Gefahr!

## Link zum Thread im Homematic Forum:

https://homematic-forum.de/forum/viewtopic.php?f=76&t=53925&sid=b3c1556a95baa7e0ea64069ffd812379

## Features

- ATMEGA644PA-AU (Pinbeschriftung/Netznamen folgen dem Bobuino Pinout).
- USB Ladecontroller Microchip MCP73831T-2ACI/OT. Ladestrom Max. 500mA, Ladeschlussspannung **4,2V**.
- MCP1703T-3302E/CB LDO mit sehr geringem Ruhestrom.
- Leiterplattenformat optimiert für direkte Verlötung von 18650er LiIon Zellen mit U-Lötfahnen (18x65mm).
- Empfohlener maximaler Entladestrom 1,5A. LED Lichterketten Entladestrom Typ. 50-100mA.
- Lichterketten Vorwiderstand auf Lpl. bestückbar (ggf. 330mW 0805er Type verwenden).
- optional I2C Header Leiste und Pull-Ups bestückbar.
- optional SHT31 Temp./Humi Sensor bestückbar.
- optional SMD Headerleisten mit I/Os im 2,54er Raster auf der BOT Seite bestückbar.
- optional ZIF Buchse für Sharp Memory LCD Display auf BOT Seite bestückbar.
- Pinning des Seriellen Programmieranschluss folgt dem gängigen Schema.
- optional STL File für Programmierhilfe mit Federkontakt Testnadeln verfügbar (Thingiverse).
- Gehäuse für HM-LC-SW1-Li bei Thingiverse verfügbar.

### FAQ

- Warum nur 500mA Ladestrom?
-> Der MCP73831 ist ein preiswerter, noch leicht von Hand bestückbarer LiIon Ladechip.
In der Schaltung ist dieser so dimensioniert, dass der Ladestrom nur 450mA beträgt. Die Ladezeit bei heute üblichen LiIon Akkus liegt damit bei ca. 5-7 Stunden, was gerade noch so akzeptabel ist.

- Warum ein teurer ATMEGA644?
-> Davon habe ich noch diverse in der Restekiste gehabt. Darüber hinaus soll die Leiterplatte auch die Erprobung eines Sharp Memory LCD Display ermöglichen (128x128Pixel). In der Hoffnung, dass mir bei der Realisierung jemand Softwaretechnisch unter die Arme greift.

### Wichtige Hinweise zur Ladeschaltung
- Den hier verwendete Lithium Ladecontroller MCP73831 gibt es in verschiedenen Varianten. Es muss zwingend darauf geachtet werden, dass eine Variante mit der **-2** im Namen verwendet wird. Das stellt sicher, dass die Ladeschlussspannung Werksseitig auf 4,2V eingestellt ist und der anschlossene LiIon Akku nicht überladen wird. In Frage kommen folgende Typen:
1. MCP73831-2ACI/OT
2. MCP73831T-2ACI/OT (wie 1. jedoch Tape and Reel -> Verfügbar bei Reichelt)
3. MCP73831-2ATI/OT (wie 1. jedoch wird Akku Voll bereits bei 20% von Ireg (hier 90mA) erkannt -> kürzere Ladezeit aber weniger eingeladene Kapazität)
4. MCP73831T-2ATI/OT (wie 3. jedoch Tape and Reel)

## Schaltung

[Schaltung](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Schematic_V03.pdf)

## Hardware

#### Benötigte Bauteile

#### Reichelt

[Reichelt Warenkorb (Nur Basisbestückung)](https://www.reichelt.de/my/1648397) **Ohne USB Buchse**


Bauteil                  | Bestellnummer    | Anzahl | Kommentar
------------------------ | ---------------- | ------ | ---------
C1, C9, C11, C17, C18    | X5R-G0603 10/6   |   5    | -
C2 .. C8, C13, C19       | X7R-G0603 100N   |   9    | -
C15, C16                 | X7R-G0603 2,2/10 |   2    | - optional auf BOT Seite
R3, R6                   | RND 0603 1 470R  |   2    | -
R1, R7..R10, R15         | RND 0603 1 10K   |   6    | -
R11                      | RND 0805   330mW |   1   | - Widerstandswert abhängig von Lichterkette
R14                      | RND 1550603 AE   |   1   | - Basisvorwiderstand FET
R5                       |RND 0603 1 2K     |   1   | - Ladestrom Einstell-Widerstand 2K=500mA
IC5                      | MCP 1703T-3302E |   1    | - 2.0µA Leckstrom
IC2                      | ATMEGA 644PA-AU |   1    | -
IC4                      | MCP 73831T-2ACI |   1    | - Alternativ MCP 73831T-2ATI
IC3                      | SHT31           |   1    | - optional Temp./Humi - nicht bei Reichelt
LD1                      | RND 135-00180   |   1    | - Ladezustand LED
LD2                      | RND 135-00182   |   1    | - Status LED
T1                       | IRLML6344       |   1    | - Alternativ SI2302, IRLML2502
S1                       | KMR 231 G LFS   |   1    | - Originaltaster ist von Würth 434153017835
J1, J2                   | SL 1X36G SMD2,54|   1    | - optional auf der BOT Seite, Abschnitt
**BU1**                  | **Hirose ZX62D-AB-5P8** | 1 | **- nicht bei Reichelt. Evtl. geht auch MIUSB-F5M-ABG-U von Reichelt oder https://lcsc.com/product-detail/USB-Connectors_Jing-Extension-of-the-Electronic-Co-C10418_C10418.html**
BU2                      | WR-FPC           |   1    | - optional auf der BOT Seite, Anschluss des Sharp Memory LCD Display. Nicht bei Reichelt. Würth 68711014022



#### Sonstiges

Bauteil | Bestellnummer            | Anzahl | Kommentar
------- | ------------------------ | ------ | ---------
IC1     | CC1101 Funkmodul 868 MHz |   1    | z.B. [eBay](https://www.ebay.de/itm/272455136087)
Akku    | Panasonic NCR18650B      |   1    | z.B. [Akkuteile](https://www.akkuteile.de/lithium-ionen-akkus/18650/panasonic/panasonic-ncr18650b-3-6v-3400mah-loetfahne-u_1006391_1662) 

~8,3 cm Draht als Antenne


### Programmieradapter
- 1x ISP (z.B. Reichelt Art. Nr. DIAMEX USB ISP)

## Aufbau
![TOP_V03](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/TOP_V03.png)
![BOT_V03](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/BOT_V03.png)

### Bestückungsunterlagen

[Assembly](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Assembly_V03.pdf)

### Hilfsmittel

Da es sich größtenteils um 0603er Bauteile handelt, empfehle ich folgendes Werkzeug:
1. Lupenbrille mit 2,5facher Vergrößerung
2. Lötzinn mit 0,3mm Durchmesser (0,5mm geht auch)
3. Entlötlitze
4. Antimagnetische Pinzette mit dünner Spitze

### Lötreihenfolge

Es empfiehlt sich folgende Bestückungsreihenfolge einzuhalten.
1. IC2 - ATMEGA644
2. BU1 - Micro USB Buchse
3. IC8, IC5 und T1
4. Alle Widerstände und Kondensatoren
5. IC1 - CC1101 Modul

## Inbetriebnahme

Für den verwendeten ATMEGA644PA-AU muss zunächst das MightyCore Arduino Hardware Paket von MCUDude heruntergeladen werden.
Als Sketch kommt der HM-LC-SW1-BA-PCB (https://github.com/pa-pa/AskSinPP/blob/master/examples/HM-LC-SW1-BA-PCB/HM-LC-SW1-BA-PCB.ino) zum Einsatz.

Erst nach dem programmieren, anlernen und testen des Aktors sollte der Akku angelötet werden.
Wichtig!!! Die Bot Seite der Leiterplatte muss nach dem Programmieren und vor dem verlöten des Akkus mit Kapton oder Isolierband abgeklebt werden um Kurzschlüsse zu vermeiden!
Je nach verwendetem Akku kann es hilfreich sein, die Lötfahnen mit einem Seitenschneider etwas zurecht zu stutzen.

## Gehäuse

![IMG_20191028_201238](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/IMG_20191028_201238.jpg)
![DSC02080](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/DSC02080.JPG)
![DSC02079](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/DSC02079.JPG)

Ein Gehäuse ist auf Thingiverse hinterlegt:
https://www.thingiverse.com/thing:3946705

## Leiterplatten

Bei Interesse an unbestückten Leiterplatten bitte im HM Forum per PM melden.

## Dankeschön

Vielen Dank an die AskSin++ Pioniere im Homematic Forum (pa-pa, Jérôme, Tom Major, Alex Reinert, Marco usw.) ohne die es sicherlich keine Eigenbau Hardware gäbe.
