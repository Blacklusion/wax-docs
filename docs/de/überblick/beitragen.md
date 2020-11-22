# Zur Dokumentation beitragen:
Derzeit sind alle Informationen zur WAX Blockchain über die verschiedenen Gilden-Webseiten verteilt.
Diese Dokumentation ist ein Versuch, alle Inhalte, die bereits veröffentlicht wurden und alle zukünftigen Artikel, die noch veröffentlicht werden, auf einer einzigen Platform zu zentralisieren.

> Ein Beitrag wäre daher sehr willkommen und kann einfach über GitHub durchgeführt werden. Es ist ebenfalls möglich existierende Artikel in eine andere Sprache zu übersetzen.

# Best Practices: <!-- {docsify-ignore} -->
## Ordner Struktur
Alle Artikel werden im Ordner **docs/** des Repositorys gespeichert. Dieser Ordner enthält mehrere Ordner für die verschiedenen Sprachen, in denen die Dokumentation derzeit verfügbar ist. Wähle den gewünschten **Sprachordner** oder erstelle bei Bedarf einen neuen.

Wähle nun den passenden **Kategorienordner** oder erstelle bei Bedarf eine neue Kategorie. Speichere in diesem den Artikel mit "-" anstelle von Leerzeichen ab. Die URLs werden auf der Grundlage des Dateinamens erstellt, daher sollten diese über alle Artikel hinweg konsistent sein.

Falls der Artikel **Bilder** enthält: In jedem Kategorienordner befindet sich ein **media/** Ordner. Erstelle in diesem Ordner einen neuen Unterordner mit dem genauen Namen des Artikels. Innerhalb dieses Ordners kann ein beliebiges Schema verwendet werden, nach welchem die Bilder benannt werden.
```
.
└── docs/
    ├── index.md
    └── sprache (e.g. de)/
        ├── _sidebar.md
        └── Kategorie (e.g. Sicherheit)/
            ├── dein-artikel.md
            └── media/
                 └── dein-artikel/
                      ├── img01.png
                      └── img02.png
```


## Überschriften richtig verwenden
In der Seitenleiste wird automatisch das Inhaltsverzeichnis des Artikels angezeigt. Dieses wird auf der Grundlage der H1- und H2-Überschriften erstellt. Wenn Du also Deinen Artikel schreibst, solltest Du daran denken, wichtige Abschnitte mit einer H1- oder H2-Überschrift hervorzuheben. So kann der Leser direkt zu diesem Abschnitt springen. Bitte **vermeide** die Verwendung von ":" nach der Überschrift, da Doppelpunkte in der Seitenleiste unschön aussehen.

Falls eine der Überschriften nicht in der Seitenleiste angezeigt werden soll, kann diese mit der folgenden Zeile ignoriert werden:

```markdown
# Dein Artikel

## Überschrift <!-- {docsify-ignore} -->

Diese Überschrift wird nicht in der Seitenleiste angezeigt.
```

Wenn alle Überschriften ignoriert werden sollen, kann auch folgende Zeile einmalig verwendet werden:

```markdown
# Dein Artikel <!-- {docsify-ignore-all} -->

## Überschrift

Diese Überschrift wird nicht in der Seitenleiste angezeigt.
```

## Seitenleiste
Wie bereits erwähnt, wird das Inhaltsverzeichnis des Artikels automatisch erstellt und in der Seitenleiste angezeigt. Zuerst muss der Artikel allerdings zu der Seitenleiste hinzugefügt werden. In jedem Sprachordner befindet sich eine **_sidebar.md** Datei:
```
.
└── docs/
    ├── index.md
    └── sprache (e.g. de)/
        └── _sidebar.md
```
Öffne diese Datei und füge wie folgt deinen Artikel hinzu:
```markdown
<!-- docs/_sidebar.md -->

- Overview
  - [Contributing to the Docs](contribute.md "How to contribute to the WAX Docs")

- Getting started
  - [chains.json](en/getting-started/chains-json.md "How to create a chains.json")
  - [bp.json](en/getting-started/bp-json.md "How to create a bp.json for WAX")
  - [Pushing bp.json on chain](en/getting-started/pushing-bp-json-onchain.md "How to push your bp.json on-chain")
```
Zusätzlich, kann nach dem Namen des Artikels auch ein Titel angegeben werden. Dieser Titel wird nicht auf der Doc-Seite angezeigt. Er wird nur für SEO-Zwecke verwendet und ermöglicht es, festzulegen, wie der Artikel in einer Vorschau angezeigt werden sollen.

## Andere Artikel verlinken
Wenn andere Artikel verlinkt werden, sollten unbedingt relative Links verwendet werden, da dies z.B. eine einfache Änderung des Domainnamens in der Zukunft ermöglicht. Artikel können verlinkt werden, indem das folgende Format verwendet wird:
```markdown
Das ist ein [Link](/de/sicherheit/anderer-artikel) zu einem anderen Artikel.
```
> Verlinke bitte so viele andere Artikel wie möglich

## Code Blöcke richtig verwendet
Markdown bietet die Möglichkeit, die Sprache des Codeblocks festzulegen. Die Doc-Seite unterstützt Syntax-Highlighting. Basierend auf der Sprache, die zu Beginn des Codeblocks angegeben wird, wird der Code automatisch farbig markiert. Eine Sprache kann mit folgendem Format angegeben werden:

<pre>
```javascript
/**
 * Code hier
 */
```
</pre>

## Immer "Hilfreiche Links" hinzufügen
Jeder Artikel sollte mit dem Abschnitt **Hilfreiche Links** enden. Hierfür bitte ebenfalls den Doppelpunkt aussparen und beiden Wörter mit einem großen Buchstaben beginnen. Dies ist ein Standard, den ich gerne etablieren würde: Die Idee ist, dass der Leser schnell andere Artikel zu ähnlichen Themen, Links zu Repositories oder Websites finden kann, die bei der Lösung des im Artikel besprochenen Problems helfen können. Hier können auch gerne eigene Produkte verlinkt werden, solange es Sinn macht.


## Hilfreiche Links
- [Markdown Cheetsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
