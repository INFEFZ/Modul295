|               |                                           |                                        |
| ------------- | ----------------------------------------- | -------------------------------------: |
| **Modul 295** | **Backend für Applikationen realisieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

# **Projekt «HelpDesk AI API» – Support-Ticket-Backend mit KI-gestützten Antwortvorschlägen**

## 1. Übersicht

|                   |                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Modul**         | 295 – Backend für Applikationen realisieren                                                                                                     |
| **Kompetenz**     | Implementiert mittels vorgegebener Technologie eine Back-End-Schnittstelle, welche aktuelle Schnittstellen-Standards einhält.                   |
| **Kompetenzfeld** | Web Engineering                                                                                                                                 |
| **Zielgruppe**    | Modul-Nachholende, die die übrigen Ausbildungsmodule bereits abgeschlossen haben                                                                |
| **Sozialform**    | Einzelarbeit                                                                                                                                    |
| **Zeitaufwand**   | ca. 20–25 Stunden Umsetzung + ca. 1 Stunde Vorbereitung der Abschlusspräsentation                                                               |
| **Technologie**   | Visual Studio 2022 (oder neuer), C#, ASP.NET Core Web API (aktuelle .NET-LTS-Version), Entity Framework Core, SQLite, xUnit, Git                |
| **Abgabe**        | Quellcode inkl. automatisiertem Testprojekt (mit Git-Historie) + technische Dokumentation + Testnachweise + Abschlusspräsentation mit Live-Demo |

Dieser Projektauftrag ist die zweite, eigenständige Variante für Modul-Nachholende mit KI-Bezug (analog zum bisherigen ToolTrack-Auftrag, jedoch mit neuem Szenario und neuer Domäne, damit keine inhaltliche Überschneidung entsteht). Er deckt weiterhin alle sechs Handlungsziele des Moduls 295 sowie die zugehörigen handlungsnotwendigen Kenntnisse gemäss Modulidentifikation (modulbaukasten.ch) vollständig ab; die Zuordnung ist in Abschnitt 6 und im Bewertungsraster (Abschnitt 11) ersichtlich. Der Auftrag schliesst mit einer bewerteten Abschlusspräsentation inkl. Live-Demo ab (Abschnitt 6.7).

> **Hinweis zum KI-Anteil:** Im Zentrum des Moduls 295 steht die Backend-Architektur, nicht die KI selbst. Die eigentliche KI-Logik wird deshalb bewusst hinter einer klaren Abstraktion (Interface) gekapselt; wie in Abschnitt 6.2 beschrieben, können Studierende frei wählen, ob sie eine echte LLM-API oder eine simulierte/regelbasierte KI-Komponente implementieren.

---

## 2. Ausgangslage

Der fiktive IT-Dienstleister **NordTech Support AG** betreibt für seine Kundschaft einen Helpdesk. Support-Mitarbeitende erfassen eingehende Anfragen als **Tickets** (z. B. „Drucker im 2. OG druckt nicht mehr", „Zugriff auf Projektlaufwerk fehlt") und bearbeiten diese bis zur Lösung. Bisher erfolgt die Erfassung in einer einfachen Tabelle, was zu langen Reaktionszeiten und inkonsistenter Kommunikation führt.

Die Geschäftsleitung möchte zwei Verbesserungen: Erstens eine strukturierte **Backend-Schnittstelle (API)** zur Verwaltung von Tickets und deren Antworten. Zweitens sollen Support-Mitarbeitende bei der Beantwortung entlastet werden, indem das System auf Knopfdruck einen **KI-gestützten Antwortvorschlag** zu einem Ticket generiert, den die Mitarbeitenden übernehmen, anpassen oder verwerfen können – der Mensch bleibt dabei immer in der Verantwortung für die tatsächlich versendete Antwort.

Zusätzlich soll zwischen zwei Arten von Benutzenden unterschieden werden: **Support-Mitarbeitende** dürfen Tickets und Antworten erfassen, bearbeiten und KI-Vorschläge anfordern. Das Löschen von Tickets oder Antworten (z. B. bei Fehlerfassungen oder Spam) ist der **Teamleitung** vorbehalten.

Die IT-Abteilung hat bereits eine kleine SQLite-Datenbank mit den Tabellen `Tickets` und `TicketAntworten` sowie Testdaten bereitgestellt (siehe Abschnitt 5). Ihre Aufgabe ist es, darauf aufbauend eine vollständige, dokumentierte, getestete und abgesicherte Back-End-Schnittstelle inkl. KI-Anbindung zu realisieren.

---

## 3. Auftrag

Realisieren Sie als Einzelarbeit mit **Visual Studio und C#** eine **ASP.NET Core Web API**, die

