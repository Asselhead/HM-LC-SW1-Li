# HM-LC-SW1-Li
Homematic AskSin Schaltaktor für LED-Lichterketten mit LiIon Akku Ladefunktion.
- Basierend auf HM-LC-SW1-BA-PCB
![ISO_BATT](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/ISO_BATT.png)

## **Warnung!!!**

Dies ist ein Hobbyprojekt, welches umfangreiche Kenntnisse im Umgang mit Lithium Akkus erfordert.
Bei Falschbehandlung von Lithium Akkus kann es zu Brand oder Explosionen kommen. Der Entwickler der Schaltung und des Layout kann keine Garantie für die korrekte Funktion übernehmen und kann für evtl. auftretende Folgeschäden keine Haftung übernehmen.
Lithium Akkus nur unter Aufsicht auf einer feuerfesten Unterlage laden! Verwendung auf eigene Gefahr!

## Features

- ATMEGA644PA-AU (Pinbeschriftung/Netznamen folgen dem Bobuino Pinout).
- USB Ladecontroller Microchip MCP73831T-2ACI/OT. Ladestrom Max. 500mA, Ladeschlussspannung **4,2V**.
- Leiterplattenformat optimiert für direkte Verlötung von 18650er LiIon Zellen mit U-Lötfahnen (18x65mm).
- Empfohlener maximaler Entladestrom 1,5A. LED Lichterketten Entladestrom Typ. 50-100mA.
- Lichterketten Vorwiderstand auf Lpl. bestückbar.
- optionale I2C Header Leiste bestückbar.
- optional SHT31 Temp./Humi Sensor bestückbar.
- optional SMD Headerleisten mit I/Os im 2,54er Raster auf der BOT Seite bestückbar.

### FAQ

- Warum nur 500mA Ladestrom?
-> Der MCP73831 ist ein preiswerter, noch leicht von Hand bestückbarer LiIon Ladechip.
In der Schaltung ist dieser so dimensioniert, dass der Ladestrom nur 450mA beträgt. Die Ladezeit bei heute üblichen LiIon Akkus liegt damit bei ca. 5-7 Stunden, was gerade noch so akzeptabel ist.

- Warum ein teurer ATMEGA644?
-> Davon habe ich noch diverse in der Restekiste gehabt, darüber hinaus soll die Leiterplatte auch die Erprobung eines Sharp Memory LCD Display ermöglichen. In der Hoffnung, dass mir bei der Realisierung jemand Softwaretechnisch unter die Arme greift.

## Schaltung

![Schematic_V0.2](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Schematic_V0.2.pdf)

## Hardware

#### Benötigte Bauteile

#### Reichelt

[Bestellliste](https://www.reichelt.de/my/1519439)

Bauteil                  | Bestellnummer    | Anzahl | Kommentar
------------------------ | ---------------- | ------ | ---------
C1, C9, C11, C17, C18    | X5R-G0603 10/6   |   5    | -
C2 .. C8, C13, C19       | X7R-G0603 100N   |   9    | -
C12, C14                 | X7R-G0603 15PF   |   2    | - optional bei bestücktem Quarz.
C15, C16                 | X7R-G0603 2,2/10 |   2    | - optional auf BOT Seite
R3, R6                   | RND 0603 1 470R  |   2    | -
R1, R7..R9, R15          | RND 0603 1 10K   |   5    | -
R11                      | RND 0805         |   1   | - Widerstandswert abhängig von Lichterkette
IC5                      | MCP 1703T-3302E |   1    | - 2.0µA Leckstrom
IC2                      | ATMEGA 644PA-AU |   1    | -
IC4                      | MCP 73831T-2ACI |   1    | - Alternativ MCP 73831T-2ATI
IC3                      | SHT31           |   1    | - optional Temp./Humi - nicht bei Reichelt
LD1                      | RND 135-00180   |   1    | - Ladezustand
LD2                      | RND 135-00182   |   1    | - Status
T1                       | IRLML 2502      |   1    | - Alternativ SI2302
Q1                       | ABM8AIG-8.000MHZ|   1    | - optional. Abracon nicht bei Reichelt
Verbinder zu U2          | MPE 156-1-032   |   1    | muss per Hand umgebogen werden
Verbinder zu U2          | SL 1X20G 2,00   |   1    | optional, hilfreich zum Anschließen des ISP


#### Sonstiges

Bauteil | Bestellnummer            | Anzahl | Kommentar
------- | ------------------------ | ------ | ---------
IC1     | CC1101 Funkmodul 868 MHz |   1    | z.B. [eBay](https://www.ebay.de/itm/272455136087)

~8,3 cm Draht als Antenne


### Programmieradapter
- 1x ISP (z.B. Reichelt Art. Nr. DIAMEX USB ISP)
- 1x ISP (z.B. [diesen hier](https://www.diamex.de/dxshop/USB-ISP-Programmer-fuer-Atmel-AVR-Rev2))

## Aufbau

### Hilfsmittel

Da es sich größtenteils um 0603er Bauteile handelt, empfehle ich folgendes Werkzeug:
1. Lupenbrille mit 2,5facher Vergrößerung
2. Lötzinn mit 0,3mm Durchmesser (0,5mm geht auch)
3. Entlötlitze
4. Antimagnetische Pinzette mit dünner Spitze
