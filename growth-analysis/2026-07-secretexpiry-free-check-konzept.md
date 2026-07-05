# Konzept: „Secret-Ablauf-Check" — kostenloses Lead-Magnet-Tool für SecretExpiry

**Stand:** 2026-07-05 · **Herleitung:** Learning 4.1 (Free-Tool-Muster aus r/micro_saas) × stärkster Pain-Point-Cluster B1 („Stille Secret-Abläufe verursachen Produktionsausfälle", Buying-Intent 9/10)

---

## 1. Funnel-Logik in einem Satz

Der Check zeigt einem Admin in 2 Minuten **seinen eigenen Schmerz in Zahlen** („Sie haben 214 App-Registrations, 31 Secrets sind bereits abgelaufen, 12 laufen in 30 Tagen ab") — und SecretExpiry ist die Antwort auf die unvermeidliche Folgefrage „und wer sagt mir das nächstes Mal *vorher*?".

Warum das funktioniert: Der beste Post-Hook aus dem Report (B1: „Wir haben 900 App-Registrations. Rate mal, wie viele Secrets abgelaufen sind.") wird vom rhetorischen Trick zum **interaktiven Erlebnis mit den echten Zahlen des Besuchers**. Statt Behauptung → Beweis im eigenen Tenant.

## 2. User-Flow (3 Schritte, kein Signup vor dem Ergebnis)

1. **Landingpage** `secretexpiry.com/check` (oder `check.secretexpiry.com`): ein Button „Tenant jetzt prüfen — kostenlos, read-only".
2. **Microsoft-Login + Admin-Consent** (OAuth): Admin meldet sich mit seinem M365-Konto an und erteilt einmalig die Read-only-Berechtigung. Kein Formular, keine E-Mail-Pflicht vor dem Ergebnis — die Hürde so niedrig wie möglich.
3. **Ergebnis-Seite** (sofort): Kennzahlen + Tabelle der kritischsten Fälle + ein einziger CTA („Dauerhaft überwachen mit SecretExpiry — Setup in 2 Minuten").

Optional Schritt 4: „Ergebnis als PDF an mich senden" → E-Mail-Feld → das ist der Lead (Double-Opt-in, DSGVO-sauber). Wichtig: optional, nicht als Gate vor dem Ergebnis.

## 3. Technischer Scope (MVP)

**Graph-API-Aufrufe (alle read-only):**
- `GET /applications?$select=displayName,appId,passwordCredentials,keyCredentials,createdDateTime` (paginiert) — App-Registrations mit Secret-/Zertifikats-Metadaten
- Optional Phase 2: `GET /servicePrincipals` für SAML-Signing-Certs

**Benötigte Berechtigung:** `Application.Read.All` (delegated, Admin-Consent) — mehr nicht. Explizit **kein** `Directory.Read.All`, kein Schreibrecht.

**Ausgewertete Felder je Credential:** `endDateTime` (Ablauf), `startDateTime`, `displayName` (Hint), `keyId`. **Wichtiger Vertrauenspunkt, prominent kommunizieren:** Die Graph-API gibt Secret-*Werte* prinzipbedingt nie heraus — der Check kann Geheimnisse technisch gar nicht lesen, nur deren Ablaufdaten. Das ist kein Versprechen, sondern API-Design von Microsoft.

**Berechnete Kennzahlen:**
- App-Registrations gesamt / mit mind. 1 Credential
- Bereits abgelaufene Secrets/Zertifikate (Anzahl + älteste Leiche)
- Ablauf in ≤ 7 / ≤ 30 / ≤ 90 Tagen
- Apps ohne Owner (falls Phase 2 `owners` mitliest — der Ownership-Pain-Point aus Cluster B3)
- „Risiko-Score" (einfach: gewichtete Summe, für den Screenshot-/Teilen-Effekt)

**Datenhaltung:** Ergebnis nur im Session-Speicher rendern, **nichts persistieren** (außer anonymem Zähler „X Checks durchgeführt" fürs Marketing und optional der PDF-Mail-Lead). Verarbeitung in der EU. Genau das auf der Seite sagen — es ist das Gegenargument zum CiraSync-Kritikpunkt „volle Admin-Rechte an US-Anbieter".

**Aufwand-Schätzung MVP:** OAuth-Flow + eine paginierte Graph-Abfrage + eine Ergebnis-Seite. Kein Datenbank-Design, kein Scheduler, kein Multi-Tenant-State — bewusst wegwerfbar schlank. Realistisch wenige Entwicklertage, zumal SecretExpiry den Graph-Zugriff im Kern schon hat.

## 4. Landingpage-Text (AEO-Format, publikationsfertig)

**URL:** `secretexpiry.com/check`
**Title (59 Z.):** `Kostenloser Check: Abgelaufene Secrets in Entra ID finden`
**Meta-Description (154 Z.):** `Wie viele App-Secrets in Ihrem Microsoft-365-Tenant sind abgelaufen? Der kostenlose Read-only-Check zeigt es in 2 Minuten — ohne Installation, EU-gehostet.`

### H1
Wie viele Ihrer App-Secrets sind bereits abgelaufen? Finden Sie es in 2 Minuten heraus.

### Kurz beantwortet (Box)
> Der kostenlose Secret-Ablauf-Check prüft Ihren Microsoft-365-Tenant read-only auf abgelaufene und bald ablaufende App-Secrets und Zertifikate. Ergebnis in unter 2 Minuten: Anzahl, kritischste Fälle, Ablauf-Zeitachse. Keine Installation, keine Kreditkarte, keine Datenspeicherung — Secret-Werte kann der Check technisch gar nicht lesen, nur Ablaufdaten.

### H2: Warum sollte ich meine App-Registrations jetzt prüfen?
Microsoft benachrichtigt genau einmal, 30 Tage vor Ablauf, per E-Mail — die im Alltag leicht untergeht. Die Folge beschreiben Admins immer wieder gleich: Freitagnachmittag, „wir kommen nicht mehr ins System", und die Ursache ist ein still abgelaufenes Client Secret, das VPN, SSO oder eine Integration lahmlegt. Je mehr App-Registrations ein Tenant hat, desto sicherer ist statistisch, dass gerade etwas abgelaufen ist, von dem niemand weiß.

### H2: Was genau prüft der Check — und was nicht?
Der Check liest über die Microsoft-Graph-API die **Metadaten** Ihrer App-Registrations: Namen, Anlagedatum und die Ablaufdaten der hinterlegten Secrets und Zertifikate. Nicht mehr. Die Werte der Secrets selbst gibt Microsofts API prinzipbedingt an niemanden heraus — auch nicht an uns. Es wird nichts geschrieben, nichts geändert, nichts gespeichert: Das Ergebnis existiert nur in Ihrer Browser-Sitzung.

### H2: Welche Berechtigung muss ich erteilen?
Eine einzige: `Application.Read.All` (lesend), per Standard-Microsoft-Consent-Dialog. Sie sehen vor der Zustimmung exakt, was angefragt wird, und können die Freigabe im Entra-Portal jederzeit widerrufen. Verarbeitung in der EU, DSGVO-konform.

### H2: Was mache ich mit dem Ergebnis?
Abgelaufene Leichen aufräumen, bald ablaufende rechtzeitig rotieren — dafür reicht der Check. Was er nicht kann: beim nächsten Ablauf *vorher* Bescheid sagen. Genau dafür ist SecretExpiry gebaut: mehrstufige Erinnerungen statt einer einzigen Microsoft-Mail, Ownership-Zuordnung („wem gehört diese App?") und Multi-Tenant-Übersicht für IT-Dienstleister.

### CTA (auf der Ergebnis-Seite)
**{{n_expiring}} Secrets laufen in den nächsten 30 Tagen ab.** Lassen Sie sich beim nächsten Mal vorher warnen → [SecretExpiry kostenlos testen]

### FAQ (FAQPage-JSON-LD)
1. **Ist der Check wirklich kostenlos?** Ja, vollständig — keine Kreditkarte, kein Abo, keine E-Mail-Pflicht für das Ergebnis.
2. **Kann der Check meine Secrets lesen?** Nein, technisch unmöglich: Die Graph-API liefert nur Metadaten (Ablaufdaten, Namen), niemals die Secret-Werte selbst.
3. **Werden meine Daten gespeichert?** Nein. Das Ergebnis wird nur in Ihrer Sitzung angezeigt; nach dem Schließen ist es weg. Optional können Sie es sich als PDF zusenden lassen.
4. **Welche Rolle brauche ich für den Check?** Ein Konto, das den Consent für `Application.Read.All` erteilen darf (Global Admin oder entsprechend delegiert).
5. **Funktioniert das auch für mehrere Kunden-Tenants?** Der Check läuft pro Tenant. Für die dauerhafte Überwachung mehrerer Kunden-Tenants ist SecretExpiry gebaut.
6. **Kann ich die Berechtigung wieder entfernen?** Ja, jederzeit im Entra-Portal unter Enterprise Applications — der Check funktioniert einmalig und braucht keine dauerhafte Verbindung.

## 5. Verbreitung (nutzt vorhandene Assets)

1. **Reddit:** Der Check ist die perfekte Antwort in genau den Threads aus Block 1 (r/AZURE, r/sysadmin, r/msp Secret-Threads) — „ich habe dafür einen kostenlosen Read-only-Check gebaut" ist in den verschärften Promo-Regeln (Learning 4.5) das einzige Format, das als Beitrag statt als Werbung gelesen wird. Auch als eigener Post tauglich: „I built a free read-only check for expired Entra secrets" + echte aggregierte Zahlen („über alle Checks: durchschnittlich X abgelaufene Secrets pro Tenant") als Build-in-Public-Material.
2. **Directory-Blitz:** Der Check ist als eigenständiges Free-Tool **separat listbar** (AlternativeTo, Uneed, freie Tool-Verzeichnisse) — verdoppelt die Directory-Backlinks (Learning 2 + die fertigen Listen aus Learning 4.4).
3. **LinkedIn:** B1-Hook-Posts enden künftig mit dem Check-Link statt mit einer rhetorischen Frage.
4. **AEO:** Die Landingpage beantwortet „how do I find expired secrets in Entra ID" — eine Query, für die aktuell nur PowerShell-Blogposts ranken; ein interaktives Tool ist das bessere Suchergebnis (auch für KI-Engines).

## 6. Erfolgsmessung

- Checks gestartet → Consent erteilt (Abbruchquote am Consent = Vertrauenshürde)
- Ergebnis gesehen → SecretExpiry-Trial gestartet (Kern-Conversion; Ziel initial ≥ 5 %)
- PDF-Leads (sekundär)
- Aggregierte anonyme Statistik als Content-Quelle („Durchschnitts-Tenant hat X abgelaufene Secrets")

## 7. Übertragung auf GALYNSKI (ehrliche Einschätzung)

Ein „GAL-Mobile-Check" ist technisch **nicht** analog machbar — ob Kontakte auf Handys ankommen, lässt sich per API nicht von außen prüfen. Realistische Alternativen: (a) ein **GAL-Hygiene-Check** (liest die GAL read-only und zeigt: X Einträge ohne Telefonnummer, Y Räume/Systemkonten, die auf Handys landen würden, Z potenzielle Dubletten) — gleicher Funnel-Mechanismus, etwas schwächerer Aha-Moment; oder (b) ein simpler **Kosten-/Zeit-Rechner** („Was kostet Sie manuelles Kontakte-Pflegen bei N Mitarbeitenden?") — billig zu bauen, aber generischer. Empfehlung: erst den Secret-Check validieren, dann (a) entscheiden.
