# Techniker-Anweisung: SEO-Fixes SSIG-Websites

**Stand:** 2026-07-05 · **Auftraggeber:** Philipp König · **Kontext:** Alle 5 Domains sind seit heute in der Google Search Console verifiziert, Sitemaps eingereicht. Die folgenden Punkte wurden bei der technischen Prüfung gefunden und sind nach Priorität sortiert. Jeder Punkt enthält einen Verifikations-Befehl, mit dem du deine Änderung selbst prüfen kannst.

---

## Prio 1 — Fehler, die Rankings aktiv schaden

### 1.1 secretexpiry.com: widersprüchliches Canonical (wichtigster Fix)

**Problem:** Die Seite `https://www.secretexpiry.com/` liefert im HTML `<link rel="canonical" href="https://secretexpiry.com"/>` (non-www). Gleichzeitig leitet `https://secretexpiry.com/` per Redirect auf die www-Version weiter. Die Seite behauptet also, ihre eigene Kopie unter einer URL zu sein, die auf sie selbst zurückverweist. Google hat als Canonical die www-Version gewählt („Seite mit Weiterleitung" in der Search Console). Genau dieses Fehlerbild hat in einem dokumentierten Fall 90 % Bing-Traffic gekostet.

**Fix:**
- Canonical auf allen Seiten auf die **www-Version** ändern, jeweils self-referencing (Startseite: `https://www.secretexpiry.com/`, Unterseite X: `https://www.secretexpiry.com/X`).
- Die Sitemap (`/sitemap.xml`) listet aktuell non-www-URLs — auf www-URLs umstellen.
- Redirect non-www → www bleibt wie er ist (der ist korrekt).

**Verifikation:**
```bash
curl -s https://www.secretexpiry.com/ | grep -i canonical
# Erwartet: href="https://www.secretexpiry.com/"
curl -s https://www.secretexpiry.com/sitemap.xml | grep "<loc>" | head -5
# Erwartet: alle URLs beginnen mit https://www.secretexpiry.com/
```

### 1.2 teamsdashboard.com: robots.txt verweist auf nicht existierende Sitemap

**Problem:** Die robots.txt enthält `Sitemap: https://teamsdashboard.com/sitemap.xml` — diese URL liefert **404**. Es existiert nur `/blog/sitemap.xml` (WordPress-Blog). Die Hauptseiten (Startseite, /preise.html, Docs, Demo) sind in keiner Sitemap.

**Fix (bevorzugt):** Eine Haupt-Sitemap unter `/sitemap.xml` anlegen, die enthält:
- `https://teamsdashboard.com/` (bzw. www — bitte konsistent zur Canonical-Entscheidung aus 1.3)
- `https://www.teamsdashboard.com/preise.html`
- `https://docs.teamsdashboard.com/` (falls indexierbar gewünscht)
- `https://demo.teamsdashboard.com/` (falls indexierbar gewünscht)
- Verweis auf `/blog/sitemap.xml` als zweiten Sitemap-Eintrag in der robots.txt ergänzen — oder eine Sitemap-Index-Datei bauen, die beide referenziert.

**Fix (minimal, falls keine Zeit):** robots.txt-Zeile ändern auf `Sitemap: https://teamsdashboard.com/blog/sitemap.xml`.

**Nach dem Fix bitte Bescheid geben** — die neue Sitemap wird dann zentral in der Search Console nachgereicht.

**Verifikation:**
```bash
curl -sI https://teamsdashboard.com/sitemap.xml | head -1   # Erwartet: HTTP 200
```

### 1.3 Canonical-Tags fehlen komplett: galynski.com und teamsdashboard.com

**Problem:** Beide Seiten haben gar kein `<link rel="canonical">`. Ohne Canonical kann jede URL-Variante (mit/ohne www, mit Tracking-Parametern wie `?utm_source=...`) als eigenständige Seite gewertet werden und Rankings aufsplitten.

**Fix:** Auf jeder Seite ein self-referencing Canonical ergänzen:
- galynski.com: `<link rel="canonical" href="https://galynski.com/" />` (bzw. je Unterseite die eigene URL; non-www ist hier die etablierte Variante)
- teamsdashboard.com: erst entscheiden, ob www oder non-www die führende Variante ist (aktuell antworten beide — die Nicht-Kanonische sollte per 301 auf die Kanonische umleiten), dann Canonical entsprechend setzen.

**Verifikation:**
```bash
curl -s https://galynski.com/ | grep -i canonical
curl -s https://www.teamsdashboard.com/ | grep -i canonical
```

---

## Prio 2 — Sichtbarkeit & Vertrauen

### 2.1 ssig-it.com (Webflow): Title + Meta-Description setzen

**Problem:** Die Startseite hat keine Meta-Description, und der Title („SSIG-IT | Ihre IT-Spezialisten") enthält kein einziges Suchwort.

**Fix im Webflow Designer:** Pages → Home → Zahnrad (Page Settings) → SEO Settings:
- **Title:** `SSIG-IT | IT-Dienstleister & Managed Services in Ulm/Blaubeuren`
- **Meta Description:** `IT-Dienstleister aus Blaubeuren bei Ulm: Managed Services, IT-Consulting, Workplace as a Service und eigene Microsoft-365-Software von SSIG-IT.`

Danach Site publishen.

**Verifikation:**
```bash
curl -s https://www.ssig-it.com/ | grep -iE '<title>|name="description"'
```

### 2.2 ssig-work.com (WordPress): Template-Demotext im Footer entfernen

**Problem:** Im Footer/Quelltext steht noch der Demo-Text des gekauften Themes: „For every modern coworking or office space website out there. This is MultiOffice. Contact us 3975 Freedom Cir Mission…" — wirkt unseriös und verwässert den lokalen SEO-Fokus.

**Fix:** Im WordPress-Customizer bzw. Theme-Footer-Widget den MultiOffice-Demoblock löschen/durch echte ssig:work-Daten ersetzen.

**Verifikation:**
```bash
curl -s https://www.ssig-work.com/ | grep -i "MultiOffice"   # Erwartet: keine Ausgabe
```

### 2.3 Bing Webmaster Tools für alle 5 Domains einrichten

**Warum:** Bing speist auch ChatGPT-Suche und Copilot. Dokumentierter Fall: monatelanger 90-%-Trafficverlust bei Bing blieb unbemerkt, weil kein Bing-Webmaster-Zugang existierte.

**Fix (ca. 10 Minuten):** https://www.bing.com/webmasters → „Import from Google Search Console" → mit dem Google-Konto anmelden, das die GSC-Properties hält → alle 5 Properties importieren (ssig-it.com, ssig-work.com, teamsdashboard.com, secretexpiry.com, galynski.com). Sitemaps werden mit importiert.

---

## Prio 3 — Ausbau (kein Fehler, aber gezielter Hebel)

### 3.1 KI-Crawler-robots.txt von teamsdashboard.com übernehmen

teamsdashboard.com erlaubt explizit GPTBot, ClaudeBot, PerplexityBot, OAI-SearchBot etc. — dieselben Blöcke in die robots.txt von **galynski.com** und **secretexpiry.com** übernehmen (dort erlaubt aktuell nur die Wildcard-Regel; die explizite Freigabe ist sauberer und zukunftssicher, falls je eine restriktivere Regel ergänzt wird).

### 3.2 Artikel-/Seiten-Template für neue Inhalte (AEO-Format)

Für alle künftigen Blogartikel und Ratgeberseiten (alle drei Produkte) folgendes Template implementieren — es rankt bei Google **und** wird von KI-Suchmaschinen (ChatGPT, Perplexity, Claude) als Quelle zitiert:

1. Einleitungsabsatz mit echter Information (kein Fluff)
2. **„Kurz beantwortet"-Box** direkt unter der H1: 40–60 Wörter, beantwortet die Kernfrage direkt (als `<blockquote>` oder hervorgehobene Box)
3. H2-Überschriften **als Fragen** formuliert („Wie synchronisiere ich die GAL auf iPhone-Kontakte?")
4. Interne Links auf die relevanten Produkt-/Preisseiten
5. Am Ende: **mindestens 6 FAQ-Fragen mit FAQPage-Structured-Data** (JSON-LD):

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [{
    "@type": "Question",
    "name": "Frage hier?",
    "acceptedAnswer": { "@type": "Answer", "text": "Antwort hier." }
  }]
}
</script>
```

### 3.3 galynski.com: englische Version (/en) — Backlog

Landingpage-Struktur ist vorhanden; EN-Variante mit `hreflang`-Tags (de/en) einplanen. Kein Blocker, aber Voraussetzung für den internationalen Markt.

---

### 1.4 teamsdashboard.com: Subdomain-Kannibalisierung (ergänzt 2026-07-08 nach GSC-Analyse)

**Problem:** Die Search Console zeigt, dass `app.teamsdashboard.com`, `demo.teamsdashboard.com` und `docs.teamsdashboard.com` für dieselben Queries wie die Startseite ranken („teams dashboard", „team dashboard", „dashboard teams") — auf Positionen 26–83. Sie verwässern damit das Ranking der Hauptseite.

**Fix:**
- `app.teamsdashboard.com` (Login) und `demo.teamsdashboard.com`: `<meta name="robots" content="noindex">` setzen — Login-/Demo-Oberflächen sollen nicht in der Suche erscheinen.
- `docs.teamsdashboard.com`: darf indexiert bleiben, aber Startseiten-Title dort auf Doku-Begriffe ausrichten („TeamsDashboard Dokumentation") statt generisch.

**Verifikation:**
```bash
curl -s https://app.teamsdashboard.com/ | grep -i 'noindex'
curl -s https://demo.teamsdashboard.com/ | grep -i 'noindex'
```

---

## Checkliste zum Abhaken

- [ ] 1.1 secretexpiry.com Canonical auf www + Sitemap-URLs auf www
- [ ] 1.2 teamsdashboard.com Haupt-Sitemap anlegen + robots.txt korrigieren → danach Rückmeldung für GSC-Einreichung
- [ ] 1.3 Canonical-Tags galynski.com + teamsdashboard.com
- [ ] 2.1 ssig-it.com Title + Meta-Description (Webflow)
- [ ] 2.2 ssig-work.com MultiOffice-Demotext entfernen
- [ ] 2.3 Bing Webmaster Tools, alle 5 Domains via GSC-Import
- [ ] 3.1 KI-Crawler-robots.txt auf galynski.com + secretexpiry.com
- [ ] 3.2 AEO-Artikel-Template (Quick-Answer + Frage-H2s + FAQ-JSON-LD)
- [ ] 3.3 galynski.com /en mit hreflang (Backlog)
