# Daigler Kunststofftechnik – Karriereseite

Recruiting-Landingpage (Ad-Funnel) für die Daigler Kunststofftechnik GmbH
(Trochtelfingen-Steinhilben). Aktuelle Stelle: **Verfahrensmechaniker (m/w/d)**
für Kunststoff- und Kautschuktechnik.

Aufbau 1:1 an der ALWA-Karriereseite orientiert – in eigenem Daigler-CI (Grün,
abgeleitet aus der Stellenanzeige) und als schlanker Single-Position-Funnel
(2 Schritte statt 3).

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an (nur nötig, wenn CV-Upload aktiviert wird)
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert

## Vor dem Live-Schalten (WICHTIG)

Im `<script>`-Bereich von `index.html` ganz oben stehen die Konfigurationswerte:

- `WEBHOOK_URL` – aktuell `PLACEHOLDER_DAIGLER_LEADTABLE_WEBHOOK`.
  **Muss durch den Daigler-eigenen Leadtable-Webhook ersetzt werden**, sonst
  landen die Bewerbungen nirgends. Solange der Platzhalter steht, sieht der
  Bewerber im Fehlerfall den Hinweis, sich direkt an `info@daigler-gmbh.de` zu
  wenden.
- `SUPABASE_URL` / `SUPABASE_KEY` – optional. Leer lassen, wenn kein
  CV-Upload gewünscht ist (der Upload wird dann sauber übersprungen, das
  Formular funktioniert trotzdem). Für den Upload ein eigenes Supabase-Projekt
  anlegen und `supabase-bewerbungen.sql` einmalig ausführen.

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
(Felder u. a. `stelle`, `erfahrung`, `vorname`, `nachname`, `telefon`,
`email`, `lebenslauf`, `quelle`). Der Webhook ist in `index.html` in der
Variable `WEBHOOK_URL` hinterlegt.
