# Aufgabe: Website „Bergsteiger Hostel Innsbruck" mit Bootstrap 5

Du baust eine dreiseitige Website für ein Hostel nach. Diesmal mit **Bootstrap 5**
als Grundlage – und das ist die eigentliche Übung: möglichst wenig eigenes CSS
schreiben und stattdessen die Klassen benutzen, die Bootstrap schon mitbringt.

**Zeitrahmen:** 8–12 Stunden, gut auf mehrere Termine aufteilbar.
**Voraussetzung:** Du kennst HTML, Flexbox und Grid aus dem Café-Projekt.

---

## Das Ziel

So sieht das Ergebnis aus:

| Seite | Screenshot | Fertige Datei |
|---|---|---|
| Startseite | [vorschau/start.png](vorschau/start.png) | `loesung/index.html` |
| Zimmer & Preise | [vorschau/zimmer.png](vorschau/zimmer.png) | `loesung/zimmer.html` |
| Kontakt | [vorschau/kontakt.png](vorschau/kontakt.png) | `loesung/kontakt.html` |
| Startseite am Handy | [vorschau/start-handy.png](vorschau/start-handy.png) | – |

Diesmal bekommst du **keine ausgefüllten Kommentare pro Bauteil**. In den Dateien
im Ordner `start/` steht nur, welcher Bereich wohin gehört und welche
Bootstrap-Komponente gemeint ist. Die passenden Klassen suchst du selbst –
im [Spickzettel](SPICKZETTEL.md) oder in der
[Bootstrap-Doku](https://getbootstrap.com/docs/5.3/).

Alle Bilder und Icons liegen schon in `start/img/` und `start/icons/`.
Welche Datei wohin gehört und wie du sie einbindest, steht in
[MEDIEN.md](MEDIEN.md) – oder zum Anschauen in [medien.html](medien.html).

**Schau erst in die Lösung, wenn du eine Stelle wirklich nicht hinbekommst.**
Zwanzig Minuten selbst probieren bringt mehr als zwei Minuten abschreiben.

---

## Die Regel dieser Übung

> Alles, was Bootstrap kann, macht Bootstrap.

Eigenes CSS schreibst du nur für Dinge, die es in Bootstrap nicht gibt:
die Hausfarben, das Hero-Hintergrundbild und ein paar Korrekturen an Komponenten.
Die Datei `start/css/eigenes.css` steht am Ende bei etwa 100 Zeilen. Wenn deine
deutlich länger wird, hast du Arbeit gemacht, die dir Bootstrap abgenommen hätte.

Konkret heißt das:
- **Kein** eigenes `display: flex` – dafür gibt es `d-flex`, `justify-content-between`, `gap-3`
- **Kein** eigenes `grid-template-columns` – dafür gibt es `row` und `col-md-6 col-lg-4`
- **Keine** eigenen `margin`/`padding`-Regeln – dafür gibt es `py-5`, `mb-3`, `g-4`
- **Keine** eigene Media Query – dafür gibt es die Breakpoints `sm md lg xl`

---

## Die Schritte

### Schritt 1 – Bootstrap einbinden und verstehen
In `start/` sind CSS- und JS-Link schon gesetzt. Schau dir an, **warum**
das CSS im `<head>` und das JavaScript ganz unten steht, und was passiert,
wenn du `bootstrap.bundle.min.js` entfernst. (Tipp: dann geht das Burger-Menü nicht mehr.)

### Schritt 2 – Navbar mit Burger-Menü
Die erste echte Bootstrap-Komponente. Sie muss:
- ab dem Breakpoint `lg` ausgeklappt sein, darunter als Burger-Menü zusammenklappen
- dunkel sein und beim Scrollen oben kleben bleiben
- den aktiven Link hervorheben

Baue sie einmal richtig und kopiere sie dann auf die beiden anderen Seiten.
Beim Kopieren musst du den aktiven Link umhängen.

### Schritt 3 – Das Raster
Der wichtigste Teil überhaupt. Für den Leistungs-Bereich, die Zimmer-Cards
und die Bewertungen brauchst du immer dasselbe Muster:

```html
<div class="container">
  <div class="row g-4">
    <div class="col-12 col-md-6 col-lg-4"> … </div>
  </div>
</div>
```

Verstehe, warum es 12 Spalten sind, was `g-4` macht und warum `col-md-6`
auch für alle größeren Breiten gilt, solange nichts anderes dasteht.

### Schritt 4 – Hero mit eigenem CSS
Das Hintergrundbild kann Bootstrap nicht. Hier schreibst du selbst:
`background-image` mit einem `linear-gradient` darüber, damit die weiße
Schrift lesbar bleibt, `background-size: cover` und eine Mindesthöhe in `vh`.

### Schritt 5 – Cards
Drei Karten, die **gleich hoch** sind, egal wie lang der Text ist.
Der Trick dafür heißt `h-100` – finde heraus, warum das zusammen mit
`row`/`col` funktioniert.

### Schritt 6 – Carousel
Bildergalerie mit drei Bildern, Punkten unten, Pfeilen links und rechts
und einer Bildunterschrift, die auf kleinen Screens verschwindet
(`d-none d-md-block`). Achte auf die `data-bs-`-Attribute: sie verbinden
die Knöpfe mit dem Carousel über dessen `id`.

### Schritt 7 – Accordion und Modal (Seite „Zimmer")
- **Accordion**: vier Fragen, immer nur eine offen. Das regelt `data-bs-parent`.
- **Modal**: Der Button an jedem Zimmer öffnet dasselbe Modal, aber darin soll
  stehen, welches Zimmer angeklickt wurde. Das JavaScript dafür ist vorgegeben –
  du musst nur die richtigen Attribute und `id`s setzen.

### Schritt 8 – Tabelle
Die Preistabelle: gestreift, mit Kopfzeile in unserer Hausfarbe, mit `caption`
und in einem `table-responsive`, damit sie auf dem Handy seitlich scrollt
statt die Seite zu sprengen.

### Schritt 9 – Formular mit Prüfung (Seite „Kontakt")
Bootstraps `needs-validation`. Jedes Pflichtfeld bekommt eine eigene
`invalid-feedback`-Meldung. Das JavaScript ist vorgegeben – dein Teil ist
das HTML: `required`, `type="email"`, `min`/`max` bei der Personenzahl.
Teste, was passiert, wenn du leer absendest.

### Schritt 10 – Bootstrap in eigenen Farben
Zum Schluss der Feinschliff, damit die Seite nicht nach Standard-Bootstrap aussieht:
eigene Button-Varianten (`.btn-berg`), eigene Farb-Hilfsklassen und ein
Accordion in unseren Farben statt im Bootstrap-Blau. Der saubere Weg dafür sind
**CSS-Variablen**, nicht `!important` auf alles:

```css
.btn-berg {
  --bs-btn-bg: var(--berg);
  --bs-btn-hover-bg: var(--berg-hell);
  --bs-btn-color: #fff;
}
```

---

## Checkliste

- [ ] Alle drei Seiten sind über die Navigation erreichbar, der aktive Link stimmt jeweils
- [ ] Das Burger-Menü öffnet und schließt unter 992px
- [ ] Carousel, Accordion und Modal funktionieren
- [ ] Das Modal zeigt das richtige Zimmer an
- [ ] Das Formular meckert bei leeren Pflichtfeldern und zeigt danach die Erfolgsmeldung
- [ ] Bei 390px Breite gibt es **kein** seitliches Scrollen
- [ ] Die Karten sind gleich hoch
- [ ] Keine Fehler in der Browser-Konsole (F12)
- [ ] `eigenes.css` ist unter 120 Zeilen
- [ ] Du hast **keine** eigene `@media`-Regel geschrieben (außer beim Hero)

## Wenn du schneller fertig bist

- **Offcanvas** statt Burger-Dropdown: das Menü schiebt sich von rechts herein
- **Toast** statt Alert für die Erfolgsmeldung im Formular
- **Dark Mode** über `data-bs-theme="dark"` – Bootstrap 5.3 kann das von Haus aus
- Eine vierte Seite `hausordnung.html` mit einer `list-group` und Ankerlinks
- Bootstrap per **Sass** selbst bauen und die Farben direkt in `$primary` setzen,
  statt sie im Nachhinein zu überschreiben
