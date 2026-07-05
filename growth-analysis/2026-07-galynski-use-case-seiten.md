# GALYNSKI — Use-Case-Seiten: Struktur & fertige Texte

**Stand:** 2026-07-05 · **Zweck:** Jede Zielgruppe bekommt eine eigene, indexierbare Landing-URL mit eigenem Title, Quick-Answer-Box (AEO) und FAQ-Schema — nach dem Agensi-Playbook (Learning 1 im Social-Listening-Report). Alle Produktaussagen unten sind gegen galynski.com (Stand heute) geprüft; nichts ist erfunden.

**Empfohlene URL-Struktur:**

```
galynski.com/loesungen                     ← Hub-Seite (kurz, verlinkt auf alle)
galynski.com/loesungen/aussendienst        ← Seite 1: Vertrieb & Außendienst
galynski.com/loesungen/byod                ← Seite 2: BYOD / ohne MDM
galynski.com/loesungen/it-dienstleister    ← Seite 3: Systemhäuser & IT-Dienstleister
galynski.com/branchen/handwerk-bau         ← Seite 4: Handwerk & Bau
```

**Interne Verlinkung (Pflicht, macht die Seiten zum Netz statt zu Insel-Seiten):**
- Startseite → Footer- oder Nav-Block „Lösungen" mit Links auf alle 4 Seiten
- Jede Use-Case-Seite → Preise-Sektion, „Jetzt starten" und mindestens 2 andere Use-Case-Seiten
- Künftige Blogartikel → auf die thematisch passende Use-Case-Seite verlinken (nicht immer nur auf die Startseite)

**Format je Seite (AEO-Template):** H1 → „Kurz beantwortet"-Box (40–60 Wörter) → Frage-H2s → CTA → 6 FAQs als FAQPage-JSON-LD (Snippet in der Techniker-Anweisung, Punkt 3.2).

---

## Seite 1 — Vertrieb & Außendienst

**URL:** `/loesungen/aussendienst`
**Title (58 Z.):** `Firmenkontakte für den Außendienst aufs Handy | GALYNSKI`
**Meta-Description (152 Z.):** `Ihr Vertrieb sieht sofort, welcher Kunde oder Kollege anruft: GALYNSKI synchronisiert das Microsoft-365-Adressbuch automatisch aufs Smartphone.`

### H1
Ihr Außendienst erreicht jeden — und weiß sofort, wer anruft.

### Kurz beantwortet (Box)
> GALYNSKI synchronisiert das komplette Microsoft-365-Firmenadressbuch automatisch in die nativen Kontakte der Vertriebs-Smartphones. Anrufe von Kollegen, Kunden und Lieferanten erscheinen mit Name, Position und Firma — ohne App, ohne MDM, ohne manuelles Kontakte-Pflegen. Einrichtung in unter 2 Minuten, ab 4 € pro Benutzer und Monat.

### H2: Warum sieht mein Vertriebsteam Anrufer nur als unbekannte Nummer?
Die Globale Adressliste (GAL) von Microsoft 365 ist in Outlook sichtbar — aber sie synchronisiert nicht in die nativen Kontakte des Smartphones. Genau dort schaut das Telefon aber nach, wenn ein Anruf eingeht. Das Ergebnis kennt jeder im Außendienst: Der Kollege aus dem Innendienst ruft an, das Display zeigt „+49 170 …", und der Rückruf an den wichtigen Kunden wird verwechselt oder verpasst. Wer viel unterwegs ist, kann es sich nicht leisten, bei jeder unbekannten Nummer zu raten.

### H2: Wie kommen die Firmenkontakte automatisch auf die Handys?
GALYNSKI verbindet sich einmalig per Admin-Consent mit Ihrem Microsoft-365-Tenant und synchronisiert das Firmenadressbuch täglich in einen Kontaktordner jedes Mitarbeitenden — über die vorhandene Exchange-/Outlook-Synchronisation, die auf jedem Business-Smartphone ohnehin läuft. Ihre Vertriebler müssen nichts installieren, nichts freigeben, nichts pflegen. Neue Kolleginnen und geänderte Durchwahlen sind am nächsten Morgen automatisch auf allen Geräten.

### H2: Muss der Vertrieb dafür eine App installieren?
Nein. GALYNSKI arbeitet cloudbasiert über Microsoft 365 und Exchange — es gibt keine Mitarbeiter-App und kein Geräteprofil. Das ist besonders für Außendienst-Teams mit gemischten Geräten (privat und Firmenhandy, iOS und Android) entscheidend: Es funktioniert überall dort, wo das Firmenpostfach eingerichtet ist.

