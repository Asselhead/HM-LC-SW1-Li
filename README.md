# HM-LC-SW1-Li
Homematic AskSin Schaltaktor für LED-Lichterketten mit LiIon Akku Ladefunktion.
- Basierend auf HM-LC-SW1-BA-PCB
![ISO_BATT](https://github.com/Asselhead/HM-LC-SW1-Li/blob/master/Images/ISO_BATT.png)

## Features

- ATMEGA644PA-AU
- USB Ladecontroller Microchip MCP73831T-2ACI/OT. Ladestrom Max. 500mA.
- Leiterplattenformat optimiert für direkte Verlötung von 18650er LiIon Zellen.
- Empfohlener maximaler Entladestrom 1,5A. LED Lichterketten Entladestrom Typ. 50-100mA.
- Lichterketten Vorwiderstand auf Lpl. bestückbar.
- optionale I2C Header Leiste bestückbar.
- optional SHT31 Temp./Humi Sensor bestückbar.
- optional SMD Headerleisten auf der BOT Seite bestückbar.

### FAQ

- Warum nur 500mA Ladestrom? -> Der MCP73831 ist ein preiswerter, noch leicht von Hand bestückbarer LiIon Ladechip.
In der Schaltung ist dieser so dimensioniert, dass der Ladestrom nur 450mA beträgt. Die Ladezeit bei heute üblichen LiIon Akkus liegt damit bei ca. 5-7 Stunden, was gerade noch so akzeptabel ist.
- Warum ein teurer ATMEGA644? -> Davon habe ich noch diverse in der Restekiste gehabt, darüber hinaus soll die Leiterplatte auch die Erprobung eines Sharp Memory LCD Display ermöglichen. In der Hoffnung, dass mir bei der Realisierung jemand Softwaretechnisch unter die Arme greift.
