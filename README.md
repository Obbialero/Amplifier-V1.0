# 🔊 Amplificatore Audio con Controllo Digitale del Volume (MAX5488 + TDA7377)

**Versione:** 1.0 
**Autore:** Obbialero Andrea  
**Data:** 27/01/2024  

## 📌 Descrizione del Progetto
Questo progetto consiste nella realizzazione di un amplificatore audio stereo a 4 canali, con controllo digitale del volume via SPI, progettato interamente su un singolo PCB.
Utilizza il potenziometro digitale MAX5488 per la gestione del volume e il TDA7377 come amplificatore di potenza. L’alimentazione è suddivisa in tre linee distinte: +24V, +12V e +5V, ottenute tramite regolatori XL4016 (buck) e LM7805 (lineare).

---

## 🔧 Specifiche Tecniche
Caratteristica	Valore
Canali Audio	4 (stereo ×2)
Amplificatore	TDA7377
Controllo Volume	Digitale via SPI (MAX5488)
Alimentazioni	+24V, +12V, +5V
Regolatori	XL4016 (Buck), LM7805 (Lineare)
Ingressi Audio	Jack PJ-3200
Uscite Audio	Connettori 4 pin
PCB	Progettato da zero

---

## 📦 Distinta Base (BOM)
Consulta la [Distinta Base completa](./BOM_PCB_AMPLIFIER_V1.0.csv) per tutti i componenti utilizzati, comprensivi di codici, valori e note tecniche.

---

## 🔌 Schema a Blocchi
arduino
Copia
Modifica
           +24V DC
              │
         ┌────▼──────┐
         │ XL4016    │   Buck Converter → +12V
         └────┬──────┘
              │
         ┌────▼──────┐
         │ LM7805    │   Regolatore Lineare → +5V
         └────┬──────┘
              │
         ┌────▼──────────────────┐
         │     MAX5488 (SPI)     │
         │  Potenziometro Digit. │
         └────┬──────────────────┘
              │
         ┌────▼──────┐
         │ TDA7377   │   Amplificatore Audio 4x
         └────┬──────┬──────┘
              │      │
          OUT1–2   OUT3–4

---
          
## 🎚️ Controllo Volume Digitale (SPI)          
Il volume viene gestito digitalmente tramite MAX5488, controllabile via microcontrollore (es. ESP32, Raspberry Pi, Arduino).

Segnale SPI	Descrizione
SCLK	Clock seriale
DIN	Dati seriali
CS#	Chip Select

---

## 🧱 Filtraggio e Protezione
Componente	Funzione
LC Filter	47 µH + 100nF–1000µF su linee Vcc
Diodo Schottky	VS-10BQ040-M3 su linea +24V
Diodo 1N4148	Protezione segnali digitali
Condensatori di bypass	Ravvicinati ai pin di alimentazione

---

## 📎 Connettori
Componente	Funzione
PJ-3200	Ingresso audio stereo
U11/U13	Connettori audio 4 pin
P11	Ingresso alimentazione

---

## 🛠️ Raccomandazioni PCB
Tracce di potenza (24V/12V): ≥2 mm di larghezza

Separazione masse: PW-GND (potenza) e S-GND (segnale) ben distinte

Linee SPI: il più corte possibile per minimizzare interferenze

Condensatori bulk: montati vicino a XL4016 e TDA7377

---

## 📂 File Inclusi
README.md – Documentazione del progetto

Schematic_PCB_AMPLIFIER_2025-05-14.pdf – Schema elettrico

distinta_base.xlsx – BOM dettagliata

(eventuali file .sch / .brd da includere)

---

## 📸 Immagini e PCB
(Inserire immagini del prototipo o rendering del PCB se disponibili)

---

## ⚠️ Avvertenze
⚠️ Attenzione: la linea da 24V può generare surriscaldamento.
Utilizzare dissipatori su XL4016 e TDA7377 per evitare thermal shutdown.
Assicurarsi che le masse siano ben collegate e le connessioni audio schermate.

---

## 📬 Contatti
Per dubbi, miglioramenti o segnalazioni:
**Andrea Obbialero**– https://obbialero.github.io/

---

## 📘 Licenza
Questo progetto è rilasciato sotto licenza MIT.
Libero per uso personale, educativo e commerciale con attribuzione.