### H2: Bekommt jeder im Unternehmen alle Kontakte?
Nur wenn Sie das wollen. Mit Verteilungsregeln steuern Sie, welches Team welche Kontakte erhält — zum Beispiel: Der Vertrieb bekommt zusätzlich die Customer-Service-Liste, aber nicht umgekehrt. Räume, Ressourcen und Systemkonten filtert GALYNSKI automatisch heraus, damit kein Adressbuch-Müll auf den Handys landet.

### CTA
**Jetzt kostenlos registrieren** — keine Kreditkarte nötig, Setup in unter 2 Minuten. [Preise ansehen]

### FAQ (als FAQPage-JSON-LD)
1. **Funktioniert GALYNSKI auf privaten Handys im Vertrieb?** Ja. GALYNSKI benötigt weder MDM noch eine App — die Kontakte kommen über die normale Exchange-/Outlook-Kontaktsynchronisation auf jedes Gerät, auf dem das Firmenpostfach eingerichtet ist.
2. **Wie schnell sind neue Mitarbeitende auf allen Geräten sichtbar?** GALYNSKI synchronisiert täglich, geplante Syncs laufen nachts zwischen 02:00 und 05:00 Uhr Ortszeit. Änderungen von heute sind morgen früh auf allen Smartphones.
3. **Zeigt das Handy bei Anrufen auch Position und Firma an?** Ja — die Anruferkennung zeigt Name, Position und Firma, sofern diese Felder in Microsoft 365 gepflegt sind.
4. **Was kostet GALYNSKI für ein Vertriebsteam?** 4 € pro Benutzer und Monat (zzgl. MwSt.), bei jährlicher Zahlung 25 % günstiger, ab 51 Benutzern gestaffelt. Jederzeit kündbar.
5. **Entstehen Dubletten mit bestehenden persönlichen Kontakten?** Nein — GALYNSKI bereinigt Dubletten per E-Mail-Abgleich und schreibt in einen eigenen Kontaktordner.
6. **Ist das DSGVO-konform?** Ja. GALYNSKI wird in der EU gehostet und ist DSGVO-konform; ein vollständiges Audit-Log dokumentiert alle Syncs und Änderungen.

---

## Seite 2 — BYOD / ohne MDM

**URL:** `/loesungen/byod`
**Title (56 Z.):** `GAL-Sync ohne MDM: Firmenkontakte auf BYOD | GALYNSKI`
**Meta-Description (150 Z.):** `Firmenadressbuch auf private Smartphones — ohne Intune, ohne MDM, ohne App. GALYNSKI synchronisiert die Microsoft-365-GAL DSGVO-konform per Cloud.`

### H1
Das Firmenadressbuch auf jedem Gerät — ganz ohne MDM.

### Kurz beantwortet (Box)
> GALYNSKI bringt die Microsoft-365-GAL auf private und unverwaltete Smartphones, ohne dass die Geräte in Intune oder ein anderes MDM eingebunden werden müssen. Die Kontakte laufen über die vorhandene Exchange-Synchronisation ins native Adressbuch — keine App, kein Geräteprofil, kein Eingriff ins Privatgerät. DSGVO-konform, EU-gehostet.

