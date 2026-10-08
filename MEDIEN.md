# Medien & Icons – Übersicht

Alle Dateien sind SVG, selbst erstellt, frei verwendbar. Sie liegen doppelt:
einmal in `start/` (zum Arbeiten) und einmal in `loesung/` (für die Vorlage).
Du musst nichts herunterladen und nichts umbenennen.

Eine Seite mit allen Dateien zum Anschauen: **[medien.html](medien.html)**
([online ansehen](https://ahsumasearch-afk.github.io/bootstrap-uebungsprojekt/medien.html))

---

## Bilder – `img/`

| Datei | Zeigt | Größe | Wird gebraucht in |
|---|---|---|---|
| `logo.svg` | Logo, helle Schrift | 240 × 48 | Navbar, Footer (dunkler Hintergrund) |
| `logo-dunkel.svg` | Logo, dunkle Schrift | 240 × 48 | Favicon (`<link rel="icon">`) |
| `hero.svg` | Bergpanorama bei Nacht | 1600 × 900 | Hero – als CSS-Hintergrundbild, **nicht** als `<img>` |
| `galerie-1.svg` | Wanderweg am Morgen | 1600 × 800 | Carousel, 1. Bild |
| `galerie-2.svg` | Terrasse mit Aussicht | 1600 × 800 | Carousel, 2. Bild |
| `galerie-3.svg` | Innsbruck bei Nacht | 1600 × 800 | Carousel, 3. Bild |
| `zimmer-schlafsaal.svg` | Etagenbetten, grün | 800 × 560 | Zimmer-Card + Zimmerseite |
| `zimmer-doppel.svg` | Etagenbetten, rot | 800 × 560 | Zimmer-Card + Zimmerseite |
| `zimmer-familie.svg` | Etagenbetten, blau | 800 × 560 | Zimmer-Card + Zimmerseite |
| `aufenthaltsraum.svg` | Gemeinschaftsraum | 800 × 560 | Abschnitt „Das Haus" |
| `fruehstueck.svg` | Frühstücksteller | 800 × 560 | Reserve – in der Lösung nicht verbaut |
| `lage.svg` | Schematische Karte | 800 × 500 | Abschnitt „Anreise" + Kontaktseite |

## Icons – `icons/`

Alle 24 × 48 px Zeichenfläche, Strichstärke 1,8.
Die Farbe steckt **fest in der Datei** – bei `<img>` kann CSS sie nicht ändern.

| Datei | Zeigt | Farbe | Wird gebraucht für |
|---|---|---|---|
| `wlan.svg` | WLAN-Wellen | dunkelblau | Leistung „WLAN inklusive" |
| `fruehstueck.svg` | Tasse mit Dampf | dunkelblau | Leistung „Frühstück" |
| `fahrrad.svg` | Fahrrad | dunkelblau | Leistung „Radverleih" |
| `waschen.svg` | Waschmaschine | dunkelblau | Leistung „Waschküche" |
| `bett.svg` | Bett | dunkelblau | Zimmer-Ausstattung |
| `dusche.svg` | Dusche | dunkelblau | Zimmer-Ausstattung |
| `schluessel.svg` | Schlüssel | dunkelblau | Rezeption, Zimmersafe |
| `berg.svg` | Berggipfel | dunkelblau | Tourenberatung |
| `standort.svg` | Kartennadel | dunkelblau | Adresse |
| `uhr.svg` | Uhr | dunkelblau | Öffnungszeiten, Hinweis-Alert |
| `telefon.svg` | Hörer | dunkelblau | Telefonnummer |
| `mail.svg` | Briefumschlag | dunkelblau | E-Mail-Adresse |
| `stern.svg` | gefüllter Stern | gelb | Bewertungen (5× pro Zitat) |
| `instagram.svg` | Instagram | weiß | Footer |
| `facebook.svg` | Facebook | weiß | Footer |
| `twitter.svg` | Vogel | weiß | Footer |

---

## So bindest du sie ein

### Normales Bild
```html
<img src="img/aufenthaltsraum.svg" alt="Gemeinschaftsraum des Hostels">
```

### Bild, das sich an die Spalte anpasst (Bootstrap)
```html
<img src="img/lage.svg" class="img-fluid rounded-4 shadow-sm" alt="Karte mit der Lage des Hostels">
```
`img-fluid` ist wichtig – ohne das sprengt ein 1600 px breites Bild das Layout.

### Bild in einer Card
```html
<img src="img/zimmer-doppel.svg" class="card-img-top" alt="Doppelzimmer">
```

### Bild im Carousel
```html
<img src="img/galerie-1.svg" class="d-block w-100" alt="Wanderweg oberhalb von Innsbruck">
```

### Logo in der Navbar
```html
<a class="navbar-brand" href="index.html">
  <img src="img/logo.svg" alt="Bergsteiger Hostel" height="36">
</a>
```
Nur `height` setzen, die Breite ergibt sich. Dazu im CSS `.navbar-brand img { width: auto; }`.

### Favicon
```html
<link rel="icon" href="img/logo-dunkel.svg">
```

### Hero-Hintergrund (CSS, nicht HTML!)
```css
.hero {
  background-image: linear-gradient(rgba(12, 28, 44, .55), rgba(12, 28, 44, .75)),
                    url("../img/hero.svg");
  background-size: cover;
  background-position: center;
  min-height: 78vh;
}
```
Der Verlauf liegt **über** dem Bild und macht die weiße Schrift lesbar.
Achte auf `../` im Pfad – die CSS-Datei liegt in `css/`, die Bilder eine Ebene höher.

### Icon neben Text
```html
<div class="d-flex gap-3">
  <img src="icons/standort.svg" alt="" width="24" height="24" class="flex-shrink-0 mt-1">
  <div>
    <h3 class="h6 fw-bold mb-1">Adresse</h3>
    <p class="text-secondary mb-0">Bergweg 14<br>6020 Innsbruck</p>
  </div>
</div>
```

### Fünf Sterne
```html
<div class="mb-2">
  <img src="icons/stern.svg" alt="" width="18" height="18">
  <img src="icons/stern.svg" alt="" width="18" height="18">
  <img src="icons/stern.svg" alt="" width="18" height="18">
  <img src="icons/stern.svg" alt="" width="18" height="18">
  <img src="icons/stern.svg" alt="" width="18" height="18">
</div>
```

---

## Drei Regeln, die oft schiefgehen

**1. Pfade.** Die HTML-Dateien liegen im selben Ordner wie `img/` und `icons/`,
deshalb `src="img/datei.svg"` – ohne führenden Schrägstrich. Nur im CSS gilt
`url("../img/datei.svg")`, weil `style.css` eine Ebene tiefer in `css/` liegt.

**2. Alt-Texte.** Jedes `<img>` braucht ein `alt`. Sagt das Bild etwas aus,
beschreib es. Ist es reine Deko neben Text, der dasselbe sagt (also alle Icons
in diesem Projekt), dann `alt=""` – leer, aber vorhanden.

**3. Breite und Höhe.** Bei Icons immer `width` und `height` mitgeben, sonst
springt das Layout beim Laden. Bei großen Bildern reicht `img-fluid`.

---

## Alles als ZIP

`medien.zip` im Repo enthält beide Ordner (`img/` und `icons/`) zum direkten
Entpacken in ein eigenes Projekt.