- den lesenden und schreibenden Zugriff (CRUD) auf die vorgegebenen Datenquellen `Tickets` und `TicketAntworten` ermöglicht und dabei die Geschäftsregel «zu einem geschlossenen Ticket können keine neuen Antworten mehr erfasst werden» durchsetzt,
- über einen Endpunkt verfügt, der für ein Ticket einen **KI-gestützten Antwortvorschlag** generiert und als spezielle Antwort speichert,
- die KI-Logik hinter einer sauberen Abstraktion (Interface + Dependency Injection) kapselt, sodass eine echte oder eine simulierte Implementierung austauschbar ist,
- aktuelle Schnittstellen-Standards einhält und vollständig dokumentiert ist (OpenAPI/Swagger),
- mit automatisierten Tests (Unit- und Integrationstests) sowie manuellen Tests gegen die Anforderungen abgeglichen wird, definierte Coderichtlinien erfüllt, in einem Softwareverwaltungssystem nachvollziehbar versioniert wird, und über einen rollenbasierten Authentifizierungsmechanismus (Rollen «Support-Mitarbeiter» und «Teamleitung») verfügt, der die Zugriffsrechte entsprechend der Ausgangslage differenziert.

---

## 4. Rahmenbedingungen

- **Zielgruppe:** Modul-Nachholende mit bereits abgeschlossenen übrigen Ausbildungsmodulen (entsprechend anspruchsvollerer Umfang)
- **Sozialform:** Einzelarbeit
- **Zeitrahmen:** ca. 20–25 Stunden Umsetzung (siehe Zeitbudget je Handlungsziel in Abschnitt 6) plus ca. 1 Stunde Vorbereitung der Abschlusspräsentation
- **Entwicklungsumgebung:** Visual Studio 2022 oder neuer, aktuelle LTS-Version von .NET (z. B. .NET 8 oder .NET 10)
- **Datenzugriff:** Entity Framework Core mit SQLite-Provider
- **Schnittstellen-Standard:** RESTful API mit JSON, dokumentiert über OpenAPI/Swagger
- **Testframework:** xUnit für automatisierte Unit- und Integrationstests (`WebApplicationFactory`)
- **Authentifizierung/Autorisierung:** JWT (JSON Web Token) mit Rollen-Claims («Support-Mitarbeiter», «Teamleitung»)
- **KI-Anbindung:** freie Wahl zwischen einer echten LLM-API (z. B. OpenAI, Azure OpenAI) oder einer simulierten/regelbasierten Komponente – siehe Abschnitt 6.2 für die konkreten Anforderungen an beide Varianten
- **Versionsverwaltung:** Git (lokal oder auf GitHub/GitLab/Azure DevOps)
- **Vorgegebene Datenquelle:** SQLite-Datenbank `helpdesk.db` mit den Tabellen `Tickets` und `TicketAntworten`, Schema und Seed-Daten gemäss Abschnitt 5
- **Abschlusspräsentation:** 15–20 Minuten pro Person, inkl. Live-Demo der lauffähigen Anwendung, wird bewertet (siehe Abschnitt 6.7 und 11.2)
- **Zulässige Hilfsmittel:** Fachliteratur, offizielle Microsoft-Dokumentation, Unterrichtsunterlagen. KI-Tools dürfen unterstützend zum Verständnis eingesetzt werden; der Code muss jedoch selbstständig nachvollzogen und im Rahmen einer allfälligen Rückfrage erklärt werden können. (Dies betrifft die Werkzeugnutzung beim Programmieren – unabhängig davon, ob im Projekt selbst eine KI-Komponente umgesetzt wird.)

---

## 5. Vorgegebene Datenquelle

Die folgende Datenquelle gilt als **gegeben** und ist Ausgangspunkt Ihrer Implementierung (Handlungsziel 2). Führen Sie das Skript in einer neuen SQLite-Datenbank `helpdesk.db` aus, bevor Sie mit der Implementierung beginnen.