### H2: Warum ist GAL-Sync auf BYOD-Geräten so schwierig?
Microsoft 365 bietet keine native Funktion, um die Globale Adressliste in die Handy-Kontakte zu synchronisieren. Die üblichen Workarounds setzen entweder Geräteverwaltung (Intune/MDM) voraus — was viele Mitarbeitende auf Privatgeräten zu Recht ablehnen — oder verlangen manuelles Kopieren, das nach zwei Wochen veraltet ist. IT-Teams kennen die Folge: ständige Tickets („Warum finde ich Kollegen nicht auf dem Handy?") und Betriebsrats-Diskussionen über MDM auf Privatgeräten.

### H2: Wie funktioniert GALYNSKI ohne Zugriff auf die Geräte?
GALYNSKI berührt die Smartphones überhaupt nicht. Der Sync passiert serverseitig in Microsoft 365: Die GAL-Kontakte werden in einen Kontaktordner des jeweiligen Benutzerpostfachs geschrieben — und von dort nimmt die ganz normale Exchange-/Outlook-Synchronisation sie mit aufs Gerät, wie jeden anderen Kontakt auch. Kein Profil, keine Richtlinie, keine App. Das Privatgerät bleibt privat.

### H2: Was sagt der Datenschutz dazu?
GALYNSKI wird in der EU gehostet und arbeitet DSGVO-konform. Es werden nur die Geschäftskontaktfelder synchronisiert, und ein Audit-Log mit 365 Tagen Aufbewahrung dokumentiert jede Änderung — das erleichtert die Abstimmung mit Datenschutzbeauftragten und Betriebsrat erheblich. Da kein MDM auf Privatgeräten nötig ist, entfällt der heikelste Diskussionspunkt komplett.

### H2: Behält die IT trotzdem die Kontrolle?
Ja — zentral statt am Gerät. Im Dashboard sehen Sie Sync-Status, aktive Regeln und Lizenz-Auslastung; Delete-Caps und Drop-Erkennung verhindern, dass fehlerhafte Massenänderungen Kontakte im großen Stil löschen. Bis zu 5 Admins verwalten das gemeinsam, ohne zusätzliche Dashboard-Lizenzen.

### CTA
**In 4 Schritten startklar** — kostenlos registrieren, Microsoft 365 verbinden, Regeln festlegen, fertig. [Jetzt starten]

### FAQ (als FAQPage-JSON-LD)
1. **Brauchen Mitarbeitende eine App auf dem Privatgerät?** Nein. Es gibt keine Mitarbeiter-App — die Kontakte kommen über die vorhandene Exchange-/Outlook-Synchronisation aufs Gerät.
2. **Muss das Privatgerät in Intune oder ein MDM eingebunden werden?** Nein. GALYNSKI arbeitet vollständig serverseitig über Microsoft 365 und Exchange; die Geräte bleiben unverwaltet.
3. **Kann die IT steuern, wer welche Kontakte bekommt?** Ja, über Verteilungsregeln: aus der gesamten GAL oder gezielt aus Microsoft-365-Gruppen, bis zu 3 Regeln mit je 3 Zielgruppen.
4. **Was passiert, wenn jemand das Unternehmen verlässt?** Der Sync läuft über das Benutzerpostfach — wird das Konto deaktiviert, endet auch die Kontaktsynchronisation auf dem Gerät.
5. **Landen Räume, Verteiler und Systemkonten auch auf dem Handy?** Nein, die filtert GALYNSKI automatisch heraus, bevor synchronisiert wird.
6. **Wo werden die Daten verarbeitet?** In der EU. GALYNSKI ist DSGVO-konform und führt ein Audit-Log mit 365 Tagen Aufbewahrung.

---

## Seite 3 — Systemhäuser & IT-Dienstleister

**URL:** `/loesungen/it-dienstleister`
**Title (59 Z.):** `GAL-Sync für Ihre Kunden einrichten | GALYNSKI für Systemhäuser`
**Meta-Description (154 Z.):** `Als IT-Dienstleister GAL-Sync bei Kunden ausrollen: Setup in Minuten, Admin-Zugänge fürs Systemhaus, Audit-Log, planbare Preise. Ohne MDM-Projekt.`

### H1
Die Kundenanfrage „Kontakte aufs Handy" — in Minuten gelöst statt in Projekttagen.

### Kurz beantwortet (Box)
> Systemhäuser richten GALYNSKI je Kunden-Tenant in unter 2 Minuten ein: Admin-Consent erteilen, Verteilungsregeln festlegen, fertig. Bis zu 5 Admin-Zugänge pro Instanz — Ihr Team verwaltet den Sync für den Kunden mit, inklusive Audit-Log und Schutz vor Massenänderungen. Planbar ab 4 € pro Benutzer und Monat, ohne MDM-Rollout.

### H2: Warum ist „GAL aufs Handy" für IT-Dienstleister ein Dauerthema?
Fast jeder Microsoft-365-Kunde stellt irgendwann dieselbe Frage: „Warum sehe ich Kollegen nicht in den Handy-Kontakten?" Die ehrliche Antwort — Microsoft bietet das nativ nicht — verkauft sich schlecht. Die Alternativen sind ein MDM-Projekt (teuer, auf BYOD unbeliebt), PowerShell-Eigenbau (wartungsintensiv, hängt an einer Person) oder internationale Tools mit Preismodellen, die bei wachsender Nutzerzahl schnell teuer werden.

### H2: Wie rollt ein Systemhaus GALYNSKI beim Kunden aus?
Pro Kunde: Account anlegen, Admin-Consent im Kunden-Tenant mit einem Klick erteilen, Zielgruppen und Kontaktordner festlegen — der Sync läuft ab dann täglich und automatisch, geplante Läufe nachts zwischen 02:00 und 05:00 Uhr. Chunking, Graph-Batching und Throttling-Handling sind eingebaut, damit auch Rollouts mit tausenden Benutzern kontrolliert durchlaufen. Es gibt kein Gerätetouching, keine App-Verteilung, kein Schulungsaufwand beim Endkunden.

### H2: Behält mein Team den Zugriff, ohne Lizenzen zu verbrennen?
Ja: Bis zu 5 Admins pro Instanz sind inklusive, eingeladen per Link oder 6-stelligem Code — ohne zusätzliche Dashboard-Lizenz. So verwalten Ihre Techniker Regeln, Syncs und Status direkt mit. Das Audit-Log (365 Tage Retention) dokumentiert jede Änderung — praktisch für Support-Fälle und Compliance-Nachweise gegenüber dem Kunden.

### H2: Was schützt den Kunden vor Sync-Unfällen?
Delete-Caps, Drop-Erkennung, Truncation-Abbruch und Aggregate-Guards stoppen riskante Syncs, bevor falsche Kontakte im großen Stil entfernt werden. Dublettenbereinigung per E-Mail-Abgleich ist inklusive; Räume, Ressourcen und No-Reply-Adressen werden automatisch gefiltert.

### CTA
**Richten Sie Ihren ersten Kunden heute ein** — kostenlos registrieren, keine Kreditkarte. Fragen zur Einführung bei mehreren Kunden? [Kontakt aufnehmen]

### FAQ (als FAQPage-JSON-LD)
1. **Kann ich als externer IT-Dienstleister Admin der Kunden-Instanz sein?** Ja — bis zu 5 Admins pro Instanz sind inklusive, Einladung per Link oder Code, ohne zusätzliche Lizenzkosten.
2. **Wie lange dauert das Setup je Kunde?** Unter 2 Minuten bis zum ersten konfigurierten Sync: registrieren, Admin-Consent erteilen, Regeln festlegen.
3. **Skaliert das auch bei großen Kunden-Tenants?** Ja — Chunking, Graph-Batching und Throttling-Handling sind für Rollouts vom kleinen Team bis zu tausenden Benutzern ausgelegt.
4. **Wie weise ich dem Kunden nach, was synchronisiert wurde?** Über das Audit-Log mit 365 Tagen Aufbewahrung: Logins, Syncs, Regeländerungen und Admin-Aktionen sind nachvollziehbar.
5. **Was kostet das für meinen Kunden?** 4 € pro Benutzer und Monat (zzgl. MwSt.), jährlich 25 % günstiger, Staffelpreise ab 51 Benutzern, jederzeit kündbar.
6. **Braucht der Endkunde MDM oder eine App?** Nein — der Sync läuft serverseitig über Microsoft 365/Exchange in die nativen Kontakte, ganz ohne Geräteverwaltung.

**Hinweis für die Umsetzung:** Keine zentrale Multi-Tenant-Konsole versprechen — die gibt es aktuell nicht. Die Seite ist bewusst auf „pro Kunde in Minuten einrichten + 5 Admin-Zugänge" getextet. Falls eine Partner-/Mandantenverwaltung auf der Roadmap steht, ist diese Seite der Ort, sie später anzukündigen.

---

## Seite 4 — Handwerk & Bau

**URL:** `/branchen/handwerk-bau`
**Title (57 Z.):** `Kundenkontakte aufs Monteur-Handy | GALYNSKI für Handwerk`
**Meta-Description (151 Z.):** `Monteure und Bauleiter erreichen Büro, Kollegen und Lieferanten ohne Nummern-Suchen: GALYNSKI synchronisiert Microsoft-365-Kontakte aufs Smartphone.`

### H1
Ihre Monteure telefonieren viel. Ihre Handys wissen nur nicht, mit wem.

### Kurz beantwortet (Box)
> GALYNSKI synchronisiert Büro-, Kollegen- und Lieferantenkontakte aus Microsoft 365 automatisch auf die Smartphones von Monteuren und Bauleitern. Anrufe von der Baustelle zeigen sofort Name und Firma — ohne dass jemand Kontakte abtippt oder eine App installiert. Läuft auf jedem Gerät mit Firmenpostfach, ab 4 € pro Benutzer und Monat.

### H2: Warum stehen im Monteur-Handy nie die richtigen Nummern?
Auf der Baustelle wird über das Handy koordiniert — Büro, Polier, Subunternehmer, Lieferant. Aber die Kontakte pflegt niemand: Der neue Kollege steht nicht im Adressbuch, die alte Nummer vom Großhändler schon. Wer im Büro Outlook nutzt, hat die aktuellen Daten — auf dem Handy des Monteurs kommen sie nie an, weil Microsoft 365 die Globale Adressliste nicht in die Handy-Kontakte synchronisiert.

### H2: Wie hält GALYNSKI die Kontakte auf allen Geräten aktuell?
Einmal eingerichtet, synchronisiert GALYNSKI täglich automatisch: Was die Büro-IT in Microsoft 365 pflegt, steht am nächsten Morgen in den nativen Kontakten aller Mitarbeiter-Smartphones. Niemand auf der Baustelle muss etwas tun — keine App, kein Update, kein Abtippen. Ruft das Büro oder ein Kollege an, zeigt das Display Name, Position und Firma.

### H2: Funktioniert das auch mit einfachen oder privaten Handys?
Ja. Voraussetzung ist nur, dass das Firmenpostfach (Exchange/Outlook) auf dem Gerät eingerichtet ist — dann kommen die Kontakte über die normale Synchronisation an, auf iOS und Android, auf Firmen- wie Privatgeräten. Ein MDM oder Geräteprofil ist nicht nötig; das ist gerade in Betrieben ohne eigene IT-Abteilung der entscheidende Unterschied.

### H2: Wer richtet das ein, wenn wir keine eigene IT haben?
Entweder Ihr IT-Dienstleister (Setup dauert unter 2 Minuten, [Infos für Systemhäuser]) — oder Sie selbst: kostenlos registrieren, Microsoft 365 mit einem Klick verbinden, festlegen, wer welche Kontakte bekommt. Ab dann läuft es im Hintergrund.

### CTA
**Kostenlos testen** — keine Kreditkarte, jederzeit kündbar. [Jetzt starten] · [Preise]

### FAQ (als FAQPage-JSON-LD)
1. **Müssen die Monteure etwas installieren oder einstellen?** Nein — die Kontakte erscheinen automatisch in der normalen Kontakte-App, sobald das Firmenpostfach auf dem Gerät eingerichtet ist.
2. **Können wir nur bestimmte Kontakte verteilen, z. B. ohne die Geschäftsführung?** Ja, über Verteilungsregeln: pro Regel legen Sie Quelle (GAL oder Microsoft-365-Gruppe) und Zielgruppe fest.
3. **Was ist mit Lieferanten und externen Kontakten?** Alles, was als Kontakt in Ihrem Microsoft-365-Adressbuch gepflegt ist, kann synchronisiert werden — inklusive externer Geschäftskontakte.
4. **Funktioniert das mit unseren gemischten Geräten (iOS/Android, alt/neu)?** Ja, GALYNSKI ist geräteunabhängig — es nutzt die Exchange-Synchronisation, die auf allen gängigen Smartphones vorhanden ist.
5. **Was kostet das für einen 20-Personen-Betrieb?** 80 € pro Monat (20 × 4 €, zzgl. MwSt.), bei jährlicher Zahlung 25 % weniger. Jederzeit kündbar.
6. **Sind unsere Daten sicher?** GALYNSKI wird in der EU gehostet, ist DSGVO-konform und schützt mit Delete-Caps und Audit-Log vor fehlerhaften Massenänderungen.

---

## Hub-Seite `/loesungen` (kurz)

**Title:** `GALYNSKI Lösungen: GAL-Sync für jedes Team | GALYNSKI`
**Meta-Description:** `Firmenkontakte automatisch aufs Smartphone — für Außendienst, BYOD, Systemhäuser und Handwerk. Finden Sie das passende GALYNSKI-Szenario.`

Inhalt: H1 „Für wen ist GALYNSKI?" + 4 Karten (je Zielgruppe: 2 Sätze + Link auf die Detailseite). Keine lange Seite — sie existiert primär als Verteiler und Nav-Ziel.

---

## Nächste Ausbaustufen (nach Live-Gang dieser 4 Seiten)

1. **Vergleichsseiten** (höchste Kaufabsicht): `/vergleich/cirasync-alternative` — „CiraSync-Alternative aus Deutschland" mit neutraler Feature-/Preis-Tabelle. Danach analog für weitere Wettbewerber (Cloudiway, Sigsync — siehe Wettbewerbsliste im Social-Listening-Report).
2. **Ratgeber-Artikel** im AEO-Format, die auf die Use-Case-Seiten verlinken: „GAL auf iPhone synchronisieren — 3 Wege im Vergleich", „Unbekannter Anrufer bei Kollegen-Anrufen: Ursache & Lösung", „Outlook-Kontakte auf Android: Warum die GAL fehlt".
3. **EN-Versionen** der Use-Case-Seiten unter `/en/solutions/...` mit hreflang (siehe Techniker-Anweisung 3.3).
4. **Erfolgsmessung:** Ab Live-Gang wandern die Seiten in den wöchentlichen Search-Console-Gap-Loop — Queries, auf denen sie Impressionen sammeln, steuern die nächsten Ratgeber-Artikel.
