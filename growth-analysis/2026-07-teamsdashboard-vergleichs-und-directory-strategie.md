# TeamsDashboard: Wettbewerbslandschaft, Directory-Ziele & erste Vergleichsseite

**Stand:** 2026-07-20 · **Herleitung:** Übertragung der GALYNSKI-Sichtbarkeitsstrategie (Directories + Vergleichsseiten, siehe Learning 3 im Hauptreport) auf TeamsDashboard, auf Wunsch von Philipp König.

---

## 1. Produktfakten (verifiziert 2026-07-20 via curl gegen teamsdashboard.com)

- **Preis:** 4,25 €/User/Monat, ein Preis für alle Features (Standard-Lizenz)
- **Enterprise:** White-Labeling, eigene Subdomain (`firma.teamsdashboard.com`), Corporate Design, MSAL-Login — auf Anfrage
- 14 Tage kostenlos testen, keine Kreditkarte
- 4 Ansichten (Karten/Kompakt/Minimal/Liste), Live-Status alle 15 Sekunden, Telefonnummern sichtbar mit 1-Klick-Anruf, Filter & Gruppierung nach beliebigen Feldern, Vollbild-Modus
- **Kernpositionierung:** kein Teams-internes Widget, sondern ein eigenständiges Web-Dashboard (Browser-URL) — explizit für Lobby-Displays, Empfangsbereiche, Team-Monitore gedacht. Keine Installation nötig, Hosting in Deutschland, DSGVO-konform.

## 2. Reale Wettbewerber (recherchiert 2026-07-20)