```sql
CREATE TABLE Tickets (
    Id              INTEGER PRIMARY KEY AUTOINCREMENT,
    Titel           TEXT    NOT NULL,
    Beschreibung    TEXT    NOT NULL,
    Kategorie       TEXT    NOT NULL,      -- z.B. "Hardware", "Software", "Netzwerk", "Zugriffsrechte"
    Prioritaet      TEXT    NOT NULL,      -- "Niedrig", "Mittel", "Hoch", "Kritisch"
    Status          TEXT    NOT NULL,      -- "Offen", "InBearbeitung", "Geloest", "Geschlossen"
    ErstelltVon     TEXT    NOT NULL,      -- Name/E-Mail der Kundschaft
    ErstelltAm      TEXT    NOT NULL,      -- Format: YYYY-MM-DD
    GeschlossenAm   TEXT    NULL           -- NULL solange nicht geschlossen
);

INSERT INTO Tickets (Titel, Beschreibung, Kategorie, Prioritaet, Status, ErstelltVon, ErstelltAm, GeschlossenAm) VALUES
('Drucker im 2. OG druckt nicht', 'Der Netzwerkdrucker im 2. OG zeigt einen Papierstau an, obwohl kein Papier gestaut ist.', 'Hardware', 'Mittel', 'Offen', 'anna.keller@nordtech.ch', '2026-08-01', NULL),
('Zugriff auf Projektlaufwerk fehlt', 'Ich habe seit dem Rollenwechsel keinen Zugriff mehr auf das Laufwerk P:\\Projekte.', 'Zugriffsrechte', 'Hoch', 'InBearbeitung', 'michael.frei@nordtech.ch', '2026-08-03', NULL),
('Outlook stürzt beim Start ab', 'Outlook 365 stürzt seit dem letzten Update jedes Mal beim Öffnen ab.', 'Software', 'Hoch', 'Offen', 'sara.moser@nordtech.ch', '2026-08-05', NULL),
('WLAN im Sitzungszimmer instabil', 'Die WLAN-Verbindung bricht im grossen Sitzungszimmer alle paar Minuten ab.', 'Netzwerk', 'Niedrig', 'Geloest', 'urs.baumann@nordtech.ch', '2026-07-20', NULL),
('Passwort-Reset benötigt', 'Ich habe mein Passwort vergessen und benötige einen Reset.', 'Zugriffsrechte', 'Kritisch', 'Geschlossen', 'lena.hofer@nordtech.ch', '2026-07-15', '2026-07-15');

CREATE TABLE TicketAntworten (
    Id              INTEGER PRIMARY KEY AUTOINCREMENT,
    TicketId        INTEGER NOT NULL,
    Verfasser       TEXT    NOT NULL,
    Text            TEXT    NOT NULL,
    IstKiVorschlag  INTEGER NOT NULL,      -- 0 = manuelle Antwort, 1 = KI-generierter Vorschlag
    ErstelltAm      TEXT    NOT NULL,      -- Format: YYYY-MM-DD
    FOREIGN KEY (TicketId) REFERENCES Tickets (Id)
);

INSERT INTO TicketAntworten (TicketId, Verfasser, Text, IstKiVorschlag, ErstelltAm) VALUES
(2, 'Support-Team', 'Wir prüfen aktuell die Berechtigungsgruppe und melden uns bis morgen zurück.', 0, '2026-08-03'),
(5, 'Support-Team', 'Ihr Passwort wurde zurückgesetzt, das temporäre Passwort wurde Ihnen per SMS zugestellt.', 0, '2026-07-15');
```

> Hinweis: Die Studierenden erstellen darauf aufbauend ihre C#-Datenmodelle (`Ticket`, `TicketAntwort`) inkl. Navigationseigenschaft sowie den `DbContext` passend zu diesem bestehenden Schema.

---

## 6. Aufgabenstellung im Detail

### 6.1 Handlungsziel 1 – Entwicklungsumgebung einrichten *(ca. 1.5 Std.)*

- Installieren/prüfen Sie die benötigten Komponenten: Visual Studio mit ASP.NET-Workload, aktuelle .NET-SDK-Version, EF Core Tools, ggf. DB-Browser für SQLite.
- Erstellen Sie eine Visual-Studio-Solution mit zwei Projekten: dem Web-API-Projekt sowie einem xUnit-Testprojekt.
- Legen Sie die Projektstruktur im API-Projekt an (z. B. Ordner `Models`, `Data`, `DTOs`, `Services`, `Controllers`, `Middleware`).
- Binden Sie die vorgegebene SQLite-Datenbank (`helpdesk.db`) über eine Connection-String-Konfiguration in `appsettings.json` ein.
- Dokumentieren Sie kurz (in der README), welche Komponenten installiert wurden, wie die Solution aufgebaut ist und wie Projekt sowie Tests lokal zum Laufen gebracht werden.

### 6.2 Handlungsziel 2 – Backend-Schnittstelle implementieren und dokumentieren *(ca. 9 Std.)*

Implementieren Sie eine strukturierte REST-API für **zwei zusammenhängende Ressourcen** sowie eine **KI-Vorschlagsfunktion**:

**Tickets:**

| Methode | Route               | Zweck                                                                                                           |
| ------- | ------------------- | --------------------------------------------------------------------------------------------------------------- |
| GET     | `/api/tickets`      | Liste aller Tickets, mit Paginierung, Filterung (z. B. nach `status`, `kategorie`, `prioritaet`) und Sortierung |
| GET     | `/api/tickets/{id}` | Einzelnes Ticket abrufen                                                                                        |
| POST    | `/api/tickets`      | Neues Ticket erfassen                                                                                           |
| PUT     | `/api/tickets/{id}` | Ticket aktualisieren (inkl. Statuswechsel)                                                                      |
| DELETE  | `/api/tickets/{id}` | Ticket löschen                                                                                                  |

**TicketAntworten** (referenziert ein Ticket):

