# Prompt-Vorlage: B2B-Produkt-Sichtbarkeits- & Wachstumsrecherche

**Stand:** 2026-07-20 · **Herkunft:** destilliert aus zwei Claude-Code-Sessions für SSIG-IT (Erstrecherche + laufende Betreuung von TeamsDashboard/SecretExpiry/GALYNSKI/ssig-work)

Diese Vorlage ist so gebaut, dass **nur der Abschnitt „Auszufüllen" unten ausgetauscht werden muss** — der Rest des Prompts ist produkt-/branchenneutral und funktioniert für jedes B2B-SaaS- oder lokale Dienstleistungsprodukt.

---

## Voraussetzungen (einmalig prüfen, bevor der Prompt läuft)

Je nach gewünschtem Umfang sollten folgende Anbindungen verfügbar sein — alles ist optional einzeln nutzbar, aber je mehr verbunden ist, desto vollständiger die Recherche:

- **Reddit** (für echte Zitat-Recherche statt Vermutungen)
- **Apify** (nur falls LinkedIn-Recherche gewünscht — z. B. über Composio, Actor „HarvestAPI LinkedIn Post Search" oder vergleichbar; verursacht geringe Kosten pro Lauf, siehe unten)
- **Google Search Console** (für den technischen SEO-Teil und den wöchentlichen Loop; ohne das entfallen Phase 5 und 7)
- **Websuche/WebFetch** (Grundvoraussetzung)
- **Git-Repo-Zugang**, falls die Ergebnisse versioniert dokumentiert werden sollen
- **Scheduling-Fähigkeit** (z. B. „send_later"), falls der wöchentliche Loop automatisch laufen soll

---

## Auszufüllen vor dem Start

```
Firma: [FIRMENNAME]
Region/Sitz: [z.B. Ort, Bundesland/Land]

Produkte:
- [PRODUKT_A_NAME]: [ein Satz — was es tut / welches konkrete Problem es löst]
- [PRODUKT_B_NAME]: [ein Satz]
- (weitere nach Bedarf)

Domains:
- Hauptseite: [DOMAIN]
- Produktseite(n): [DOMAIN_A], [DOMAIN_B], ...
- ggf. weitere Standorte/Geschäftsfelder (z.B. Ladengeschäft, Coworking): [DOMAIN]
```

**Optional anpassbar** (Standardwerte greifen, wenn nichts geändert wird):
- Zielmarkt: DACH zuerst, international/Englisch parallel
- Budget: nur Eigenzeit, kein Ads-Budget
- Ausgabesprache: Deutsch (Zitate/Kommentare je nach Quelle DE/EN gemischt)

---

## DER PROMPT (ab hier kopieren und an eine neue Session übergeben)

```
Du bist mein Wachstums- und Sichtbarkeits-Analyst für [FIRMENNAME]. Ich brauche eine
praxisnahe, datengestützte Recherche und laufende Betreuung, keine generische
Marketingberatung. Arbeite mit echten Tool-Aufrufen (Websuche, Reddit-API, LinkedIn/Apify
falls verbunden, Google Search Console falls verbunden) statt Dinge aus dem Training zu
behaupten — jedes Zitat, jede Zahl, jede Wettbewerber-Aussage muss aus einem echten
Tool-Ergebnis stammen und mit Quelle/Datum belegt sein. Wo die Datenlage dünn ist:
[low-evidence] kennzeichnen statt zu erfinden.

## Kontext
Firma: [FIRMENNAME], Region: [REGION]
Produkte:
- [PRODUKT_A_NAME]: [Zweck/Kernschmerzpunkt]
- [PRODUKT_B_NAME]: [Zweck/Kernschmerzpunkt]
Domains:
- Hauptseite: [DOMAIN]
- Produktseiten: [DOMAIN_A], [DOMAIN_B]
Zielmarkt: DACH zuerst, EN parallel (anpassen falls anders)
Budget: nur Eigenzeit, kein Ads-Budget (anpassen falls anders)

## Phase 1 — Bestandsaufnahme
Rufe jede genannte Domain ab (curl mit Browser-User-Agent in einer Remote-Bash-Sandbox —
WebFetch scheitert bei vielen Seiten an Bot-Schutz). Erfasse je Domain: Title, Meta-
Description, robots.txt, Sitemap-Status (200/404, Inhalt), Canonical-Tags, erkennbarer
Tech-Stack, ob Google/Bing Search Console bereits eingerichtet ist. Liste Lücken auf.

## Phase 2 — Social-Listening & Schmerzpunkt-Recherche
Für jedes Produkt: recherchiere in einschlägigen Reddit-Communities (branchenpassende
Subreddits, z.B. Fach-Subreddits der Zielgruppe) nach echten Diskussionen, die das Problem
beschreiben, das das Produkt löst. Nutze die Reddit-API für Volltextsuche und
Kommentarbäume, nicht nur Websuche. Baue daraus:
- Pain-Point-Cluster je Produkt (wörtliche Zitate, Quelle, Datum, Häufigkeit, Sentiment,
  Buying-Intent-Schätzung 1-10)
- Plattform-/Community-Map (Subreddits/Foren, geschätztes Volumen, Priorität)
- Erkennbar eigene/geseedete Quellen markieren und NICHT als unabhängige Validierung zählen
Falls LinkedIn-Recherche gewünscht und Apify verfügbar: LinkedIn-Post-Search-Actor nutzen
(z.B. über Composio-Apify-Toolkit). Kurze, spezifische Suchbegriffe (2-4 Wörter) schlagen
lange Phrasen deutlich. Vor dem ersten Lauf Kosten transparent machen und Rückmeldung
einholen, danach mit Kostenobergrenze (maxTotalChargeUsd) je Lauf arbeiten.

## Phase 3 — Wettbewerbslandschaft
Für jedes Produkt: alle bekannten Alternativen identifizieren (Websuche + G2/Capterra-
Reviews + Reddit-Erwähnungen). Je Wettbewerber: Schwächen aus echten Quellen dokumentieren
(nie erfunden), Herkunft/Hosting, Preismodell falls öffentlich. Wettbewerbstabelle bauen.
Hinweis: Direkte Marken-Namen-Suche auf LinkedIn/Reddit findet oft nur den Eigen-
Marketing-Feed der Konkurrenz — für organische Platzierungs-Chancen sind neutrale
Schmerzpunkt-Posts (ohne Konkurrenznennung) ergiebiger.

## Phase 4 — Content-Strategie & fertige Assets
Pro Produkt:
- Content-Kalender je Plattform (Frequenz, Ton, Kommentar:Post-Ratio — in Foren/Reddit
  9:1-Regel, sonst wirkt es wie Spam)
- 8+ Post-Ideen mit Hook (Zielsprachen), Kernaussage, CTA, Hashtags, Visual-Idee — jede aus
  einem echten recherchierten Pain-Point abgeleitet, nicht generisch
- Kommentar-Vorlagen für konkrete gefundene Posts (nicht generisch): Mehrwert zuerst,
  Produktname optional dezent einbauen (auf Wunsch), endet mit echter Frage statt Verkaufs-
  CTA. Nie unter Werbe-Posts von Wettbewerbern selbst kommentieren.
- Use-Case-/Zielgruppen-Landingpages je Kernzielgruppe im AEO-Format: H1, Quick-Answer-Box
  (40-60 Wörter), fragenbasierte H2s mit Fließtext, 6 FAQs als FAQPage-JSON-LD, Title/Meta-
  Description, interne Verlinkung. Alle Produktaussagen live auf der Website verifizieren.
- Vergleichsseiten „[Produkt] vs. [Wettbewerber]" im selben Format, bewusst fair (Abschnitt
  „wann ist der Wettbewerber die bessere Wahl"), Wettbewerber-Preis-/Feature-Aussagen vor
  Veröffentlichung mit Stand-Datum kennzeichnen und gegenprüfen lassen

## Phase 5 — Technisches SEO-Setup
Falls Google Search Console verfügbar: alle Domains als Properties verifizieren/prüfen,
Sitemaps einreichen, Indexierungsstatus prüfen (URL Inspection). Technische Fixes
identifizieren: Canonical-Konflikte, kaputte Sitemap-Referenzen in robots.txt, fehlende
Meta-Descriptions, Leftover-Demo-Content von Templates, KI-Crawler-robots.txt (GPTBot/
ClaudeBot/PerplexityBot erlauben). Bot-Sichtbarkeits-Check:
`curl -A "bingbot/2.0" <url> | grep "<h1"` — leeres Ergebnis heißt kaputtes Prerendering.
Ergebnis als EIGENSTÄNDIGE Techniker-Arbeitsanweisung dokumentieren (priorisiert, mit
Verifikations-Befehl je Punkt, Checkliste), getrennt von der Marketing-Strategie.

## Phase 6 — Kostenloses Lead-Magnet-Tool (optional, pro Produkt prüfen)
Für das Produkt mit dem stärksten, konkretesten Schmerzpunkt: prüfen, ob ein kleines
kostenloses Read-only-Check-Tool machbar ist, das das Problem im System des Besuchers
sichtbar macht (z.B. API-Scan mit einer Kennzahl als Ergebnis) und direkt zum Produkt
überleitet. Kein Signup-Gate vor dem Ergebnis, minimal nötige Berechtigungen, nichts
dauerhaft speichern. Konzept inkl. Nutzerfluss, technischem Scope, Landingpage-Text,
Verbreitungsplan dokumentieren.

## Phase 7 — Laufender Wochen-Loop
Falls Scheduling verfügbar: wöchentlichen Rhythmus einrichten. Search-Console-Daten aller
Properties ziehen, auswerten nach Keyword-Gaps (Impressionen ohne eigene Seite),
Kannibalisierung (mehrere eigene Seiten/Subdomains auf derselben Query), neuen
aufkommenden Queries. Wochenvergleich statt Einzelstand. Wenn zuvor identifizierte offene
Punkte (Techniker-Fixes, geplante Seiten) über mehrere Wochen unverändert bleiben: das
explizit benennen statt stillschweigend erneut zu berichten — im Zweifel aktiv
vorschlagen, den Loop zu pausieren/zu eskalieren, statt wirkungslos weiterzulaufen.

## Arbeitsweise (gilt für alle Phasen)
- Keine erfundenen Zitate, Zahlen oder Wettbewerber-Fakten — alles mit Tool-Beleg und
  Quelle/Datum, sonst [low-evidence] kennzeichnen
- Vor kostenpflichtigen oder öffentlich sichtbaren Aktionen (bezahlte API-Läufe, Posten/
  Kommentieren unter echtem Namen, E-Mails an Dritte) kurz Rückmeldung einholen, nicht
  automatisch ausführen
- Alles in versionierten Markdown-Dateien in einem growth-analysis/-Ordner dokumentieren,
  mit Datum im Dateinamen; bei Repo-Anbindung committen und pushen
- Ehrlich über Grenzen/Sackgassen berichten (z.B. wenn eine Recherche nur Rauschen findet)
  statt Erfolg vorzutäuschen
```

---

## Kurz-Checkliste für den Start

1. Abschnitt „Auszufüllen" oben mit Firma/Produkten/Domains befüllen
2. Geprüft, welche der optionalen Anbindungen (Reddit/Apify/GSC) verfügbar sind — Prompt läuft auch mit nur Websuche, liefert dann aber weniger Tiefe
3. Den Block zwischen den ` ``` ` in eine neue Session einfügen
4. Bei Bedarf Reihenfolge/Umfang der Phasen im ersten Prompt selbst einschränken (z. B. „nur Phase 1-4 diese Woche")
