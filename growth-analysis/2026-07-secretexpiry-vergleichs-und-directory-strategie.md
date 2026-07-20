# SecretExpiry: Wettbewerbslandschaft, Directory-Ziele & erste Vergleichsseite

**Stand:** 2026-07-20 · **Herleitung:** Übertragung der GALYNSKI-Sichtbarkeitsstrategie (Directories + Vergleichsseiten, siehe Learning 3 im Hauptreport) auf SecretExpiry, auf Wunsch von Philipp König.

---

## 1. Produktfakten (verifiziert 2026-07-20 via curl gegen secretexpiry.com)

- **Zero-Knowledge-Architektur:** liest nie die tatsächlichen Secret-Werte, nur Metadaten (Ablaufdatum) — zentrales Vertrauensargument, deckt sich mit dem bereits im Secret-Ablauf-Check-Konzept verwendeten Punkt.
- Kostenloser Einstieg möglich („Get started for free“), kostenpflichtige Pläne darüber
- Multi-Tenant-fähig (MSP Pro sichtbar in der Produkt-Demo) — direkter Treffer für Pain-Point-Cluster #4 im Hauptreport (MSP-/Multi-Tenant-Skalierungsproblem, Buying-Intent 8/10)
- EU-Hosting in Frankfurt, DSGVO-konform, AES-256-Verschlüsselung
- Setup unter 2 Minuten, vollautomatischer täglicher Sync, kein Code nötig
- Smart-Email-Alerts

## 2. Reale Wettbewerber & Alternativen (recherchiert 2026-07-20)

Anders als bei GALYNSKI ist der Markt hier fragmentierter: SecretExpiry konkurriert nicht mit einer Handvoll klarer Direktkonkurrenten, sondern mit (a) einer Nischenfunktion in größeren RMM-/Monitoring-Suiten, (b) DIY-PowerShell-Skripten und (c) einem direkten Feature-Konkurrenten.