| Anbieter | Typ | Kernunterschied zu TeamsDashboard | Quelle |
|---|---|---|---|
| **Team Board** (teamboard.in) | In-Teams-App, $5/User/**Jahr** | Läuft *innerhalb* des Teams-Clients als installierte App (via AppSource), nicht als eigenständiges Display. 64K+ Nutzer, 1.100+ Organisationen laut eigener Angabe — etablierter, viel günstigerer Wettbewerber, aber anderes Einsatzszenario (persönliches Widget statt Wandbildschirm/Empfang). | [teamboard.in](https://teamboard.in/) |
| **Simple In/Out** | In/Out-Statustafel, integriert in Teams/Outlook/M365 | Ähnlich wie Team Board: Status-Board *innerhalb* bestehender M365-Oberflächen, kein eigenständiges Wallboard. | [simpleinout.helpscoutdocs.com](https://simpleinout.helpscoutdocs.com/article/262-microsoft-teams) |
| **Enable 365 Presence** | Presence-/Workforce-App für Teams | Fokus auf Homeoffice/Büro-Anwesenheit, ebenfalls App-basiert statt Display-basiert. | [enable365.ai/apps/presence](https://enable365.ai/apps/presence/) |
| **MSB365 Teams Presence Dashboard** | **Open Source, kostenlos** (GitHub) | Die relevanteste Bedrohung für Preis-sensible Kunden: DIY-Alternative für IT-Teams, die selbst hosten/warten können — exakt die Zielgruppe aus Pain-Point-Cluster #4 im Hauptreport („Wir bauen das über Graph API selbst, ist aber kompliziert"). | [msb365.blog](https://www.msb365.blog/?p=5867) |
| **Bridge Wallboard** | Companion-App für Teams Contact-Center/Call-Center | Nischenprodukt für Call-Center-Umgebungen, nicht für allgemeine Büro-/Empfangs-Displays. | [bridgeoc.com/lync/wb.htm](https://www.bridgeoc.com/lync/wb.htm) |

**Wichtigste Erkenntnis:** Kein einziger der gefundenen Wettbewerber adressiert das Display-/Wallboard-/Empfangs-Szenario (Cluster #3 „Empfang braucht Präsenz + Anrufweiterleitung“ und #4 „Physische Displays/Türschilder“ im Hauptreport) so direkt wie TeamsDashboard. Team Board & Co. sind persönliche In-App-Widgets für den einzelnen Nutzer-Desktop, kein Ersatz für einen Wandbildschirm im Empfangsbereich. Das ist die ehrliche und verteidigbare Differenzierung — **nicht** behaupten, günstiger oder funktional überlegen zu sein (Team Board ist bei reiner Presence-Anzeige ca. 10× günstiger pro User/Monat).

## 3. Größte offene Chance: Microsoft AppSource / Teams Store

**Rechercheergebnis (2026-07-20):** Weder „TeamsDashboard“ noch „teamsdashboard.com“ taucht in Microsoft AppSource oder dem Teams-App-Katalog auf. Team Board und Simple In/Out sind dort gelistet — das ist wahrscheinlich der Haupttreiber für Team Boards 64K+ Nutzer (Installation direkt aus dem Teams-Client heraus, keine externe Suche nötig).

**Aber:** TeamsDashboard ist bewusst als eigenständiges Web-Dashboard gebaut (keine Installation, browserbasiert) — eine AppSource-/Teams-Store-Listung würde eine echte Teams-App (Tab/Personal-App-Manifest, Zertifizierungsprozess, ggf. Single-Sign-On via Teams SSO) erfordern. Das ist **kein Nachmittags-Task**, sondern ein eigenes Entwicklungsprojekt mit Microsoft-Zertifizierung (Validierungsrichtlinien, Sicherheitsprüfung, mehrwöchiger Review). Empfehlung: als eigenständigen Prio-3-Punkt in die Techniker-Anweisung aufnehmen (siehe unten), nicht selbst vortäuschen.

Realistische Zwischenlösung bis dahin: ein leichtgewichtiger **Personal-Tab in Teams**, der lediglich auf das bestehende Web-Dashboard verlinkt/es einbettet (iFrame-Tab, deutlich weniger Aufwand als eine volle Bot-/Messaging-Extension), würde für die AppSource-Sichtbarkeit bereits ausreichen.

## 4. Directory- & Verzeichnis-Ziele (sofort umsetzbar, kostenlos)

- **Capterra — Kategorie „Wallboard Display“:** [capterra.com/p/168392/Wallboard-Display](https://www.capterra.com/p/168392/Wallboard-Display/) — passende Kategorie, dort listen u. a. OptiSigns/Yodeck. TeamsDashboard fehlt.
- **G2 — Kategorie „Wallboard Display“ Alternativen:** [g2.com/products/wallboard-display/competitors/alternatives](https://www.g2.com/products/wallboard-display/competitors/alternatives)
- **SoftwareSuggest / GetApp:** unter „Digital Signage Software“ bzw. „Workplace Management Software“ eintragen (gleiches Prinzip wie bei den GALYNSKI-Directory-Zielen in Learning 3).
- **AlternativeTo:** als „Alternative zu Microsoft Teams“ (Feature-Ergänzung, nicht Ersatz) eintragen — passt zur Homepage-eigenen Gegenüberstellung „Microsoft Teams vs. Teams Dashboard“.

## 5. Vergleichsseite: TeamsDashboard vs. Team Board

**URL-Vorschlag:** `teamsdashboard.com/vergleich/team-board-alternative`
**Title (58 Z.):** `TeamsDashboard vs. Team Board: Welches Tool für welchen Zweck?`
**Meta-Description (151 Z.):** `TeamsDashboard und Team Board lösen unterschiedliche Probleme: persönliches Presence-Widget vs. Wandbildschirm für Empfang & Büro. Der ehrliche Vergleich.`

### H1
TeamsDashboard vs. Team Board: Persönliches Widget oder Wandbildschirm?

### Kurz beantwortet (Box)
> Team Board ist eine App **innerhalb** von Microsoft Teams für die persönliche Desktop-Ansicht (ab 5 $/User/Jahr, über AppSource installiert). TeamsDashboard ist ein **eigenständiges Web-Dashboard** für Lobby-Bildschirme, Empfangsbereiche und Team-Monitore — kein Teams-Login der Betrachtenden nötig, Vollbild-optimiert, mit klickbaren Telefonnummern. Wer eine persönliche Statusübersicht im eigenen Teams-Client sucht, ist bei Team Board richtig; wer einen Bildschirm im Empfang oder Flur mit Live-Status aller Mitarbeitenden zeigen will, bei TeamsDashboard.

### H2: Was ist der grundsätzliche Unterschied?
Team Board wird wie eine normale Teams-App aus dem AppSource-Katalog installiert und läuft als Tab oder Panel innerhalb des Teams-Clients — jede Person sieht es nur, wenn sie selbst in Teams eingeloggt ist und die App geöffnet hat. TeamsDashboard läuft dagegen als Webseite mit eigener URL, die auf jedem Bildschirm ohne Teams-Login angezeigt werden kann: am Empfangstresen, auf einem Flur-Monitor oder als Türschild. Für die Frage „Wer ist gerade im Büro?“ auf dem eigenen Rechner ist das ein Detail — für einen gemeinsam sichtbaren Bildschirm im Empfangsbereich ist es der entscheidende Unterschied.

### H2: Was kostet welche Lösung?
Team Board kostet 5 $/User/Jahr (ca. 0,42 $/Monat) und ist damit für reine Presence-Anzeige deutlich günstiger. TeamsDashboard kostet 4,25 €/User/Monat, bietet dafür aber vier Anzeige-Modi speziell für gemeinsam genutzte Bildschirme, 1-Klick-Anruf über sichtbare Telefonnummern und optional White-Labeling mit eigener Subdomain für Enterprise-Kunden. Der Preisvergleich ist nur fair, wenn man den Anwendungsfall vergleicht: ein Empfangs- oder Flurbildschirm braucht keine Team-Board-Lizenz pro Betrachter, sondern eine einmalige TeamsDashboard-Lizenz für die anzeigenden Nutzer-Accounts.

### H2: Kann ich beide gleichzeitig nutzen?
Ja — die Tools schließen sich nicht aus. Team Board eignet sich für Mitarbeitende, die im eigenen Teams-Client schnell sehen wollen, wer gerade verfügbar ist. TeamsDashboard eignet sich für den gemeinsam sichtbaren Bildschirm, den auch Besucher:innen am Empfang oder Kolleg:innen ohne eigenen Teams-Zugriff (z. B. an einem reinen Anzeige-Terminal) sehen. Viele Unternehmen, die aktuell nach einem „Empfangsdisplay mit Teams-Status“ suchen (siehe reale Foren-Threads in Block 1 des Hauptreports), haben dieses Szenario noch gar nicht mit einer fertigen Lösung abgedeckt.

### H2: Für wen ist Team Board die bessere Wahl?
Für Teams, die ausschließlich eine persönliche Verfügbarkeitsübersicht *im* Teams-Client wollen — inklusive 1-Klick-Nachrichten, Anrufe und Videocalls direkt aus der App heraus — und dabei den niedrigsten Preis pro Nutzer suchen. Das ist eine faire und für viele Teams völlig ausreichende Lösung.

### FAQ (FAQPage-JSON-LD)
1. **Ist Team Board eine direkte Alternative zu TeamsDashboard?** Teilweise — beide zeigen Teams-Präsenzstatus, aber Team Board läuft im Teams-Client selbst, TeamsDashboard als eigenständiges Web-Dashboard für gemeinsam genutzte Bildschirme.
2. **Brauche ich für ein Empfangsdisplay eine Teams-Lizenz pro Betrachter?** Bei TeamsDashboard nein — die Lizenz gilt für die angezeigten Nutzer-Accounts, nicht für jede Person, die den Bildschirm ansieht.
3. **Läuft TeamsDashboard auch ohne Installation?** Ja, es ist eine Web-App, die per Browser-URL aufgerufen wird — keine Teams-App-Installation, kein IT-Rollout nötig.
4. **Was ist günstiger?** Team Board bei reiner Presence-Anzeige pro Nutzer im eigenen Client. TeamsDashboard bei einem zentralen Display für mehrere Betrachtende (Empfang, Flur, Lobby).
5. **Kann ich TeamsDashboard auf einem TV im Empfangsbereich anzeigen?** Ja, dafür ist der Vollbild-Modus mit vier Ansichts-Varianten gebaut.
6. **Bietet TeamsDashboard auch White-Labeling?** Ja, im Enterprise-Paket inklusive eigener Subdomain und Corporate Design.

---

## Nächste Schritte (Checkliste)

- [ ] Vergleichsseite oben veröffentlichen (Text ist publikationsfertig)
- [ ] Capterra „Wallboard Display“ + G2-Pendant eintragen
- [ ] SoftwareSuggest/GetApp unter Digital-Signage/Workplace-Management eintragen
- [ ] AppSource-/Teams-Store-Listung als eigenes Entwicklungsprojekt in die Techniker-Anweisung aufnehmen (Prio 3, mit Hinweis auf Zertifizierungsaufwand)
- [ ] Preisangaben (Team Board $5/Jahr) vor Veröffentlichung erneut prüfen — Wettbewerberpreise ändern sich