| Methode | Route                                     | Zweck                                                                                                      |
| ------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| GET     | `/api/tickets/{id}/antworten`             | Alle Antworten zu einem Ticket abrufen                                                                     |
| POST    | `/api/tickets/{id}/antworten`             | Manuelle Antwort erfassen (Ticket darf nicht «Geschlossen» sein)                                           |
| POST    | `/api/tickets/{id}/ki-vorschlag`          | KI-gestützten Antwortvorschlag generieren und als Antwort speichern (Ticket darf nicht «Geschlossen» sein) |
| DELETE  | `/api/tickets/{id}/antworten/{antwortId}` | Antwort löschen (z. B. Korrektur einer Fehlerfassung)                                                      |

Anforderungen an die Umsetzung:

- **Geschäftsregel:** Sowohl `POST /api/tickets/{id}/antworten` als auch `POST /api/tickets/{id}/ki-vorschlag` prüfen, ob das Ticket aktuell **nicht** den Status «Geschlossen» hat. Ist es bereits geschlossen, liefert die API `409 Conflict` mit einer verständlichen Fehlermeldung. Wird der Status eines Tickets per `PUT` auf «Geschlossen» gesetzt, wird `GeschlossenAm` automatisch gesetzt.
- **Service-Layer:** Die Geschäftslogik (Statusprüfung, konsistente Aktualisierung, Aufruf der KI-Komponente) ist in einer eigenen Service-Schicht gekapselt, nicht direkt im Controller.
- **KI-Abstraktion:** Definieren Sie ein Interface, z. B.

  ```csharp
  public interface IKiVorschlagService
  {
      Task<string> GenerateVorschlagAsync(string titel, string beschreibung, string kategorie);
  }
  ```

  und implementieren Sie **eine** der folgenden zwei Varianten (freie Wahl, muss in der Dokumentation begründet werden):

  - **Variante A – Echte LLM-Anbindung:** Aufruf eines externen LLM-Dienstes (z. B. OpenAI, Azure OpenAI oder ein vergleichbarer Anbieter) über `HttpClient`. Der API-Key wird **nicht** im Quellcode oder Repository abgelegt, sondern über `dotnet user-secrets` oder eine Umgebungsvariable bereitgestellt. Fehler (z. B. Timeout, fehlender Key, Dienst nicht erreichbar) werden abgefangen und führen zu einer sinnvollen Fehlermeldung statt zu einem Absturz.
  - **Variante B – Simulierte KI:** Eine regel-/vorlagenbasierte Generierung des Vorschlags anhand von Kategorie und Schlüsselwörtern in der Beschreibung (z. B. vordefinierte Textbausteine je Kategorie, kombiniert mit Platzhaltern). Diese Variante ist klar als Simulation zu kennzeichnen (z. B. im Klassennamen `SimulatedKiVorschlagService` und in der Dokumentation) und benötigt keine externe Abhängigkeit.

  In beiden Fällen wird der generierte Vorschlag als neue `TicketAntwort` mit `IstKiVorschlag = true` gespeichert. Die konkrete Implementierung wird über Dependency Injection eingebunden (`builder.Services.AddScoped<IKiVorschlagService, ...>()`), sodass sie bei Bedarf ausgetauscht werden könnte, ohne den restlichen Code anzupassen.
- Sauber getrennte Schichten: Controller, Service-Layer, Datenzugriff (EF Core `DbContext`), Datenmodell/DTOs. Verwendung von DTOs für Ein-/Ausgabe (kein direktes Durchreichen des Entity-Modells nach aussen).
- **Paginierung, Filterung, Sortierung:** `GET /api/tickets` unterstützt mindestens `page`, `pageSize`, eine Filterung (z. B. nach `status` und/oder `kategorie`) sowie eine Sortierung (z. B. `sortBy=Prioritaet&sortDirection=desc`).
- Aussagekräftige HTTP-Statuscodes (200, 201, 204, 400, 404, 409 usw.) und konsistente Fehlerantworten über eine zentrale Exception-Handling-Middleware (`ProblemDetails`).
- Strukturiertes Logging (`ILogger`) für zentrale Vorgänge (Ticket erstellt, Statuswechsel, KI-Vorschlag angefordert/generiert, abgelehnte Antwort, Fehlerfälle).
- Dokumentation der Schnittstelle über **OpenAPI/Swagger** (z. B. Swashbuckle), inkl. Beispielwerten und Beschreibung sämtlicher Endpunkte.
- Ergänzende schriftliche Dokumentation (Markdown oder Word): Architekturüberblick, Datenmodell inkl. Beziehung Ticket–Antwort, Beschreibung der Endpunkte und der Geschäftsregel, gewählte KI-Variante (A oder B) mit Begründung, eingesetzte Technologien.

### 6.3 Handlungsziel 3 – Anforderungen überprüfen, Korrekturen vornehmen *(ca. 4.5 Std.)*

