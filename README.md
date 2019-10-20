# HM-LC-SW1-Li
Homematic AskSin Schaltaktor für LED-Lichterketten mit LiIon Akku Ladefunktion.
- Basierend auf HM-LC-SW1-BA-PCB
![ISO_BATT](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/ISO_BATT.png)

## Features

- ATMEGA644PA-AU (Pinbeschriftung/Netznamen folgen dem Bobuino Pinout).
- USB Ladecontroller Microchip MCP73831T-2ACI/OT. Ladestrom Max. 500mA.
- Leiterplattenformat optimiert für direkte Verlötung von 18650er LiIon Zellen (18x65mm).
- Empfohlener maximaler Entladestrom 1,5A. LED Lichterketten Entladestrom Typ. 50-100mA.
- Lichterketten Vorwiderstand auf Lpl. bestückbar.
- optionale I2C Header Leiste bestückbar.
- optional SHT31 Temp./Humi Sensor bestückbar.
- optional SMD Headerleisten auf der BOT Seite bestückbar.

### FAQ

- Warum nur 500mA Ladestrom? -> Der MCP73831 ist ein preiswerter, noch leicht von Hand bestückbarer LiIon Ladechip.
In der Schaltung ist dieser so dimensioniert, dass der Ladestrom nur 450mA beträgt. Die Ladezeit bei heute üblichen LiIon Akkus liegt damit bei ca. 5-7 Stunden, was gerade noch so akzeptabel ist.
- Warum ein teurer ATMEGA644? -> Davon habe ich noch diverse in der Restekiste gehabt, darüber hinaus soll die Leiterplatte auch die Erprobung eines Sharp Memory LCD Display ermöglichen. In der Hoffnung, dass mir bei der Realisierung jemand Softwaretechnisch unter die Arme greift.

## Hardware

#### Bauteile

#### Reichelt

[Bestellliste](https://www.reichelt.de/my/1519439)

Bauteil                  | Bestellnummer    | Anzahl | Kommentar
------------------------ | ---------------- | ------ | ---------
C1, C8, C9, C16, C17     | X5R-G0603 10/6   |   5    | -
C2 .. C7, C10, C11, C14  | X7R-G0603 100N   |   9    | -
C12, C13                 | X7R-G0603 15PF   |   2    | -
R1, R3                   | RND 0603 1 470R  |   2    | -
R2, R8, R9               | RND 0603 1 10K   |   3    | -
IC1                      | MCP 1703T-3302E |   1    | - 2.0µA Leckstrom
IC4                      | ATMEGA 644PA-AU |   1    | -
IC8                      | MCP 73831T-2ACI |   1    | -
IC9                      | SHT31           |   1    | - optional Temp./Humi
LD1                      | LED grün 0603   |   1    | - pair
LD2                      | LED blau 0603   |   1    | - Charge
T1                       | SI2302          |   1    | - nicht bei Reichelt
Q1                       | ABM8AIG-8.000MHZ|   1    | - Abracon nicht bei Reichelt
Verbinder zu U2          | MPE 156-1-032   |   1    | muss per Hand umgebogen werden
Verbinder zu U2          | SL 1X20G 2,00   |   1    | optional, hilfreich zum Anschließen des ISP


#### Sonstiges

Bauteil | Bestellnummer            | Anzahl | Kommentar
------- | ------------------------ | ------ | ---------
IC2     | CC1101 Funkmodul 868 MHz |   1    | z.B. [eBay](https://www.ebay.de/itm/272455136087)

~8,3 cm Draht als Antenne


### Programmieradapter
- 1x ISP (z.B. [diesen hier](https://www.diamex.de/dxshop/USB-ISP-Programmer-fuer-Atmel-AVR-Rev2))
