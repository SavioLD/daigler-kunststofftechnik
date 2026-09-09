# Daigler Kunststofftechnik – Karriereseite

Recruiting-Landingpage (Ad-Funnel) für die Daigler Kunststofftechnik GmbH
(Trochtelfingen-Steinhilben). Aktuelle Stelle: **Verfahrensmechaniker (m/w/d)**
für Kunststoff- und Kautschuktechnik.

Aufbau 1:1 an der ALWA-Karriereseite orientiert – in eigenem Daigler-CI (Grün,
abgeleitet aus der Stellenanzeige) und als schlanker Single-Position-Funnel
(2 Schritte statt 3).

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert

## Konfiguration

Im `<script>`-Bereich von `index.html` ganz oben steht:

- `WEBHOOK_URL` – LeadTable-Generic-Webhook der Daigler-Tabelle
  (`api-v2.lead-table.com/api/webhook/generic/…`). Bewerbungen landen damit
  direkt in LeadTable. Bei einem Fehler sieht der Bewerber den Hinweis, sich
  direkt an `info@daigler-gmbh.de` zu wenden. Übergebene Felder: `vorname`,
  `nachname`, `email`, `telefon`, `stelle`, `erfahrung`, `fuehrerschein`,
  `deutschniveau`, `schicht`, `datenschutz`, `quelle`, `seite` – ggf. in
  LeadTable den Spalten zuordnen.

## Vorfilter (Qualifizierung)

4 Qualifizierungsfragen vor den Kontaktdaten: **Erfahrung, Führerschein,
Deutschniveau, Schichtbereitschaft**. Jede Antwort hat Punkte (0 = schwächste
Passung). Liegt die Gesamtpunktzahl unter dem Schwellwert `SCREEN_MIN` (in
`index.html`, Standard = 2) – praktisch also nur, wenn jemand **durchweg die
schwächsten** Antworten wählt – erscheint eine **freundliche Absage** und es
wird **kein Lead** an LeadTable gesendet. Motivierte Quereinsteiger:innen (z. B.
ohne Erfahrung, aber schichtbereit und mit ausreichend Deutsch) kommen durch.
Schwellwert/Punkte lassen sich oben im Script (`SCORE`, `SCREEN_MIN`) anpassen.

Kein Lebenslauf-Upload: Der CV wird bewusst nicht abgefragt (kein Backend nötig,
keine Wartung). Der Lebenslauf wird im persönlichen Erstkontakt geklärt.

## Bilder (Hero-Foto & Logo)

Optionale Dateien gehören in einen Ordner **`bilder/`** im Repo-Root. Fehlt eine
Datei, bleibt der grüne Farbverlauf bzw. der Text-Schriftzug stehen (nichts
bricht).

- `bilder/hero.jpg` oder `bilder/verfahrensmechaniker.jpg` – Hero-Foto
  (Querformat, mind. ~1600 px breit, Motiv rechts platzieren – links liegt die
  Textfläche).
- `bilder/daigler-logo.svg` / `.png` – Logo für Topbar (dunkel auf hell).
- `bilder/daigler-logo-weiss.svg` / `.png` – helles Logo für Hero & Footer.

## CI / Design

- **Farben** (aus der Stellenanzeige abgeleitet): Smaragdgrün `#2d8a6f`,
  Tannengrün `#12463a`, Salbeigrün-Akzent `#9cc3b3`.
- **Font**: Manrope (Google Fonts).
- Struktur, Sektionen und Bewerbungs-Funnel wie bei der ALWA-Vorlage.

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/root`.
2. Nach ein paar Minuten ist die Seite unter
   `https://<user>.github.io/daigler-kunststofftechnik/` erreichbar
   (bzw. unter der hinterlegten Custom-Domain).

## Bewerbungen (Leadtable)

Jede abgeschlossene Bewerbung wird per Webhook an Leadtable gesendet
(Felder u. a. `vorname`, `nachname`, `telefon`, `email`, `stelle`,
`erfahrung`, `fuehrerschein`, `deutschniveau`, `quelle`). Der Webhook ist in
`index.html` in der Variable `WEBHOOK_URL` hinterlegt.
