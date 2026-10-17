# guild-theme

Jekyll-Theme der Open Architecture Guild. Enthält nur das Aussehen: Layouts, Includes, Stylesheet und Favicon. Die Texte liegen in der Seite, die das Theme nutzt (`_data/`). Keine Schriften, Skripte oder Bilder von Dritten, Hell- und Dunkelmodus automatisch.

## Verwenden (GitHub Pages)

In der `_config.yml` der Seite:

```yaml
remote_theme: Open-Architecture-Guild/guild-theme@v0.1.0   # Tag statt main: Änderungen am Theme wirken erst nach Umstellen
plugins:
  - jekyll-remote-theme
```

GitHub Pages baut die Seite dann selbst, eine eigene Action ist nicht nötig. Während der Entwicklung kann `@main` verwendet werden.

## Inhalt

```
_layouts/default.html   Rahmen: Kopf, Hinweisband, Inhalt, Fuß
_layouts/home.html      Startseite, vollständig aus _data/home.yml
_layouts/page.html      Textseiten (Impressum, Datenschutz, Platzhalter)
_includes/              head, header, notice, footer, logo
assets/css/guild.css    Alle Farben und Maße als Variablen in :root
assets/img/favicon.svg
```

## Was die Seite liefern muss

`_config.yml`: `title`, `tagline`, `description`, `lang`, `url`, `repository` (für den Link „Auf GitHub bearbeiten“).

`_data/navigation.yml`: `main` als Liste mit `title`, `url`, optional `button: true`.
`_data/notice.yml`: `enabled`, `tag`, `text`, optional `link_title`, `link_url`.
`_data/footer.yml`: `about`, `columns` (je `title` und `links`), `note`, optional `edit_title`.
`_data/home.yml`: Abschnitte `hero`, `preview`, `entries`, `status`, `projects`, `principles`, `participate`, `decisions`, `disclaimer`. Das Beispiel steht in `site/_data/home.yml`.

Front Matter einer Seite: `layout`, `title`, optional `description`, `noindex: true`, `edit_path`.

Links in den Daten: Pfade mit `/` oder `#` am Anfang werden an `baseurl` angepasst, alles mit `:` (https:, mailto:) bleibt unverändert.

## Anpassen

Farben und Maße stehen am Anfang von `assets/css/guild.css`. Schriften: Newsreader und Atkinson Hyperlegible Next sind eingetragen, aber nicht mitgeliefert; ohne Dateien fällt die Seite auf Systemschriften zurück. Zum Selbsthosten Fontsource-Pakete (SIL OFL) nach `assets/fonts/` legen und per `@font-face` einbinden, nicht von einem CDN laden.

Lizenz: noch nicht festgelegt (ADR-0001), bis dahin wie die anderen Repos der Organisation vorläufig MIT. Eine `LICENSE`-Datei liegt noch nicht bei.
