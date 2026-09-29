# Bootstrap-5-Spickzettel

Die Klassen, die du in diesem Projekt brauchst. Die vollständige Doku steht
unter <https://getbootstrap.com/docs/5.3/> – dieser Zettel ist die Abkürzung.

## Die Breakpoints

| Kürzel | ab Breite | gemeint ist |
|---|---|---|
| *(keins)* | 0 | Handy, der Standard |
| `sm` | 576px | großes Handy |
| `md` | 768px | Tablet |
| `lg` | 992px | Laptop |
| `xl` | 1200px | großer Bildschirm |

**Wichtig:** Bootstrap ist *mobile first*. `col-md-6` heißt „ab 768px halbe Breite" –
darunter gilt automatisch volle Breite. Du schreibst also immer nur, ab wann sich
etwas ändert.

## Raster

```html
<div class="container">          <!-- zentriert, mit Rand -->
  <div class="row g-4">          <!-- Zeile, g-4 = Abstand zwischen den Spalten -->
    <div class="col-12 col-md-6 col-lg-4">Spalte</div>
  </div>
</div>
```

| Klasse | Wirkung |
|---|---|
| `container` | feste Maximalbreite pro Breakpoint |
| `container-fluid` | immer volle Breite |
| `row` | Zeile, braucht `col-*` als Kinder |
| `col` | teilt den Platz gleichmäßig auf |
| `col-6` | 6 von 12 Spalten = halbe Breite |
| `g-4` / `gx-4` / `gy-4` | Abstand: beide Richtungen / nur waagerecht / nur senkrecht |
| `order-lg-2` | Reihenfolge ab `lg` tauschen |
| `offset-md-2` | 2 Spalten Platz davor lassen |

## Abstände

Muster: `{Eigenschaft}{Seite}-{Größe}`

- Eigenschaft: `m` = margin, `p` = padding
- Seite: `t` oben, `b` unten, `s` links, `e` rechts, `x` links+rechts, `y` oben+unten, nichts = alle
- Größe: `0` bis `5`, oder `auto`

Beispiele: `py-5` (viel Luft oben und unten), `mb-3`, `mt-0`, `ms-auto` (schiebt nach rechts), `px-4`

## Flexbox

| Klasse | Wirkung |
|---|---|
| `d-flex` | Flex-Container |
| `flex-column` | untereinander statt nebeneinander |
| `flex-wrap` | umbrechen, wenn kein Platz mehr ist |
| `justify-content-between` | Platz dazwischen verteilen |
| `justify-content-center` | mittig |
| `align-items-center` | senkrecht mittig |
| `gap-3` | Abstand zwischen den Kindern |
| `ms-auto` | einzelnes Element nach rechts schieben |

## Anzeigen und Verstecken

| Klasse | Wirkung |
|---|---|
| `d-none` | ausblenden |
| `d-none d-md-block` | erst ab Tablet anzeigen |
| `d-md-none` | ab Tablet ausblenden |
| `text-md-end` | Text erst ab Tablet rechtsbündig |
| `visually-hidden` | nur für Screenreader sichtbar |

## Farben

`primary secondary success danger warning info light dark`

| Muster | Beispiel |
|---|---|
| Hintergrund | `bg-primary`, `bg-light`, `bg-warning-subtle` |
| Text | `text-secondary`, `text-white`, `text-danger` |
| Button | `btn btn-primary`, `btn btn-outline-secondary` |
| Badge | `badge text-bg-success` |
| Rahmen | `border border-primary` |

## Text

`fw-bold` `fw-normal` · `fst-italic` · `small` · `lead` · `display-4`
`text-center` `text-end` · `text-uppercase` · `text-truncate`
`h1`–`h6` als *Klasse*: macht ein `<h3>` so groß wie eine `<h1>`, ohne die Struktur kaputtzumachen.

## Rahmen, Ecken, Schatten

`border` `border-0` · `rounded` `rounded-3` `rounded-4` `rounded-circle`
`shadow-sm` `shadow` `shadow-lg` · `overflow-hidden` · `w-100` `h-100`

## Komponenten in diesem Projekt

