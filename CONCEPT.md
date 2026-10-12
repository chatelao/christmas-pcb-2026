# Konzeptspezifikation: Berner Weihnachts-PCB ("Wiehnachts-Bärn PCB")

## 1. Übersicht & Vision
Das **"Wiehnachts-Bärn" PCB** ist ein elektronisches, weihnachtliches Badge / Christbaum-Ornament, das die historische Kulisse und Wahrzeichen der Stadt Bern mit feierlicher Weihnachtsbeleuchtung vereint.

Es dient als stilvoller Weihnachtsschmuck, Werbegeschenk oder DIY-Lötsatz. Durch das elegante Zusammenspiel von matt-schwarzer Platine, glänzendem Gold (ENIG) und strahlendem Weiß entsteht ein hochwertiges, modernes Kunstwerk für die Festtage.

---

## 2. Farb- & Ästhetikkonzept

Das Visuelle lebt vom Dreiklang aus **Matt-Schwarz, vergoldeten Flächen und weissem Siebdruck**:

*   **Lötstopplack:** Matt Schwarz (*Matte Black*) – bietet einen edlen, tiefen Kontrast.
*   **Oberflächenfinish:** ENIG (*Electroless Nickel Immersion Gold*) – echtes Gold auf allen freiliegenden Kupferflächen (Lötpads, Leiterbahnen, Deko-Elemente).
*   **Siebdruck (Silkscreen):** Reinweiß (*Bright White*) – für feine Konturen, Schneeflocken und Beschriftung.
*   **FR4-Substrat & Aussparungen (FR4 Backlight Effects):**
    *   Teilweise Aussparung von Kupfer und Lötstopplack auf der Rückseite, um diffuse Lichteffekte durch das leicht transparente FR4-Material zu erzeugen (z. B. leuchtendes Zifferblatt der Zytglogge oder Aare-Fluss).

---

## 3. Motive & Berner Weihnachtssymbolik

Das Platine-Layout kombiniert ikonische Berner Wahrzeichen mit weihnachtlicher Romantik:

1.  **Zytglogge (Zeitglockenturm):**
    *   Zentrales Motiv im Zentrum oder auf einer Seite der Platine.
    *   Das Zifferblatt ist mit Gold-Traces verziert; die Zeiger leuchten durch LEDs.
    *   Figurenspiel (Mondo, Bär) als weißer Siebdruck gezeichnet.
2.  **Der Berner Bär:**
    *   Bär mit roter/weisser Weihnachtsmütze (Silkscreen/Solder Mask Opening).
    *   Goldene Akzente an Tatzen und Krone.
3.  **Bundeshaus & Berner Altstadt Skyline:**
    *   Silhouetten-Panorama der Berner Altstadt im unteren Drittel der Platine.
    *   Kuppel des Bundeshauses mit vergoldeten Details.
4.  **Die Aare-Schlaufe:**
    *   Geschwungene Kupferspur (ENIG-Gold) entlang des unteren Randes, welche die Aare darstellt.
    *   Kapazitiver Touch-Sensor integriert in die Aare-Spur.
5.  **Weihnachtselemente:**
    *   Schneeflocken (*Muster im weißem Siebdruck & vergoldeten Durchkontaktierungen/Vias*).
    *   Sterne an der Spitze der Platine als LED-Lichtpunkte.
    *   Schlaufe/Öse am oberen Rand für das Aufhängen am Weihnachtsbaum (mit vergoldetem Innenring).

---

## 4. Elektronische Architektur & Komponenten

### 4.1 Mikrocontroller (MCU)
*   **Option A (Low Cost / RISC-V):** CH32V003F4P6 (32-Bit RISC-V, ultra-günstig, geringer Stromverbrauch).
*   **Option B (Einsteigerfreundlich / Arduino):** ATtiny85 / ATtiny1614 oder RP2040.
*   **Option C (Smart / Wireless):** ESP32-C3 (für WLAN-gesteuerte Lichtshows / Zeitsynchronisation).
*   *Empfehlung für Standard-Badge:* **CH32V003** oder **ATtiny1614** (perfekter Kompromiss aus Preis, Stromverbrauch und Pin-Anzahl).