- Testen Sie jeden Endpunkt manuell über Swagger UI oder Postman/Insomnia; dokumentieren Sie die Tests mit Screenshots (Request + Response), inkl. des Konfliktfalls «Antwort/KI-Vorschlag bei geschlossenem Ticket».
- Erstellen Sie **automatisierte Unit-Tests** (xUnit) für die zentrale Geschäftslogik im Service-Layer, u. a.: Antwort zu offenem Ticket gelingt, Antwort zu geschlossenem Ticket wird abgelehnt, Statuswechsel auf «Geschlossen» setzt `GeschlossenAm` korrekt. Testen Sie den KI-Aufruf mit einer **Test-Doppelgänger-Implementierung** von `IKiVorschlagService` (z. B. via Moq oder einer einfachen Fake-Klasse), damit die Tests unabhängig von der gewählten Variante A/B und ohne externe Abhängigkeit laufen.
- Erstellen Sie **automatisierte Integrationstests** (`WebApplicationFactory`) für mindestens drei Endpunkte end-to-end, davon mindestens ein Test, der einen nicht autorisierten Zugriff (`401`/`403`) nachweist.
- Prüfen Sie die Eingabevalidierung (z. B. leere Pflichtfelder, ungültige Kategorie/Priorität, negative IDs) mit Data Annotations oder FluentValidation und testen Sie mindestens 3 Negativfälle.
- Führen Sie eine Selbstüberprüfung gegen die funktionalen, nicht-funktionalen und Sicherheitsanforderungen (Abschnitte 7–9) durch und halten Sie in einem Änderungsprotokoll (Tabelle mit Datum/Befund/Korrektur) fest, was Sie dabei korrigiert haben.

### 6.4 Handlungsziel 4 – Coderichtlinien einhalten *(ca. 1.5 Std.)*

- Aktivieren Sie eine `.editorconfig`-Datei mit den Microsoft C#-Coding-Conventions (Namensgebung PascalCase/camelCase, Klammernstil, `var`-Verwendung usw.) für Web-API- und Testprojekt.
- Aktivieren Sie die integrierten .NET-Analyzer bzw. binden Sie zusätzlich `StyleCop.Analyzers` ein, sodass Verstösse laufend im Editor angezeigt werden.
- Beheben Sie alle Warnungen/Regelverstösse; dokumentieren Sie kurz, welche Regeln Sie angewendet haben und wie Sie Verstösse korrigiert haben (Vorher/Nachher-Beispiel genügt).

### 6.5 Handlungsziel 5 – Versionsverwaltung *(laufend, ca. 0.5 Std. initialer Aufwand)*

- Initialisieren Sie zu Projektbeginn ein Git-Repository (inkl. passender `.gitignore` für Visual-Studio-/.NET-Projekte – **insbesondere so, dass keine API-Keys/Secrets versehentlich committet werden**).
- Committen Sie **regelmässig** in nachvollziehbaren, thematisch sinnvollen Schritten (nicht ein einziger Commit am Schluss) mit aussagekräftigen Commit-Messages.
- Die Commit-Historie muss den Entwicklungsverlauf über alle Handlungsziele hinweg sichtbar machen (Setup, CRUD Tickets, CRUD/Geschäftsregel Antworten, KI-Anbindung, Tests, Coderichtlinien, Authentifizierung/Autorisierung).
- Abgabe inkl. `.git`-Ordner oder als Link auf ein Remote-Repository.

### 6.6 Handlungsziel 6 – Authentifizierung implementieren *(ca. 3.5 Std.)*

- Implementieren Sie einen `POST /api/auth/login`-Endpunkt, der Benutzername/Passwort entgegennimmt (fest hinterlegte oder in `appsettings.json` konfigurierte Testbenutzer je Rolle genügen) und bei Erfolg ein **JWT mit Rollen-Claim** («Support-Mitarbeiter» oder «Teamleitung») zurückgibt.
- Konfigurieren Sie JWT-Bearer-Authentication (Issuer, Audience, Signaturschlüssel) in `Program.cs`.
- Setzen Sie folgende Zugriffsrechte um:
  - **Lesende Endpunkte** (`GET` auf `/api/tickets` und `/api/tickets/{id}/antworten`): erfordern eine gültige Authentifizierung (beliebige Rolle).
  - **Ticket erfassen/aktualisieren, Antwort erfassen, KI-Vorschlag anfordern** (`POST`/`PUT` auf `/api/tickets`, `POST` auf `/api/tickets/{id}/antworten` und `/ki-vorschlag`): mit beiden Rollen möglich (`[Authorize]`).
  - **Ticket löschen, Antwort löschen** (`DELETE`-Endpunkte): nur mit Rolle **Teamleitung** (`[Authorize(Roles = "Teamleitung")]`).