### Navbar
```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark sticky-top">
  <div class="container">
    <a class="navbar-brand" href="#">Logo</a>
    <button class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#menue">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="menue">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item"><a class="nav-link active" href="#">Start</a></li>
      </ul>
    </div>
  </div>
</nav>
```
`navbar-expand-lg` = ab 992px ausgeklappt. Die `id` im `data-bs-target` muss zum `div` passen.

### Card
```html
<div class="card h-100 border-0 shadow-sm">
  <img src="…" class="card-img-top" alt="…">
  <div class="card-body">
    <h3 class="h5 card-title">Titel</h3>
    <p class="card-text">Text</p>
  </div>
  <div class="card-footer bg-white border-0">Fuß</div>
</div>
```
`h-100` sorgt dafür, dass alle Karten einer Zeile gleich hoch sind.

### Carousel
```html
<div id="galerie" class="carousel slide" data-bs-ride="carousel">
  <div class="carousel-indicators">
    <button data-bs-target="#galerie" data-bs-slide-to="0" class="active"></button>
  </div>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="…" class="d-block w-100" alt="…">
      <div class="carousel-caption d-none d-md-block">…</div>
    </div>
  </div>
  <button class="carousel-control-prev" data-bs-target="#galerie" data-bs-slide="prev">
    <span class="carousel-control-prev-icon"></span>
  </button>
</div>
```

### Accordion
```html
<div class="accordion" id="fragen">
  <div class="accordion-item">
    <h3 class="accordion-header">
      <button class="accordion-button collapsed" data-bs-toggle="collapse" data-bs-target="#f1">Frage</button>
    </h3>
    <div id="f1" class="accordion-collapse collapse" data-bs-parent="#fragen">
      <div class="accordion-body">Antwort</div>
    </div>
  </div>
</div>
```
`data-bs-parent` sorgt dafür, dass immer nur eine Antwort offen ist.
Die erste offene bekommt `show` am `collapse` und **kein** `collapsed` am Button.

### Modal
```html
<button data-bs-toggle="modal" data-bs-target="#meinModal">Öffnen</button>

<div class="modal fade" id="meinModal" tabindex="-1">
  <div class="modal-dialog modal-dialog-centered">
    <div class="modal-content">
      <div class="modal-header">
        <h2 class="modal-title h5">Titel</h2>
        <button class="btn-close" data-bs-dismiss="modal"></button>
      </div>
      <div class="modal-body">Inhalt</div>
      <div class="modal-footer">…</div>
    </div>
  </div>
</div>
```

### Tabelle
`table` `table-striped` `table-hover` `table-bordered` `align-middle`
In `<div class="table-responsive">` einpacken, damit sie auf dem Handy scrollt.

### Formular
```html
<form class="row g-3 needs-validation" novalidate>
  <div class="col-md-6">
    <label for="name" class="form-label">Name</label>
    <input type="text" class="form-control" id="name" required>
    <div class="invalid-feedback">Bitte ausfüllen.</div>
  </div>
</form>
```
`form-control` für Eingabefelder, `form-select` für Auswahllisten,
`form-check` + `form-check-input` für Checkboxen.
Die Fehlermeldungen erscheinen erst, wenn das Formular die Klasse `was-validated` hat.

### Weitere Kleinteile
`alert alert-warning` · `badge text-bg-info` · `breadcrumb` + `breadcrumb-item` ·
`list-unstyled` · `list-group` + `list-group-item` · `btn-close`

## Bootstrap umfärben

Nicht die Bootstrap-Datei ändern und nicht alles mit `!important` erschlagen.
Der saubere Weg sind die CSS-Variablen, die Bootstrap selbst benutzt:

```css
/* global */
:root { --bs-link-color: #1d3b53; }

/* nur in einer Komponente */
.btn-berg { --bs-btn-bg: #1d3b53; --bs-btn-hover-bg: #2c5573; --bs-btn-color: #fff; }
.accordion { --bs-accordion-active-bg: rgba(29,59,83,.07); }
.table-berg { --bs-table-bg: #1d3b53; --bs-table-color: #fff; }
```

Welche Variable eine Komponente benutzt, steht in der Doku unter „CSS variables"
oder findest du im Browser mit F12 → Elements → Computed.
