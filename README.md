# Bergsteiger Hostel – Übungsprojekt für HTML, CSS & Bootstrap 5

Dreiseitige Hostel-Website zum Nachbauen. Aufbauübung nach dem
[Café-Projekt](https://github.com/ahsumasearch-afk/html-css-uebungsprojekt):
diesmal mit Bootstrap 5 statt handgeschriebenem Flexbox und Grid.

**Vorlage ansehen:** <https://ahsumasearch-afk.github.io/bootstrap-uebungsprojekt/>

Kein Build-Werkzeug, kein npm, keine Installation – Bootstrap kommt per CDN,
alle Bilder und Icons liegen als SVG im Projekt.

## Ordner

```
bootstrap-uebungsprojekt/
├── AUFGABE.md        ← Aufgabenstellung in 10 Schritten
├── SPICKZETTEL.md    ← die wichtigsten Bootstrap-Klassen auf einen Blick
├── vorschau/         ← Screenshots aller Seiten (das Ziel)
├── start/            ← hier arbeitet der Schüler
│   ├── index.html    ← Gerüst: nur Bereichsliste, keine fertigen Klassen
│   ├── zimmer.html
│   ├── kontakt.html
│   ├── css/eigenes.css
│   ├── img/          ← 12 Bilder (SVG)
│   └── icons/        ← 16 Icons (SVG)
└── loesung/          ← fertige Website
```

## Was geübt wird

| Thema | Wo im Projekt |
|---|---|
| Raster-System, Breakpoints | überall: `row` / `col-md-6 col-lg-4` |
| Navbar mit Burger-Menü | alle drei Seiten |
| Carousel | Bildergalerie auf der Startseite |
| Cards gleicher Höhe | Zimmer-Vorschau |
| Accordion | häufige Fragen |
| Modal mit `data`-Attributen | Zimmer anfragen |
| Tabellen, `table-responsive` | Preise nach Saison |
| Formular mit `needs-validation` | Kontaktseite |
| Utility-Klassen | statt eigener CSS-Regeln |
| Bootstrap umfärben über CSS-Variablen | `css/eigenes.css` |
| Mehrseitige Navigation | aktiver Link pro Seite |

## Unterschied zum Café-Projekt

Das Café-Projekt hatte pro Abschnitt einen Kommentar, der genau sagte, was
zu tun ist. Hier steht nur noch, **welcher Bereich** wohin gehört und
**welche Komponente** gemeint ist – die Klassen sucht der Schüler selbst.
Als Ziel dienen die Screenshots in `vorschau/` und die Live-Vorlage.

## Loslegen

1. Repo herunterladen (**Code → Download ZIP**) und entpacken.
2. `loesung/index.html` im Browser öffnen oder die
   [Live-Vorlage](https://ahsumasearch-afk.github.io/bootstrap-uebungsprojekt/) ansehen.
3. `AUFGABE.md` lesen, `SPICKZETTEL.md` daneben offen lassen.
4. In `start/` arbeiten.

## Lizenz

Alle Inhalte (Texte, Bilder, Icons, Code) sind für dieses Projekt erstellt und
frei für Unterricht und private Nutzung verwendbar. Das Bergsteiger Hostel ist erfunden.
Bootstrap steht unter der MIT-Lizenz.
