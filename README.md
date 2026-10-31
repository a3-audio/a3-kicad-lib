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

# Parts used by the A3 boards

Everything below was taken from the boards themselves (the copies KiCad embeds in the schematic `lib_symbols` and in the
`.kicad_pcb`), because the original working library was lost. Standard KiCad libraries are not repeated here.

| Board | Symbol libraries (nickname) | Footprint libraries (nickname) |
|---|---|---|
| A3-Mixer v3.1 (`pcb/v3_1`) | `MCP23S17`, `MCP3208T-CI_SL`, `W5500-EVB-Pico-PoE` (files `MCP23S17T_E_SO`, `MCP3208T-CI_SL`, `W5500-EVB-Pico-PoE`) | `footprints` (= `MCP23S17T_E_SO.pretty`), `MCP3208T_CI_SL`, `MCP3208T-CI_SL` (both = `MCP3208T_CI_SL.pretty`) |
| A3-Mixer v0.2 (`pcb/v0_2`) | `mixer.pcb-rescue` | `teensy` |
| A3-Motion v3.1 (`pcb/v3_1`, `enc_pot`, `led_but`) | `3dAudioSym` | `3dAudioFoot` |
| A3-Motion v1 (`pcb/v1`) | `controller_motion_pcb-rescue`, `btn-matrix-rescue` | `teensy`, `SamacSys_Parts` |

The `*-rescue` libraries are KiCad 5 "rescue" copies that the old v1/v0.2 schematics reference. They hold the board's
Teensy 4.1, 74HC4051, 228CMVARGBFR RGB LED and WS2811 symbols plus rescued copies of standard symbols. They exist only so
those old boards open without missing-library errors; new designs use the standard libraries.

Footprints without a 3D model in the repository (the model path is kept as the board had it): `teensy:Teensy41`,
`teensy:Teensy41_my` (`Teensy_4.1_Assembly.STEP`), `SamacSys_Parts:228CMVARGBFR` (`228CMVARGBFR.stp`).

The MCP3208 symbol, footprint and 3D model are a third-party download (SnapMagic, own terms in
`symbols/MCP3208T-CI_SL.License.txt`) and are to be replaced by our own drawing.

# Licence

CERN-OHL-S-2.0 (see `LICENSES/`, `.reuse/dep5`). Third-party parts keep their own terms: the MCP3208 files
(`LicenseRef-SnapMagic`, to be replaced) and the Cherry MX breakout in `archive/` (MIT).
