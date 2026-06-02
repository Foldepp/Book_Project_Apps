# Begleit-Apps zur Selbsthilfe-Buchreihe 🌱

Interaktive, offline-fähige Mini-Apps, die je ein Buch der Selbsthilfe-Reihe begleiten.
Pro Buch **ein emotionaler Bogen**: eine Symbolfigur (= die Leserin) reist mit einer
warmen, namenlosen Begleit-Stimme durch eine ruhige Geschichte, in die — bewusst
unbenannt — beruhigende Selbstregulations-Übungen eingewoben sind.

Die App ist das **Erlebnis** (ein geführtes Durchleben, geschenkhaft, offline auf dem
Homescreen). Die *vollständige* Übungs- und Meditationssammlung lebt weiterhin auf der
kostenlosen Begleitseite zum Buch — die App dupliziert sie bewusst nicht, sondern
verweist am Ende sanft darauf.

> Dieses Repo ist ein **frischer Start** für die App-Reihe. Die erste, abgeschlossene
> App „Wieder fliegen“ (Flugangst) liegt in ihrem **eigenen Repo** und bleibt dort
> unverändert — sie ist hier nur als **Stil-Referenz** (`wieder-fliegen.html`) enthalten.

-----

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | **Bd. 1 – Selbstwert:** „Der Baum, der wachsen darf" (aktueller Prototyp, zugleich Pages-Startseite) |
| `wieder-fliegen.html` | Stil-/Mechanik-**Referenz** (abgeschlossenes Erst-Projekt, nur als Vorlage) |
| `Konzept-Begleit-Apps.md` | wiederverwendbare **Blaupause** für neue Themen/Apps |
| `CLAUDE.md` | Kontext + Arbeitsanweisungen für künftige Claude-Sessions — **zuerst lesen** |

-----

## Eine neue Buch-App bauen (Kurzfassung)

1. **Einen Bogen wählen** (nicht das ganze Buch): einen Kern-Transformations-Moment.
2. **Symbolfigur + Begleiter festlegen** (Tier/Naturbild = Leserin; warme namenlose Stimme).
3. Eine vorhandene App als Vorlage kopieren und **nur den Inhalt** anpassen:
   - das `pages`-Array (chapter / line / voice / prompt / mode),
   - das `words`-Array (Halte-Worte),
   - die Farbwelt (CSS-Variablen im `:root`),
   - die Symbol-Grafik (CSS).
4. **Sicherheits-Leitplanken** aus `CLAUDE.md` / der Blaupause respektieren.
5. Am Ende sanft auf die kostenlose Begleitseite zum Buch verweisen.

> Geplanter nächster Ausbauschritt: Engine und Inhalt sauber trennen, sodass eine neue
> Buch-App nur noch ein Content-Objekt braucht (siehe `CLAUDE.md`).

-----

## Hosten über GitHub Pages

1. Settings → Pages → Source: Branch `main`, Ordner `/ (root)` → Save.
2. Die Reihe ist dann erreichbar unter `https://<user>.github.io/<repo>/` (zeigt `index.html`).
3. Weitere Apps liegen als zusätzliche `.html`-Dateien daneben (z. B.
   `https://<user>.github.io/<repo>/wieder-fliegen.html`).
4. **Hinweis:** GitHub Pages auf kostenlosen Accounts benötigt ein **öffentliches** Repo.
   Dieses Repo darf zum Entwickeln privat bleiben; zum Veröffentlichen auf „public" stellen.

-----

## Bitte beachten

Die Apps sind eine warme Ergänzung, **kein Ersatz** für Therapie oder einen Notfallplan.
Sie regulieren und erden — sie bearbeiten kein Trauma. Designprinzipien und
Sicherheits-Leitplanken stehen in `CLAUDE.md` und `Konzept-Begleit-Apps.md`.
