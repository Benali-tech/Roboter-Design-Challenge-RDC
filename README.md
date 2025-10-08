# Roboter-Design-Challenge-RDC 🤖🚗

Ein autonomes Fahrzeug-Projekt.

Unser Roboter fährt selbstständig einen Parcours ab, folgt einer Linie, erkennt Hindernisse und meistert Aufgaben wie Rampen oder Tunnel – **ohne Fernbedienung**!

---

## 🏁 Ziel des Wettbewerbs

Der Roboter muss **vollständig autonom** einen vorgegebenen Parcours bewältigen:
- Schwarze Linie verfolgen
- Hindernisse erkennen und überwinden
- Spezielle Aufgaben lösen (z. B. „Müll“ einsammeln, Signale erkennen)
- Unter verschiedenen Bedingungen fahren (unterschiedliche Böden, Steigungen)

## 🧱 Hardware-Bauteile (aus dem Bausatz)

Wir nutzen nur Teile aus dem offiziellen Bausatz + max. **10€ Eigenkäufe**:

- **Arduino Uno** (Hirn des Roboters)
- **HC-SR04 Ultraschallsensor** – für Abstandsmessung
- **IR-Linienfolgesensoren** – zur Spurverfolgung
- **L298N Motor-Treiber** – steuert die Motoren
- **2 DC-Motoren mit Rädern**
- **Akku, Platine, Kabel, Schrauben**

## 🛠️ Aufbau des Roboters

Der Roboter wurde komplett selbst gebaut – kein vorgefertigtes Chassis.  
Er hat:
- Eine stabile Basis aus Metallteilen
- Zwei Antriebsräder hinten, Vorderrad frei drehbar (Lenkung durch Geschwindigkeitsunterschied)
- Sensoren vorne und unten angebracht


## 💻 Software & Programmierung

### Hauptsteuerung: Arduino (C++)
Der Roboter wird hauptsächlich mit **Arduino** gesteuert. Der Code befindet sich im Ordner `arduino/`.

Beispiel-Funktionen:
- Linienverfolgung mit IR-Sensoren
- Distanzmessung mit Ultraschall
- Ausweichen bei Hindernis < 10 cm
- Fahren über Rampe / Tunnel

### Zusatz: Python (optional)
Python wird genutzt für:
- Serielle Kommunikation mit Arduino (`pyserial`)
- Visualisierung von Sensordaten (`matplotlib`)
- Testen und Analysieren

Code in `python/`:
- `serial_reader.py`: Liest Daten vom Arduino
- `visualization.py`: Zeigt Distanzverlauf als Diagramm

---

## ⚙️ Wie starten?

### 1. Arduino-Code hochladen
- Öffne `arduino/rdc_main.ino` in der Arduino IDE
- Wähle Board: **Arduino Uno**
- Wähle Port (z. B. `COM3`)
- Klicke auf **Upload**

### 2. Python-Skript starten (optional)
Im Terminal:
```bash
cd python
python serial_reader.py
>>>>>>> a4ba82ad891cf18d6e2bc647e97413a85ef5929c

### Projektstruktur (Python-Teil):

Roboter-Design-Challenge-RDC/
│
├── arduino/
│   └── rdc_main.ino                # Arduino-Hauptcode
│
├── python/
│   ├── __init__.py
│   ├── config.py                   # Serielle Port-Konfiguration, Logging-Level etc.
│   ├── serial_reader.py            # Kommunikation mit Arduino
│   ├── visualization.py            # Live- oder gespeicherte Daten visualisieren
│   ├── data_logger.py              # (optional) Speichert Messwerte in CSV
│   ├── utils/
│   │   ├── __init__.py
│   │   ├── parser.py               # Hilfsfunktionen für Datenverarbeitung
│   │   └── filters.py              # evtl. Glättung von Messwerten
│   ├── tests/
│   │   ├── test_serial_reader.py   # Unit Tests
│   │   └── test_parser.py
│   └── main.py                     # Einstiegspunkt, verbindet alles
│
├── requirements.txt
└── README.md