- Weisen Sie in der Dokumentation und mit Screenshots nach: Zugriff ohne Token wird mit `401 Unauthorized` abgelehnt, Zugriff mit Token der Rolle «Support-Mitarbeiter» auf einen teamleitungs-geschützten Endpunkt wird mit `403 Forbidden` abgelehnt, und der Zugriff mit passender Rolle funktioniert.

### 6.7 Abschlusspräsentation mit Live-Demo *(15–20 Min., ca. 1 Std. Vorbereitung)*

Zum Abschluss präsentieren Sie Ihr Projekt vor der Klasse bzw. der Lehrperson. Die Präsentation ist Teil der Bewertung (siehe Abschnitt 11.2) und zeigt, dass Sie Ihre Lösung nicht nur umgesetzt, sondern auch verstanden und begründet haben.

**Dauer:** 15–20 Minuten, gefolgt von einer kurzen Fragerunde (ca. 5 Min.).

**Empfohlener Ablauf:**

| Teil | Inhalt                                                                                                                                                                                                 | Richtzeit    |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ |
| 1    | Ausgangslage und Auftrag kurz einordnen (NordTech Support AG, Ziel der API, Rollenkonzept)                                                                                                             | ca. 2 Min.   |
| 2    | Architektur- und Datenmodellüberblick (Schichten inkl. Service-Layer, Beziehung Ticket–Antwort, KI-Abstraktion `IKiVorschlagService`, gewählte Variante A/B und Begründung)                            | ca. 3–4 Min. |
| 3    | **Live-Demo CRUD & Geschäftsregel:** Ticket- und Antwort-Endpunkte über Swagger UI oder Postman live vorführen, inkl. abgelehnter Antwort bei bereits geschlossenem Ticket (`409`)                     | ca. 4–5 Min. |
| 4    | **Live-Demo KI-Vorschlag:** für ein offenes Ticket einen KI-Vorschlag generieren lassen und das Ergebnis zeigen                                                                                        | ca. 2–3 Min. |
| 5    | **Live-Demo Authentifizierung/Autorisierung:** Login als Support-Mitarbeiter und als Teamleitung, Zugriff ohne Token (`401`), Zugriff mit falscher Rolle (`403`), Zugriff mit passender Rolle (Erfolg) | ca. 3–4 Min. |
| 6    | Kurzer Einblick in die automatisierten Tests (inkl. Test der KI-Komponente über Test-Doppelgänger) sowie Rückblick auf Herausforderungen                                                               | ca. 2 Min.   |
| 7    | Fragen der Lehrperson/Klasse                                                                                                                                                                           | ca. 5 Min.   |

**Anforderungen an die Demo:**