### 4.2 Beleuchtung (LEDs)
*   **Vorderseite:**
    *   8x Warmweiße SMD-LEDs (0603 oder 0805) als blinkende/flackernde Sterne am Berner Nachthimmel.
    *   1x Bernstein/Gold-LED hinter dem Zytglogge-Zifferblatt.
*   **Rückseite (Reverse-Mount / Underglow):**
    *   4-6x Adressierbare RGB/Warmweiß-LEDs (z. B. WS2812B-2020 oder SK6812MINI-E) für Korona-Lichteffekte um die Platine und die Aare herum.

### 4.3 Stromversorgung
*   **Knopfzelle:** CR2032 Halterung auf der Rückseite für kabellosen Betrieb am Weihnachtsbaum.
*   **USB-C:** Type-C Buchse (nur Power) an der Unterseite für Dauerbetrieb auf dem Schreibtisch oder am Fenster.
*   **Power Management:**
    *   Auto-Power-Down Schaltung / Deep Sleep nach 30 Minuten Inaktivität zur Akkuschonung.
    *   Schiebe-Schalter (ON / OFF / TIMER).

### 4.4 Interaktion & Audio
*   **Kapazitiver Touch:** Aare-Kupferspur als Touch-Fläche zum Wechseln der Lichtmodi.
*   **Button:** Dezenter SMD-Taster auf der Rückseite.
*   **Audio (Optional):** Piezo-Buzzer (SMD) für 8-Bit Weihnachtsmelodien (*"O Tannenbaum"*, *"Zicke Zacke"*, *"Jingle Bells"*), stummschaltbar.

---

## 5. Platine-Form & Mechanisches Design

*   **Form:** Kontur in Form einer klassischen Weihnachtsbaum-Kugel (Durchmesser ca. 75 mm - 85 mm) mit stilisierter Berner Bärenkopf-Spitze oder kantonales Wappen als Aussenlinie.
*   **Befestigung:** Lötstelle/Durchbruch an der Spitze mit vergoldetem Ring für Christbaum-Aufhänger oder Band.
*   **Dicke:** 1.6 mm Standard FR4.

---

## 6. Software- & Firmware-Modi

1.  **Berner Gemütlichkeit (Kerzenschein-Modus):** Sanftes, ruhiges Warmweiss-Flackern der LEDs (Simulation von echten Kerzen auf der Aare).
2.  **Schneegestöber über dem Gurten:** Lauflicht-Effekt von oben nach unten über die Sterne.
3.  **Zytglogge Chime (Party-Modus):** Bunte Farbläufe mit synchronsiertem Piezo-Gespiel bei Touch-Berührung.
4.  **Eco-Nachtmodus:** Minimale Helligkeit für maximale Batterielaufzeit (hält mehrere Wochen mit CR2032).

---

## 7. Vorläufige Stückliste (Bill of Materials - BOM)

| Komponente | Beschreibung | Gehäuse / Footprint | Menge |
| :--- | :--- | :--- | :--- |
| **MCU** | CH32V003F4P6 oder ATtiny1614 | TSSOP-20 / SOIC-14 | 1 |
| **LEDs (Front)** | Warmweiß 0603 LED | 0603 | 8-10 |
| **LEDs (Glow)** | SK6812MINI-E / WS2812B-2020 | Reverse-Mount SMD | 4-6 |
| **USB-Buchse** | USB-C 16-Pin / 6-Pin Power Only | SMD | 1 |
| **Batteriehalter**| CR2032 Batteriehalter | SMD / THT | 1 |
| **Schalter** | Miniatur-Schiebeschalter | SMD | 1 |
| **Taster** | 3x4mm SMD-Taster | SMD | 1 |
| **Buzzer** | Passiver Piezo-Summer 9x9mm | SMD | 1 (Opt.) |
| **Passivmaterial**| Widerstände, Kondensatoren (100nF, 10uF, LDO) | 0603 | ~10 |

---

## 8. Zusammenfassung des Design-Guides für KiCad / EDA

*   **Front Layer (F.Cu & F.Mask):** Detaillierte Kunstwerke in Gold (Solder Mask Openings auf Massefläche) und Weiss (F.SilkS).
*   **Back Layer (B.Cu & B.Silks):** Bauteile weitgehend auf die Rückseite verlegt, damit die Vorderseite als reines Kunstwerk erstrahlt.
*   **Edg.Cuts:** Benutzerdefinierte Platinenkontur (Berner Skyline / Kugelkontur).
