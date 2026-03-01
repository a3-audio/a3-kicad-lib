# a3-kicad-lib

## Allgemeine Infos für A3
- SMD Bauteilgröße: 1206

## Struktur der Library

- symbols/ – .kicad_sym Dateien für Schaltplansymbole
- footprints/ – .pretty Ordner mit .kicad_mod Dateien
- 3d/ – STEP/WRL‑Modelle
- templates/ – optionale Referenzdesigns oder Beispielmodule
- docs/ – Datenblätter, interne Spezifikationen, Guidelines

# Namenskonventionen und Konsistenz

- Symbol‑Namen (z. B. Hersteller_Partnummer)
- Footprint‑Namen (z. B. Package‑Typ + Abmessungen)
- Pin‑Nummerierung entsprechend Datenblatt
- 3D‑Modell‑Namen passend zum Footprint
- KiCad Library Convention (KLC) ist kein starres Regelwerk, aber ein hilfreicher Standard, der spätere Fehler vermeidet und die Wiederverwendbarkeit erhöht

# Symbol‑ und Footprint‑Qualität

- Pin‑Reihenfolge und ‑Orientierung exakt nach Datenblatt
- Footprint‑Maße ausschließlich aus dem Package‑Drawing übernehmen
- Courtyard und Fab‑Layer sauber definiert
- 3D‑Modelle korrekt ausgerichtet und skaliert
- Parameter wie Pad‑Size und Clearance konsistent über die Library hinweg

# Integration in KiCad‑Projekte

Für jedes Projekt empfiehlt sich:
- Library als Git‑Submodule einbinden
- oder über KiCad’s Library Manager auf einen festen Pfad verlinken
- keine lokalen Kopien der Symbole/Footprints im Projekt (außer Overrides)
- Das entspricht auch Best Practices, die empfehlen, projektlokale Libraries nur für projektspezifische Anpassungen zu nutzen, nicht für generische Bauteile
