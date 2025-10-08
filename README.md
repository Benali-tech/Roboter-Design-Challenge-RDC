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
├── arduino/                 # Enthält den Arduino-Code (C++) für die Robotersteuerung
│   └── rdc_main.ino         # Hauptprogramm: Linienverfolgung, Ultraschallsensor, Motorsteuerung
│
├── python/                  # Python-Kommunikation, Visualisierung & Analyse
│   │
│   ├── config.py            # Zentrale Konfiguration (Serieller Port, Baudrate, Log-Dateien)
│   │
│   ├── serial_reader.py     # Verbindet sich mit Arduino über USB/Serial und liest Datenströme
│   │
│   ├── data_logger.py       # Speichert eingehende Sensordaten (Distanz, Linienstatus, etc.) in CSV-Datei
│   │
│   ├── visualization.py     # Liest geloggte Daten und zeigt sie als Diagramm (Matplotlib)
│   │
│   ├── main.py              # Hauptskript – verbindet alle Module (SerialReader, Logger, etc.)
│   │                        # Läuft kontinuierlich und liest Daten vom Roboter
│   │
│   ├── utils/               # Sammlung von Hilfsfunktionen & Datenverarbeitung
│   │   ├── __init__.py      # Markiert diesen Ordner als Python-Paket (Pflicht für Importe)
│   │   ├── parser.py        # Enthält Funktionen, um serielle Datenstrings zu zerlegen (z. B. "DIST:25;LINE:1")
│   │   └── filters.py       # Optional: Filter & Glättungsfunktionen für Sensordaten (z. B. gleitender Mittelwert)
│   │
│   ├── tests/               # Automatische Tests für Qualitätssicherung
│   │   ├── test_parser.py       # Testet Funktionen aus utils/parser.py
│   │   └── test_serial_reader.py # Testet Verhalten des SerialReader-Moduls (z. B. simulierte Daten)
│   │
│   ├── __init__.py          # Macht den Ordner „python“ zu einem Python-Paket
│
├── README.md                # Projektbeschreibung, Ziele, Aufbau & Bedienungsanleitung
│
├── requirements.txt         # Liste aller benötigten Python-Abhängigkeiten (pyserial, pandas, matplotlib)
│
├── LICENSE                  # Lizenzdatei (z. B. MIT, GPL) – regelt Nutzungsrechte
│
├── .gitignore               # Definiert Dateien, die Git ignorieren soll (z. B. .idea/, __pycache__)
│
└── .idea/                   # PyCharm-Projektdateien (automatisch generiert, nicht manuell bearbeiten)


