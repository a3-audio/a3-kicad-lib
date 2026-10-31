# a3-kicad-lib

## Allgemeine Infos für A3
- SMD Bauteilgröße: 1206

## Struktur der Library

- symbols/ – .kicad_sym Dateien für Schaltplansymbole
- footprints/ – .pretty Ordner mit .kicad_mod Dateien
- footprints/3dModel/ – STEP/WRL‑Modelle
- templates/ – optionale Referenzdesigns oder Beispielmodule
- archive/ – Third-party material no longer used by a board (Cherry MX breakout, MIT)

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

# Parts used by the A3-Mixer

| Symbol library (nickname) | Footprint library (nickname) | Origin |
|---|---|---|
| `symbols/MCP23S17T_E_SO.kicad_sym` (`MCP23S17`) | `footprints/MCP23S17T_E_SO.pretty` (`footprints`) | own |
| `symbols/MCP3208T-CI_SL.kicad_sym` (`MCP3208T-CI_SL`) | `footprints/MCP3208T_CI_SL.pretty` (`MCP3208T_CI_SL`, `MCP3208T-CI_SL`) | SnapMagic, own terms |
| `symbols/W5500-EVB-Pico-PoE.kicad_sym` (`W5500-EVB-Pico-PoE`) | – | own |

`3dAudioSym` and `3dAudioFoot` are the Motion libraries.

# Licence

CERN-OHL-S-2.0 (see `LICENSES/`, `.reuse/dep5`). Third-party parts keep their own terms: the SnapMagic MCP3208 files
(`LicenseRef-SnapMagic`) and the Cherry MX breakout in `archive/` (MIT).