| Anbieter/Ansatz | Typ | Einordnung | Quelle |
|---|---|---|---|
| **ReconAI** (Model Technology Solutions) | Direkter Feature-Wettbewerber | Bewirbt „Certificate & App Secret Expiration Monitoring“ als neues Feature — bereits in Block 1 des Hauptreports als Wettbewerbsbeobachtung erfasst. | [LinkedIn-Post, siehe Hauptreport Block 1](https://www.linkedin.com/posts/model-technology-solutions_model-technology-solutions-it-infrastructure-activity-7430354501204684800-7LeF) |
| **Turbo360** | Breite Azure-Monitoring-Plattform | Enterprise-Tool mit App-Registration-Cert-/Secret-Monitoring als *eines von vielen* Features (Kosten-Optimierung, Ressourcen-Monitoring etc.) — kein Spezialist, aber oft schon im Tenant vorhanden. | [turbo360.com/blog](https://turbo360.com/blog) |
| **AdminDroid** | M365-Reporting-Suite | Bietet Application Reports inkl. Client-Secret-Ablaufdetails als Teil eines riesigen Reporting-Pakets (Hunderte Reports) — Admins nutzen es oft schon für anderes und „finden" die Secret-Ablauf-Funktion nebenbei, statt aktiv danach zu suchen. | [blog.admindroid.com](https://blog.admindroid.com/retrieve-entra-app-registrations-with-expiring-client-secrets-and-certificates/) |
| **CIPP, Liongard, Rewst, LogicMonitor, GoGenuity** | RMM/PSA-Tools mit Teil-Abdeckung | Von r/msp-Nutzern selbst als Alternativen genannt (Block 1, Cluster #4) — decken Secret-Monitoring meist nur als Nebenfunktion einer viel größeren, teureren RMM-Suite ab. Kein 1:1-Vergleich sinnvoll (andere Kategorie/Preisklasse), aber wichtig für die Positionierung „spezialisiert vs. Suite". | Reddit r/msp (siehe Hauptreport) |
| **DIY-PowerShell-Skripte** (o365reports.com, thelazyadministrator.com, ssw.com.au, gowthamcbe.com, duo-infernale.ch, softwareone.com) | Kein Produkt, aber der **meistgewählte** „Wettbewerber" | Mehrere unabhängige Admin-Blogs veröffentlichen eigene Skripte/Logic Apps für exakt dieses Problem — das bestätigt die höchste Buying-Intent-Zahl im ganzen Report (9/10, Cluster B1) UND zeigt gleichzeitig den größten Content-/Backlink-Hebel: diese Blogs schreiben bereits genau über das Problem, das SecretExpiry löst. | siehe Linkliste unten |

**Wichtigste Erkenntnis:** Der eigentliche Wettbewerber ist meistens nicht ein anderes Produkt, sondern die eigene DIY-PowerShell-Lösung des Admins. Das deckt sich exakt mit dem bereits im Report dokumentierten Cluster „Jeder baut dasselbe PowerShell-Rad neu" (Buying-Intent 7/10) — die stärkste, am besten belegte Vergleichsseite ist daher „SecretExpiry vs. Eigenbau" statt ein Produkt-vs-Produkt-Vergleich.

## 3. Größte offene Chance: Azure Marketplace / Microsoft AppSource

Wie bei TeamsDashboard: **keine Listung** für „SecretExpiry“ im Azure Marketplace oder AppSource gefunden. Für ein Produkt, das direkt auf Microsoft-Entra-Daten arbeitet, ist das der naheliegendste Vertriebskanal — Kunden suchen dort aktiv nach Security-/Compliance-Tools für ihren Tenant. Auch hier gilt: echte Marketplace-Listung erfordert Partner-Center-Registrierung, technische Validierung und ggf. eine SaaS-Fulfillment-API-Anbindung für die Abrechnung — kein kurzfristiger Task, aber der wirkungsvollste Prio-3-Punkt für die Techniker-Anweisung.

## 4. Directory- & Content-Ziele (sofort umsetzbar, kostenlos)

**Directories:**
- G2/Capterra: Kategorie „Security Compliance Software“ bzw. „Identity & Access Management" — SecretExpiry fehlt dort.
- AlternativeTo: als Alternative zu „Azure Key Vault"-Monitoring-Setups eintragen.
- SoftwareSuggest/GetApp: Kategorie „Cloud Security"/"IT Compliance".

**Content-/Backlink-Ziele (Blogs, die bereits über exakt dieses Problem schreiben — Gastbeitrags- oder Erwähnungs-Kandidaten):**
- [SharePointDiary](https://www.sharepointdiary.com/2024/07/app-registration-secret-certificate-expiration-notification.html)
- [AdminDroid Blog](https://blog.admindroid.com/retrieve-entra-app-registrations-with-expiring-client-secrets-and-certificates/) (auch potenzieller Kooperationspartner statt nur Wettbewerber — Reporting-Fokus vs. SecretExpiry-Monitoring-Fokus ergänzen sich)
- [o365reports.com](https://o365reports.com/an-overview-of-client-secret-management-in-azure-ad/)
- [The Lazy Administrator](https://www.thelazyadministrator.com/2023/12/16/automated-alerts-on-azure-entra-id-application-secret-expirations/)
- [SSW.Rules](https://www.ssw.com.au/rules/expiring-app-secrets-certificates)
- [Gowtham K](https://gowthamcbe.com/2024/08/30/email-notification-for-entra-id-application-secret-key-expiry/)
- [duo-infernale.ch](https://duo-infernale.ch/tackling-expiring-entra-id-client-secrets-and-saml-certificates/)
- [SoftwareOne Blog](https://www.softwareone.com/en/blog/articles/2022/09/29/monitoring-client-secret-and-certificates)

Vorgehen: höflicher Kommentar/E-Mail an die Autor:innen mit Verweis „falls Ihre Leser eine fertige Lösung statt Eigenbau suchen" — kein Spam, sondern echter Mehrwert-Hinweis (gleiche Regel wie bei den Reddit-Kommentaren im Hauptreport).

## 5. Vergleichsseite: SecretExpiry vs. Eigenbau (PowerShell-Skript)

**URL-Vorschlag:** `secretexpiry.com/vergleich/powershell-skript-alternative`
**Title (57 Z.):** `SecretExpiry vs. eigenes PowerShell-Skript: Was lohnt sich?`
**Meta-Description (156 Z.):** `Ein PowerShell-Skript für Secret-Ablauf-Monitoring ist in einer Stunde geschrieben — aber wer wartet es? Der ehrliche Vergleich mit einer fertigen Lösung.`

### H1
SecretExpiry vs. eigenes PowerShell-Skript: Was lohnt sich wirklich?

### Kurz beantwortet (Box)
> Ein PowerShell-Skript zur Secret-Ablauf-Prüfung ist schnell geschrieben, aber laut zahlreichen IT-Admin-Foren (r/sysadmin, r/AZURE) verlässlich der Teil, der bricht: kein Ownership-Tracking, keine Multi-Tenant-Übersicht, niemand liest die CSV-Mail nach der ersten Woche. SecretExpiry übernimmt genau das dauerhaft: automatischer täglicher Sync, Zero-Knowledge-Architektur (liest nie die Secret-Werte selbst), Multi-Tenant-fähig, EU-Hosting. Für ein einzelnes System reicht oft ein Skript — für laufende Verantwortung über mehrere Tenants nicht.

### H2: Warum bauen so viele Admins ihr eigenes Skript?
Weil Microsoft selbst keine eingebaute Warnung außer einer einzigen E-Mail 30 Tage vor Ablauf bietet. Ein erstes Skript mit `Get-MgApplication` und einem Logic-App-Trigger ist in ein bis zwei Stunden geschrieben — das bestätigen mehrere unabhängige Blogs (SharePointDiary, The Lazy Administrator, Gowtham K, SSW.Rules), die alle eigene Varianten davon veröffentlicht haben. Das Problem beginnt erst danach.

### H2: Wo brechen DIY-Skripte in der Praxis?
In echten Admin-Diskussionen (r/sysadmin, Thread „How are people tracking expiring Azure/Entra app secrets and certificates?") wiederholt sich ein Muster: Das Skript läuft eine Weile zuverlässig, dann ändert sich die Umgebung (neuer Tenant, neue App-Registration-Struktur), niemand pflegt es mehr, und die generierte CSV-Datei landet in einem E-Mail-Postfach, das niemand regelmäßig liest. Ein zweites, ebenso häufig genanntes Problem: Ownership — das Skript findet zwar ablaufende Secrets, aber nicht, wer für die jeweilige App verantwortlich ist.

### H2: Was übernimmt SecretExpiry, was ein Skript nicht leistet?
Dauerhafter, automatischer täglicher Sync ohne Wartung, eine zentrale Oberfläche statt CSV-Mails, Multi-Tenant-Ansicht für IT-Dienstleister mit mehreren Kunden, und eine Zero-Knowledge-Architektur als zusätzliches Vertrauensargument gegenüber selbstgeschriebenem Code, der oft mit zu weitreichenden Berechtigungen läuft. Setup dauert unter zwei Minuten, kein eigener Code nötig.

### H2: Wann reicht ein eigenes Skript aus?
Für einen einzelnen Tenant mit wenigen App-Registrations und einem Admin, der die CSV tatsächlich zuverlässig liest, ist ein einfaches Skript eine legitime, kostenlose Lösung. Der Umschlagpunkt liegt dort, wo entweder mehrere Tenants dazukommen (MSP-Fall), das Skript niemand mehr pflegt, oder Ownership-Fragen regelmäßig zu Verzögerungen führen.

### FAQ (FAQPage-JSON-LD)
1. **Ist ein PowerShell-Skript nicht kostenlos und SecretExpiry nicht?** Das Skript selbst ja, der Wartungsaufwand nicht — SecretExpiry bietet zudem einen kostenlosen Einstiegsplan.
2. **Kann SecretExpiry mein bestehendes Skript ersetzen?** Ja, ohne dass Sie den Sync-Mechanismus selbst pflegen müssen.
3. **Liest SecretExpiry meine tatsächlichen Secret-Werte?** Nein — Zero-Knowledge-Architektur, es werden ausschließlich Ablauf-Metadaten gelesen, technisch identisch zu dem, was auch ein eigenes Skript über die Graph-API abfragen würde.
4. **Was passiert bei mehreren Kunden-Tenants?** Dafür ist die Multi-Tenant-Ansicht (MSP-Modus) gebaut — ein Skript müsste dafür separat für jeden Tenant gepflegt werden.
5. **Wie lange dauert die Einrichtung?** Unter zwei Minuten, ohne eigenen Code.
6. **Was, wenn ich schon ein funktionierendes Skript habe?** Dann prüfen Sie am besten, ob es Ownership-Zuordnung und Multi-Tenant-Fähigkeit abdeckt — das sind die beiden Punkte, an denen DIY-Lösungen laut Admin-Foren am häufigsten scheitern.

---

## Nächste Schritte (Checkliste)

- [ ] Vergleichsseite oben veröffentlichen (Text ist publikationsfertig)
- [ ] G2/Capterra Security-Compliance-Kategorie eintragen
- [ ] Kontaktaufnahme mit den 6 gelisteten Admin-Blogs (Mehrwert-Hinweis, kein Spam)
- [ ] Azure-Marketplace-/AppSource-Listung als eigenes Entwicklungsprojekt in die Techniker-Anweisung aufnehmen (Prio 3)
- [ ] Zweite Vergleichsseite gegen ReconAI erwägen, sobald mehr öffentliche Fakten zu ReconAI vorliegen (aktuell nur ein LinkedIn-Post bekannt, zu dünn für einen fairen Vergleich)
