# CLAUDE.md — Begleit-Apps zur Selbsthilfe-Buchreihe

Kontext für künftige Claude-Sessions. Bitte zuerst vollständig lesen.

Dieses Repo bündelt interaktive Begleit-Apps zu einer **Selbsthilfe-Buchreihe**
(Bd. 1 = Selbstwert). Pro Buch gibt es **eine** App, die **einen** emotionalen Bogen
erlebbar macht. Es ist ein eigenständiges, frisches Projekt; das abgeschlossene
Erst-Projekt „Wieder fliegen" (Flugangst) lebt in einem separaten Repo und bleibt dort
unverändert — hier liegt es nur als Stil-Referenz (`wieder-fliegen.html`).

-----

## Produktversprechen (wichtig: nicht die Gratis-Webseite duplizieren)

Zu jedem Buch gibt es bereits eine **kostenlose Webseite mit ALLEN Übungen &
Meditationen**. Die App ist **kein** Nachschlagewerk, sondern das **Erlebnis**:

- Webseite = Werkzeugkiste (vollständig, zum Auswählen/Nachschlagen).
- App = ein geführtes, schönes Durchleben **eines** Bogens; intim, geschenkhaft, offline.

Die App verweist am Ende **sanft** auf die Webseite, statt Inhalte zu wiederholen.

-----

## Der wiederkehrende Bauplan (Buch → App)

Pro Buch genau **ein** Kern-Transformations-Bogen (nicht das ganze Buch):

1. **Symbolfigur = die Leserin.** Tier/Naturbild, das das Thema spiegelt. Tipp: ein
   grammatisch **weibliches** Substantiv wählen (z. B. „die Birke"), dann sind die
   Pronomen mühelos „sie".
2. **Begleiter = warme, namenlose Stimme.** Bei einem Buchprodukt die mitfühlende innere
   Stimme (nicht eine konkrete Person). Erklärt in 1–2 warmen Sätzen das „Warum".
3. **Bogen in ~7 Seiten:** Mangel/Schmerz → Begleiter erklärt warm → 1–3 eingewobene
   Übungen → ein **behaltbarer Satz** am Ende.
4. **Immer erreichbarer Ruhe-Anker** (Knopf), der ohne Druck in eine Mini-Beruhigung führt.
5. **Sicherheits-Footer:** kein Therapieersatz, „nutz nur, was sich gut anfühlt".

-----

## Technische Eckpfeiler (Stand: Prototyp)

- **Eine einzige offline-fähige `.html` pro App**, kein externes Laden, kein Build-Tool.
- Reines HTML/CSS/JS in einer IIFE (`(() => { … })()`).
- **Kein `localStorage`** in dieser Variante (kurze Reise, in einem Zug). Falls Persistenz
  gewünscht: immer `try/catch` mit `mem{}`-Fallback (In-App-Browser werfen sonst).
- Farbpalette als **CSS-Variablen im `:root`** (pro Buch eigene Farbwelt).
- **Grafik ist reines CSS** (keine externen Bilder).
- Höhen mit **`dvh`** + `env(safe-area-inset-*)`; `prefers-reduced-motion` respektieren.

### Datenmodell (flaches Array `const pages`)

```
{ chapter:'Überschrift', line:'Erzähltext', voice:'Die Stimme sagt: …',
  prompt:'Halte-Geste-Label', mode:'roots'|'space'|'light' }
```

- `mode` setzt die Szene-Klasse `book.mode-<mode>` und steuert die Animation.
- Persönlicher/inhaltlicher Text steckt komplett im `pages`-Array und im `words`-Array
  (die Halte-Worte). Nur dort wird angepasst.

### Mechanik (unbenannt eingewoben)

- **Halte-Geste (`gesture-pad`):** Finger halten → Szene bekommt `holding active-motion`
  (Symbol „wächst", Anker glüht), `words` zyklen alle ~950 ms. Erdung/Ressource (SE).
- **`mode:'light'`:** ein warmer, ruhiger Lichtpuls — für Selbstmitgefühl-Seiten
  (z. B. Hand aufs Herz). In „Wieder fliegen" wandert in diesem Modus ein Licht
  links↔rechts (entschärftes Augenfolgen/EMDR) — je nach Thema das eine oder andere.
- **`mode:'space'`:** „den Raum wieder weit werden lassen" bei Reizflut / lauter Stimme.
- **Ruhe-Anker-Knopf:** springt auf die Beruhigungs-/Selbstmitgefühl-Seite.

### Wichtige Funktionen (in der IIFE)

`buildStars()`, `buildDots()`, `render()`, `go(delta)`, `startHold(event)`/`stopHold()`,
und der Ruhe-Anker-Sprung (`restMode`/`threadMode`).

-----

## Aktuelle Apps

- **`index.html` — Bd. 1 Selbstwert: „Der Baum, der wachsen darf"** (Prototyp).
  Junge Birke = Leserin; warmes Licht/Sonne = namenlose Begleit-Stimme; Wurzeln als
  Lichtfaden. 7-Seiten-Bogen: Im Schatten der Großen → Wurzeln, die schon da sind → Die
  laute Stimme (innerer Kritiker) → Was schon getragen hat → Die Hand, die hält (Hand aufs
  Herz) → Dem Licht entgegen → Der Satz, der bleibt („Ich darf da sein"). Ruhe-Anker:
  „Nur atmen".
- **`wieder-fliegen.html`** — abgeschlossenes Erst-Projekt (Flugangst), nur als
  Stil-/Mechanik-Referenz. Nicht weiterentwickeln; das Original liegt in eigenem Repo.

-----

## Geplanter Ausbau: Engine + Content trennen

Statt jede App handzucoden, lohnt eine datengetriebene Vorlage: **eine wiederverwendbare
Engine** (HTML/CSS/JS-Renderer) + pro Buch ein **`BOOK`-Content-Objekt**
(Palette, Symbolfigur, Begleiter, Seiten, gewählte Übungen, Schluss-Satz, Footer,
Webseiten-Link). Dazu eine kleine, parametrisierbare **Übungs-Bibliothek**
(Atem, Halte-Anker, Augenfolgen, 5-4-3-2-1, Hand aufs Herz, sicherer Ort, Werte-Anker)
und ein fest eingebauter **Sicherheits-Layer**. Dann = neue Buch-App nur noch ein
Content-Objekt ausfüllen. Für „App Store" später als PWA (Manifest + Service-Worker)
bzw. dünner WebView-Wrapper.

-----

## Sicherheits- / Sorgfaltshinweise (zwingend)

- **Regulieren, nicht prozessieren.** Kein Trauma-Processing, kein tiefes „Reinfühlen",
  keine ungesteuerte bilaterale Stimulation. Alles im Wohlfühl-Fenster.
- **Immer überspringbar, nie Druck.** Kein „du musst", keine Timer-Hetze.
- Heikle Themen (Selbstwert, Scham, innerer Kritiker) **behutsam**, kein Flooding.
- **Kein Ersatz für Therapie/Notfallplan** — beim Verschenken klar dazusagen.
- Bei Krisen-/Means-Themen keine Methoden/Details nennen.
- Wenn sich beim Schreiben etwas „zurechtgebogen" anfühlt → Stopp-Signal.

Siehe auch `Konzept-Begleit-Apps.md` (ausführliche Blaupause) im selben Repo.