- Die Anwendung muss zum Präsentationstermin lokal lauffähig sein (kein reines Zeigen von Folien/Code-Ausschnitten anstelle einer echten Ausführung).
- Bei Wahl der echten LLM-API (Variante A) ist sicherzustellen, dass am Präsentationstermin eine funktionierende Internetverbindung sowie ein gültiger API-Key vorhanden sind; alternativ ist ein Fallback (z. B. kurzes Video/Screenshot als Backup) vorzubereiten, falls der Dienst zum Zeitpunkt der Präsentation nicht erreichbar sein sollte.
- Es wird empfohlen, die Demo-Umgebung (Visual Studio, gestartete API, Swagger UI/Postman, ggf. DB-Browser, Testlauf) vor der Präsentation vorzubereiten und einmal durchzuspielen.
- Folien sind optional und dürfen schlank gehalten werden (z. B. 3–5 Folien für Ausgangslage/Architektur); der Schwerpunkt liegt auf der Live-Demo.
- Rückfragen zu Design-Entscheidungen (z. B. „Warum diese KI-Abstraktion?", „Wie wird die Geschäftsregel konsistent durchgesetzt?", „Wie funktioniert die Rollenprüfung?") müssen aus dem Stand plausibel beantwortet werden können.

---

## 7. Funktionale Anforderungen

- Alle CRUD-Operationen auf den Ressourcen `Tickets` und `TicketAntworten` sind vollständig und korrekt implementiert.
- Der KI-Vorschlags-Endpunkt liefert für ein offenes Ticket einen plausiblen, auf Kategorie und Beschreibung bezogenen Antworttext und speichert ihn korrekt als Antwort.
- Die Geschäftsregel «keine neuen Antworten/KI-Vorschläge zu geschlossenen Tickets» ist zuverlässig durchgesetzt.
- Die API liefert und akzeptiert Daten im JSON-Format.
- `GET /api/tickets` unterstützt Paginierung, mindestens eine Filterdimension und Sortierung.
- Nicht vorhandene Ressourcen liefern `404 Not Found`, ungültige Anfragen `400 Bad Request`, Geschäftsregel-Verstösse `409 Conflict`.

## 8. Nicht-funktionale Anforderungen

- Klare Schichtentrennung (Controller / Service-Layer / KI-Abstraktion / Datenzugriff / Modelle).
- Nachvollziehbare, konsistente Namensgebung gemäss Coderichtlinien.
- Zentrale Exception-Handling-Middleware mit konsistenten `ProblemDetails`-Antworten (inkl. sinnvollem Verhalten, falls die KI-Komponente einen Fehler liefert).
- Aussagekräftiges, strukturiertes Logging zentraler Geschäftsvorgänge und Fehlerfälle.
- API-Dokumentation ist über Swagger UI aufrufbar und aktuell.
- Automatisierte Tests sind über den Standard-Testrunner (z. B. `dotnet test`) ausführbar, laufen fehlerfrei durch und sind unabhängig von einer echten externen KI-Anbindung lauffähig.

## 9. Sicherheitsanforderungen

- Sämtliche Endpunkte erfordern eine gültige Authentifizierung; administrative Operationen (Ticket/Antwort löschen) sind zusätzlich auf die Rolle «Teamleitung» beschränkt.
- Eingabedaten werden serverseitig validiert (keine ungeprüfte Übernahme von Client-Daten).
- Zugriffe auf die Datenbank erfolgen ausschliesslich parametrisiert über EF Core (kein manuelles String-Concatenation-SQL), um SQL-Injection auszuschliessen.
- Es werden keine Passwörter oder Secrets im Klartext im Repository abgelegt (z. B. Nutzung von `dotnet user-secrets` für den JWT-Signaturschlüssel sowie einen allfälligen LLM-API-Key in der Entwicklung).
- Bei Verwendung einer echten LLM-API werden vor dem Versand an den externen Dienst keine offensichtlich sensiblen Personendaten (über die für die Aufgabe notwendige Ticketbeschreibung hinaus) mitgeschickt; dies ist kurz in der Dokumentation zu reflektieren.

---

## 10. Abzugebende Ergebnisse

1. **Quellcode** der Visual-Studio-Solution (Web-API- und Testprojekt) inkl. `.git`-Verlauf (als ZIP mit `.git`-Ordner oder als Link auf ein Remote-Repository)
2. **Technische Dokumentation** (Markdown oder Word), enthält mindestens:
   - Architekturüberblick und Setup-/Startanleitung (README, inkl. Ausführen der Tests)
   - Datenmodell inkl. Beziehung Ticket–Antwort und Beschreibung der Geschäftsregel
   - Beschreibung der Endpunkte sowie des Rollen-/Autorisierungskonzepts
   - Beschreibung der gewählten KI-Variante (A – echte LLM-API oder B – simuliert) inkl. Begründung der Wahl
   - Änderungsprotokoll aus Handlungsziel 3
   - Kurzreflexion: Was war herausfordernd, was würden Sie beim nächsten Mal anders machen?
3. **Testnachweise**: Screenshots aus Swagger UI/Postman zu allen Endpunkten inkl. Geschäftsregel-Konfliktfall, KI-Vorschlag und Autorisierungsfällen (`401`/`403`), sowie ein Screenshot/Log des erfolgreichen automatisierten Testlaufs
4. **Coderichtlinien-Nachweis**: kurze Notiz/Screenshot zu verwendeten Analyzer-Regeln und einem behobenen Verstoss
5. **Abschlusspräsentation** (15–20 Min.) mit Live-Demo gemäss Abschnitt 6.7; Folien (falls verwendet) sind zusätzlich einzureichen

---

## 11. Bewertung

Die Gesamtnote setzt sich aus zwei Teilnoten zusammen: der **Projektarbeit** (Gewicht 80 %) und der **Abschlusspräsentation** (Gewicht 20 %).

### 11.1 Teilnote Projektarbeit (100 Punkte, Gewicht 80 %)

| Nr. | Kriterium                                                                                                                                | Handlungsziel | Punkte  |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ------- |
| 1   | Entwicklungsumgebung und Solution (inkl. Testprojekt) korrekt eingerichtet, lauffähig, dokumentiert                                      | HZ1           | 5       |
| 2   | CRUD-Endpunkte `Tickets` vollständig und korrekt implementiert                                                                           | HZ2           | 8       |
| 3   | CRUD `TicketAntworten` inkl. Geschäftsregel (kein Antworten/KI-Vorschlag bei geschlossenem Ticket, Auto-Timestamp) korrekt implementiert | HZ2           | 10      |
| 4   | Saubere Architektur: Service-Layer, `IKiVorschlagService`-Abstraktion mit DI, Controller, DTOs                                           | HZ2           | 8       |
| 5   | Paginierung, Filterung und Sortierung korrekt implementiert                                                                              | HZ2           | 5       |
| 6   | API über OpenAPI/Swagger vollständig dokumentiert, ergänzende technische Dokumentation inkl. KI-Konzept vorhanden und verständlich       | HZ2           | 7       |
| 7   | Manuelle Tests aller Endpunkte inkl. Negativ- und Konfliktfällen nachvollziehbar dokumentiert (Screenshots)                              | HZ3           | 5       |
| 8   | Automatisierte Unit-Tests der Geschäftslogik inkl. KI-Service über Test-Doppelgänger vorhanden, sinnvoll und lauffähig                   | HZ3           | 6       |
| 9   | Automatisierte Integrationstests (mind. 3 Endpunkte inkl. Autorisierungsfall) vorhanden, sinnvoll und lauffähig                          | HZ3           | 6       |
| 10  | Änderungsprotokoll/Anforderungsabgleich dokumentiert                                                                                     | HZ3           | 3       |
| 11  | Coderichtlinien (.editorconfig/Analyzer) eingerichtet und eingehalten, Nachweis Regelkorrektur                                           | HZ4           | 8       |
| 12  | Git-Repository mit regelmässiger, nachvollziehbarer Commit-Historie über den ganzen Entwicklungsverlauf, keine Secrets committet         | HZ5           | 8       |
| 13  | JWT-Login mit Rollen-Claim («Support-Mitarbeiter»/«Teamleitung») korrekt implementiert                                                   | HZ6           | 6       |
| 14  | Rollenbasierte Autorisierung korrekt auf allen Endpunkten angewendet, `401`/`403`-Nachweis vorhanden                                     | HZ6           | 10      |
| 15  | Gesamteindruck: Codequalität, Struktur, Konsistenz und Vollständigkeit der Abgabe                                                        | –             | 5       |
|     | **Total**                                                                                                                                |               | **100** |

$$\text{Note}_{\text{Projekt}} = 1 + \frac{\text{erreichte Punkte}}{100} \times 5$$

### 11.2 Teilnote Abschlusspräsentation (20 Punkte, Gewicht 20 %)

| Nr. | Kriterium                                                                                                                           | Punkte |
| --- | ----------------------------------------------------------------------------------------------------------------------------------- | ------ |
| 1   | Inhaltliche Struktur und Verständlichkeit (Ausgangslage, Architektur, gewählte KI-Variante, Ergebnisse klar dargestellt)            | 5      |
| 2   | Live-Demo funktioniert einwandfrei und deckt Geschäftsregel, KI-Vorschlag sowie rollenbasierte Autorisierung (inkl. `401`/`403`) ab | 8      |
| 3   | Fachliche Tiefe: kann eigene Design-Entscheidungen (insbesondere zur KI-Abstraktion) begründen und Rückfragen kompetent beantworten | 4      |
| 4   | Zeitmanagement und Präsentationstechnik (Zeitrahmen 15–20 Min. eingehalten, klar und strukturiert vorgetragen)                      | 3      |
|     | **Total**                                                                                                                           | **20** |

$$\text{Note}_{\text{Präsentation}} = 1 + \frac{\text{erreichte Punkte}}{20} \times 5$$

### 11.3 Gesamtnote

$$\text{Gesamtnote} = 0{,}8 \times \text{Note}_{\text{Projekt}} + 0{,}2 \times \text{Note}_{\text{Präsentation}}$$

Die Gesamtnote wird auf 0.1 Notenpunkte gerundet (Schweizer Notenskala 1–6). Als bestanden gilt eine Gesamtnote ≥ 4.0.

---

## 12. Hinweise

- Der Fokus des Moduls liegt auf der **Backend-Schnittstelle**; ein eigenes Frontend ist nicht Teil dieses Auftrags und wird nicht bewertet.
- Der erhöhte Umfang (zweite Ressource mit Geschäftsregel, KI-Abstraktion, Rollenkonzept, automatisierte Tests) trägt dem Umstand Rechnung, dass die Studierenden ihre übrigen Ausbildungsmodule bereits abgeschlossen haben und entsprechend mehr Vorwissen (z. B. OOP, Testtechniken) mitbringen.
- Es wird **keine** der beiden KI-Varianten (echte API vs. simuliert) bevorzugt bewertet – entscheidend ist eine saubere Abstraktion, nachvollziehbare Implementierung und Begründung der Wahl. Wer sich für Variante A entscheidet, trägt selbst die Verantwortung für Verfügbarkeit und Kosten des gewählten Anbieters während der Entwicklung und Präsentation.
- Eine einfache, direkte Umsetzung ohne zusätzliche, hier nicht geforderte Architekturmuster (z. B. kein separates Repository-Pattern zusätzlich zum Service-Layer) ist ausreichend und wird nicht negativ bewertet – wichtiger sind Korrektheit, Nachvollziehbarkeit und Sicherheit.
- Die Abschlusspräsentation findet am Präsentationstermin statt; die Anwendung muss zu diesem Zeitpunkt live vorführbar sein (siehe Abschnitt 6.7).
- Bei Unklarheiten zur Aufgabenstellung ist Rücksprache mit der Lehrperson zu halten.
