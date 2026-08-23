|               |                                           |                                        |
| ------------- | ----------------------------------------- | -------------------------------------- |
| **Modul 295** | **Backend für Applikationen realisieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

# **Projekt «ToolTrack API» – Digitale Werkzeugverwaltung mit Ausleihprozess für einen Handwerksbetrieb**

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

Da die Studierenden dieses Modul nachholen und die übrigen Module ihrer Ausbildung bereits erfolgreich abgeschlossen haben, ist dieser Projektauftrag anspruchsvoller ausgelegt als die reguläre Basisvariante: Neben der reinen CRUD-Schnittstelle sind ein zweiter, verknüpfter Datenbestand mit Geschäftsregel, eine rollenbasierte Autorisierung sowie automatisierte Tests (Unit- und Integrationstests) gefordert. Dieser Projektauftrag deckt weiterhin alle sechs Handlungsziele des Moduls 295 sowie die zugehörigen handlungsnotwendigen Kenntnisse gemäss Modulidentifikation (modulbaukasten.ch) vollständig ab; die Zuordnung ist in Abschnitt 6 und im Bewertungsraster (Abschnitt 11) ersichtlich. Der Auftrag schliesst mit einer bewerteten Abschlusspräsentation inkl. Live-Demo ab (Abschnitt 6.7).

---

## 2. Ausgangslage

Der fiktive Handwerksbetrieb **Stäubli Bau & Haustechnik AG** verwaltet seine Werkzeuge und Maschinen bisher in einer Excel-Liste. Das führt regelmässig zu Problemen: Niemand weiss genau, wo sich ein Werkzeug befindet, ob es verfügbar ist, oder wer es aktuell ausgeliehen hat. Die Geschäftsleitung hat entschieden, eine erste digitale Lösung einzuführen – zunächst als reine **Backend-Schnittstelle (API)**, die später von einer Web- oder Mobile-Anwendung genutzt werden kann.

Neben der reinen Werkzeugverwaltung soll die Lösung neu auch den **Ausleihprozess** abbilden: Mitarbeitende sollen ein Werkzeug als ausgeliehen erfassen und später wieder als zurückgegeben verbuchen können. Ein Werkzeug, das bereits ausgeliehen ist, darf nicht ein zweites Mal ausgeliehen werden. Zusätzlich soll zwischen zwei Arten von Benutzenden unterschieden werden: **Mitarbeitende** dürfen Ausleihen erfassen und zurückbuchen, aber keine Werkzeuge im Stammdatenbestand anlegen, ändern oder löschen. Das ist der **Administration** vorbehalten.

Die IT-Abteilung hat bereits eine kleine SQLite-Datenbank mit den Tabellen `Werkzeuge` und `Ausleihen` sowie Testdaten bereitgestellt (siehe Abschnitt 5). Ihre Aufgabe ist es, darauf aufbauend eine vollständige, dokumentierte, getestete und abgesicherte Back-End-Schnittstelle zu realisieren.

---

## 3. Auftrag

Realisieren Sie als Einzelarbeit mit **Visual Studio und C#** eine **ASP.NET Core Web API**, die

- den lesenden und schreibenden Zugriff (CRUD) auf die vorgegebenen Datenquellen `Werkzeuge` und `Ausleihen` ermöglicht und dabei die Geschäftsregel «ein bereits ausgeliehenes Werkzeug kann nicht erneut ausgeliehen werden» durchsetzt,
- aktuelle Schnittstellen-Standards einhält und vollständig dokumentiert ist (OpenAPI/Swagger),
- mit automatisierten Tests (Unit- und Integrationstests) sowie manuellen Tests gegen die Anforderungen abgeglichen wird,
- definierte Coderichtlinien erfüllt,
- in einem Softwareverwaltungssystem nachvollziehbar versioniert wird, und
- über einen rollenbasierten Authentifizierungsmechanismus (Rollen «Admin» und «Mitarbeiter») verfügt, der die Zugriffsrechte entsprechend der Ausgangslage differenziert.

---

## 4. Rahmenbedingungen

- **Zielgruppe:** Modul-Nachholende mit bereits abgeschlossenen übrigen Ausbildungsmodulen (entsprechend anspruchsvollerer Umfang)
- **Sozialform:** Einzelarbeit
- **Zeitrahmen:** ca. 20–25 Stunden Umsetzung (siehe Zeitbudget je Handlungsziel in Abschnitt 6) plus ca. 1 Stunde Vorbereitung der Abschlusspräsentation
- **Entwicklungsumgebung:** Visual Studio 2022 oder neuer, aktuelle LTS-Version von .NET (z. B. .NET 8 oder .NET 10)
- **Datenzugriff:** Entity Framework Core mit SQLite-Provider
- **Schnittstellen-Standard:** RESTful API mit JSON, dokumentiert über OpenAPI/Swagger
- **Testframework:** xUnit für automatisierte Unit- und Integrationstests (`WebApplicationFactory`)
- **Authentifizierung/Autorisierung:** JWT (JSON Web Token) mit Rollen-Claims («Admin», «Mitarbeiter»)
- **Versionsverwaltung:** Git (lokal oder auf GitHub/GitLab/Azure DevOps)
- **Vorgegebene Datenquelle:** SQLite-Datenbank `tooltrack.db` mit den Tabellen `Werkzeuge` und `Ausleihen`, Schema und Seed-Daten gemäss Abschnitt 5
- **Abschlusspräsentation:** 15–20 Minuten pro Person, inkl. Live-Demo der lauffähigen Anwendung, wird bewertet (siehe Abschnitt 6.7 und 11.2)
- **Zulässige Hilfsmittel:** Fachliteratur, offizielle Microsoft-Dokumentation, Unterrichtsunterlagen. KI-Tools dürfen unterstützend zum Verständnis eingesetzt werden; der Code muss jedoch selbstständig nachvollzogen und im Rahmen einer allfälligen Rückfrage erklärt werden können.

---

## 5. Vorgegebene Datenquelle

Die folgende Datenquelle gilt als **gegeben** und ist Ausgangspunkt Ihrer Implementierung (Handlungsziel 2). Führen Sie das Skript in einer neuen SQLite-Datenbank `tooltrack.db` aus, bevor Sie mit der Implementierung beginnen.

```sql
CREATE TABLE Werkzeuge (
    Id              INTEGER PRIMARY KEY AUTOINCREMENT,
    Bezeichnung     TEXT    NOT NULL,
    Kategorie       TEXT    NOT NULL,
    Standort        TEXT    NOT NULL,
    Zustand         TEXT    NOT NULL,      -- z.B. "Neuwertig", "Gebraucht", "Reparaturbedürftig"
    Verfuegbar      INTEGER NOT NULL,      -- 0 = nein, 1 = ja
    Anschaffungsdatum TEXT  NOT NULL       -- Format: YYYY-MM-DD
);

INSERT INTO Werkzeuge (Bezeichnung, Kategorie, Standort, Zustand, Verfuegbar, Anschaffungsdatum) VALUES
('Bosch Bohrhammer GBH 5-40', 'Elektrowerkzeug', 'Lager Nord', 'Neuwertig', 1, '2024-03-12'),
('Hilti Schlagbohrmaschine TE 6', 'Elektrowerkzeug', 'Baustelle Zürich', 'Gebraucht', 0, '2022-08-01'),
('Stihl Trennschleifer TS 420', 'Motorgerät', 'Lager Süd', 'Reparaturbedürftig', 0, '2021-05-19'),
('Werkzeugkoffer Sanitär', 'Handwerkzeug', 'Lager Nord', 'Gebraucht', 1, '2020-11-02'),
('Nivelliergerät Leica Rugby 610', 'Messgerät', 'Baustelle Bern', 'Neuwertig', 1, '2025-01-15');

CREATE TABLE Ausleihen (
    Id              INTEGER PRIMARY KEY AUTOINCREMENT,
    WerkzeugId      INTEGER NOT NULL,
    MitarbeiterName TEXT    NOT NULL,
    Ausleihdatum    TEXT    NOT NULL,      -- Format: YYYY-MM-DD
    Rueckgabedatum  TEXT    NULL,          -- NULL = noch nicht zurückgegeben
    FOREIGN KEY (WerkzeugId) REFERENCES Werkzeuge (Id)
);

INSERT INTO Ausleihen (WerkzeugId, MitarbeiterName, Ausleihdatum, Rueckgabedatum) VALUES
(2, 'Marco Rossi', '2026-06-01', NULL),
(3, 'Fatima Yilmaz', '2026-05-10', NULL),
(4, 'Peter Studer', '2026-04-02', '2026-04-20');
```

> Hinweis: Die Studierenden erstellen darauf aufbauend ihre C#-Datenmodelle (`Werkzeug`, `Ausleihe`) inkl. Navigationseigenschaft sowie den `DbContext` passend zu diesem bestehenden Schema. Beachten Sie, dass die Werkzeuge mit Id 2 und 3 gemäss Seed-Daten bereits ausgeliehen sind (`Verfuegbar = 0`, passende offene Ausleihe ohne Rückgabedatum) – dieser konsistente Zustand ist beim Implementieren der Geschäftsregel zu berücksichtigen.

---

## 6. Aufgabenstellung im Detail

### 6.1 Handlungsziel 1 – Entwicklungsumgebung einrichten *(ca. 1.5 Std.)*

- Installieren/prüfen Sie die benötigten Komponenten: Visual Studio mit ASP.NET-Workload, aktuelle .NET-SDK-Version, EF Core Tools, ggf. DB-Browser für SQLite.
- Erstellen Sie eine Visual-Studio-Solution mit zwei Projekten: dem Web-API-Projekt sowie einem xUnit-Testprojekt.
- Legen Sie die Projektstruktur im API-Projekt an (z. B. Ordner `Models`, `Data`, `DTOs`, `Services`, `Controllers`, `Middleware`).
- Binden Sie die vorgegebene SQLite-Datenbank (`tooltrack.db`) über eine Connection-String-Konfiguration in `appsettings.json` ein.
- Dokumentieren Sie kurz (in der README), welche Komponenten installiert wurden, wie die Solution aufgebaut ist und wie Projekt sowie Tests lokal zum Laufen gebracht werden.

### 6.2 Handlungsziel 2 – Backend-Schnittstelle implementieren und dokumentieren *(ca. 9 Std.)*

Implementieren Sie eine strukturierte REST-API für **zwei zusammenhängende Ressourcen**:

**Werkzeuge** (Stammdaten):

| Methode | Route                 | Zweck                                                                          |
| ------- | --------------------- | ------------------------------------------------------------------------------ |
| GET     | `/api/werkzeuge`      | Liste aller Werkzeuge, mit Paginierung, Filterung und Sortierung (siehe unten) |
| GET     | `/api/werkzeuge/{id}` | Einzelnes Werkzeug abrufen                                                     |
| POST    | `/api/werkzeuge`      | Neues Werkzeug erfassen                                                        |
| PUT     | `/api/werkzeuge/{id}` | Werkzeug aktualisieren                                                         |
| DELETE  | `/api/werkzeuge/{id}` | Werkzeug löschen                                                               |

**Ausleihen** (Bewegungsdaten, referenziert ein Werkzeug):

| Methode | Route                           | Zweck                                                                                 |
| ------- | ------------------------------- | ------------------------------------------------------------------------------------- |
| GET     | `/api/ausleihen`                | Liste aller Ausleihen, mit Filter (z. B. `?aktiv=true` für noch nicht zurückgegebene) |
| GET     | `/api/ausleihen/{id}`           | Einzelne Ausleihe abrufen                                                             |
| POST    | `/api/ausleihen`                | Ausleihe erfassen (Werkzeug muss aktuell verfügbar sein)                              |
| PUT     | `/api/ausleihen/{id}/rueckgabe` | Rückgabe verbuchen (setzt Rückgabedatum, setzt Werkzeug wieder auf verfügbar)         |
| DELETE  | `/api/ausleihen/{id}`           | Ausleihe-Eintrag löschen (z. B. Korrektur einer Fehlerfassung)                        |

Anforderungen an die Umsetzung:

- **Geschäftsregel:** Beim Erfassen einer Ausleihe (`POST /api/ausleihen`) muss geprüft werden, ob das referenzierte Werkzeug aktuell verfügbar ist. Ist es das nicht, liefert die API `409 Conflict` mit einer verständlichen Fehlermeldung. Bei erfolgreicher Ausleihe wird `Werkzeuge.Verfuegbar` konsistent auf `false` gesetzt; bei der Rückgabe entsprechend zurück auf `true`.
- **Service-Layer:** Die Geschäftslogik (insbesondere die Verfügbarkeitsprüfung und die konsistente Aktualisierung beider Tabellen) ist in einer eigenen Service-Schicht gekapselt, nicht direkt im Controller.
- Sauber getrennte Schichten: Controller, Service-Layer, Datenzugriff (EF Core `DbContext`), Datenmodell/DTOs. Verwendung von DTOs für Ein-/Ausgabe (kein direktes Durchreichen des Entity-Modells nach aussen).
- **Paginierung, Filterung, Sortierung:** `GET /api/werkzeuge` unterstützt mindestens `page`, `pageSize`, eine Filterung (z. B. nach `verfuegbar` und/oder `kategorie`) sowie eine Sortierung (z. B. `sortBy=Bezeichnung&sortDirection=asc`).
- Aussagekräftige HTTP-Statuscodes (200, 201, 204, 400, 404, 409 usw.) und konsistente Fehlerantworten über eine zentrale Exception-Handling-Middleware (`ProblemDetails`).
- Strukturiertes Logging (`ILogger`) für zentrale Vorgänge (Ausleihe erfasst, Rückgabe verbucht, abgelehnte Ausleihe, Fehlerfälle).
- Dokumentation der Schnittstelle über **OpenAPI/Swagger** (z. B. Swashbuckle), inkl. Beispielwerten und Beschreibung sämtlicher Endpunkte beider Ressourcen.
- Ergänzende schriftliche Dokumentation (Markdown oder Word): Architekturüberblick, Datenmodell inkl. Beziehung Werkzeug–Ausleihe, Beschreibung der Endpunkte und der Geschäftsregel, eingesetzte Technologien.

### 6.3 Handlungsziel 3 – Anforderungen überprüfen, Korrekturen vornehmen *(ca. 4.5 Std.)*

- Testen Sie jeden Endpunkt manuell über Swagger UI oder Postman/Insomnia; dokumentieren Sie die Tests mit Screenshots (Request + Response), inkl. des Konfliktfalls «Werkzeug bereits ausgeliehen».
- Erstellen Sie **automatisierte Unit-Tests** (xUnit) für die zentrale Geschäftslogik im Service-Layer, u. a.: Ausleihe eines verfügbaren Werkzeugs gelingt, Ausleihe eines nicht verfügbaren Werkzeugs wird abgelehnt, Rückgabe setzt den Verfügbarkeitsstatus korrekt zurück.
- Erstellen Sie **automatisierte Integrationstests** (`WebApplicationFactory`) für mindestens drei Endpunkte end-to-end, davon mindestens ein Test, der einen nicht autorisierten Zugriff (`401`/`403`) nachweist.
- Prüfen Sie die Eingabevalidierung (z. B. leere Pflichtfelder, ungültiges Datum, negative IDs) mit Data Annotations oder FluentValidation und testen Sie mindestens 3 Negativfälle.
- Führen Sie eine Selbstüberprüfung gegen die funktionalen, nicht-funktionalen und Sicherheitsanforderungen (Abschnitte 7–9) durch und halten Sie in einem Änderungsprotokoll (Tabelle mit Datum/Befund/Korrektur) fest, was Sie dabei korrigiert haben.

### 6.4 Handlungsziel 4 – Coderichtlinien einhalten *(ca. 1.5 Std.)*

- Aktivieren Sie eine `.editorconfig`-Datei mit den Microsoft C#-Coding-Conventions (Namensgebung PascalCase/camelCase, Klammernstil, `var`-Verwendung usw.) für Web-API- und Testprojekt.
- Aktivieren Sie die integrierten .NET-Analyzer bzw. binden Sie zusätzlich `StyleCop.Analyzers` ein, sodass Verstösse laufend im Editor angezeigt werden.
- Beheben Sie alle Warnungen/Regelverstösse; dokumentieren Sie kurz, welche Regeln Sie angewendet haben und wie Sie Verstösse korrigiert haben (Vorher/Nachher-Beispiel genügt).

### 6.5 Handlungsziel 5 – Versionsverwaltung *(laufend, ca. 0.5 Std. initialer Aufwand)*

- Initialisieren Sie zu Projektbeginn ein Git-Repository (inkl. passender `.gitignore` für Visual-Studio-/.NET-Projekte).
- Committen Sie **regelmässig** in nachvollziehbaren, thematisch sinnvollen Schritten (nicht ein einziger Commit am Schluss) mit aussagekräftigen Commit-Messages.
- Die Commit-Historie muss den Entwicklungsverlauf über alle Handlungsziele hinweg sichtbar machen (Setup, CRUD Werkzeuge, CRUD/Geschäftsregel Ausleihen, Tests, Coderichtlinien, Authentifizierung/Autorisierung).
- Abgabe inkl. `.git`-Ordner oder als Link auf ein Remote-Repository.

### 6.6 Handlungsziel 6 – Authentifizierung implementieren *(ca. 3.5 Std.)*

- Implementieren Sie einen `POST /api/auth/login`-Endpunkt, der Benutzername/Passwort entgegennimmt (fest hinterlegte oder in `appsettings.json` konfigurierte Testbenutzer je Rolle genügen) und bei Erfolg ein **JWT mit Rollen-Claim** («Admin» oder «Mitarbeiter») zurückgibt.
- Konfigurieren Sie JWT-Bearer-Authentication (Issuer, Audience, Signaturschlüssel) in `Program.cs`.
- Setzen Sie folgende Zugriffsrechte um:
  - **Lesende Endpunkte** (`GET` auf `/api/werkzeuge` und `/api/ausleihen`): erfordern eine gültige Authentifizierung (beliebige Rolle).
  - **Werkzeug-Stammdaten verändern** (`POST`, `PUT`, `DELETE` auf `/api/werkzeuge`): nur mit Rolle **Admin** (`[Authorize(Roles = "Admin")]`).
  - **Ausleihe erfassen/zurückgeben** (`POST /api/ausleihen`, `PUT /api/ausleihen/{id}/rueckgabe`): mit beiden Rollen möglich (`[Authorize]`).
  - **Ausleihe löschen** (`DELETE /api/ausleihen/{id}`): nur mit Rolle **Admin**.
- Weisen Sie in der Dokumentation und mit Screenshots nach: Zugriff ohne Token wird mit `401 Unauthorized` abgelehnt, Zugriff mit Token der Rolle «Mitarbeiter» auf einen admin-geschützten Endpunkt wird mit `403 Forbidden` abgelehnt, und der Zugriff mit passender Rolle funktioniert.

### 6.7 Abschlusspräsentation mit Live-Demo *(15–20 Min., ca. 1 Std. Vorbereitung)*

Zum Abschluss präsentieren Sie Ihr Projekt vor der Klasse bzw. der Lehrperson. Die Präsentation ist Teil der Bewertung (siehe Abschnitt 11.2) und zeigt, dass Sie Ihre Lösung nicht nur umgesetzt, sondern auch verstanden und begründet haben.

**Dauer:** 15–20 Minuten, gefolgt von einer kurzen Fragerunde (ca. 5 Min.).

**Empfohlener Ablauf:**

| Teil | Inhalt                                                                                                                                                                                      | Richtzeit    |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| 1    | Ausgangslage und Auftrag kurz einordnen (Stäubli Bau & Haustechnik AG, Ziel der API, Rollenkonzept)                                                                                         | ca. 2 Min.   |
| 2    | Architektur- und Datenmodellüberblick (Schichten inkl. Service-Layer, Beziehung Werkzeug–Ausleihe, eingesetzte Technologien)                                                                | ca. 3 Min.   |
| 3    | **Live-Demo CRUD & Geschäftsregel:** Werkzeug- und Ausleihe-Endpunkte über Swagger UI oder Postman live vorführen, inkl. abgelehnter Ausleihe eines bereits ausgeliehenen Werkzeugs (`409`) | ca. 5–6 Min. |
| 4    | **Live-Demo Authentifizierung/Autorisierung:** Login als Mitarbeiter und als Admin, Zugriff ohne Token (`401`), Zugriff mit falscher Rolle (`403`), Zugriff mit passender Rolle (Erfolg)    | ca. 4–5 Min. |
| 5    | Kurzer Einblick in die automatisierten Tests (Unit- und Integrationstests, Testlauf zeigen) sowie Rückblick auf Herausforderungen                                                           | ca. 2–3 Min. |
| 6    | Fragen der Lehrperson/Klasse                                                                                                                                                                | ca. 5 Min.   |

**Anforderungen an die Demo:**

- Die Anwendung muss zum Präsentationstermin lokal lauffähig sein (kein reines Zeigen von Folien/Code-Ausschnitten anstelle einer echten Ausführung).
- Es wird empfohlen, die Demo-Umgebung (Visual Studio, gestartete API, Swagger UI/Postman, ggf. DB-Browser, Testlauf) vor der Präsentation vorzubereiten und einmal durchzuspielen.
- Folien sind optional und dürfen schlank gehalten werden (z. B. 3–5 Folien für Ausgangslage/Architektur); der Schwerpunkt liegt auf der Live-Demo.
- Rückfragen zu Design-Entscheidungen (z. B. „Warum ein Service-Layer?", „Wie wird die Geschäftsregel konsistent durchgesetzt?", „Wie funktioniert die Rollenprüfung?") müssen aus dem Stand plausibel beantwortet werden können.

---

## 7. Funktionale Anforderungen

- Alle CRUD-Operationen auf den Ressourcen `Werkzeuge` und `Ausleihen` sind vollständig und korrekt implementiert.
- Die Geschäftsregel «kein Werkzeug kann zweimal gleichzeitig ausgeliehen werden» ist zuverlässig durchgesetzt und über beide Tabellen hinweg konsistent.
- Die API liefert und akzeptiert Daten im JSON-Format.
- `GET /api/werkzeuge` unterstützt Paginierung, mindestens eine Filterdimension und Sortierung.
- Nicht vorhandene Ressourcen liefern `404 Not Found`, ungültige Anfragen `400 Bad Request`, Geschäftsregel-Verstösse `409 Conflict`.

## 8. Nicht-funktionale Anforderungen

- Klare Schichtentrennung (Controller / Service-Layer / Datenzugriff / Modelle).
- Nachvollziehbare, konsistente Namensgebung gemäss Coderichtlinien.
- Zentrale Exception-Handling-Middleware mit konsistenten `ProblemDetails`-Antworten.
- Aussagekräftiges, strukturiertes Logging zentraler Geschäftsvorgänge und Fehlerfälle.
- API-Dokumentation ist über Swagger UI aufrufbar und aktuell.
- Automatisierte Tests sind über den Standard-Testrunner (z. B. `dotnet test`) ausführbar und laufen fehlerfrei durch.

## 9. Sicherheitsanforderungen

- Sämtliche Endpunkte erfordern eine gültige Authentifizierung; administrative Operationen (Werkzeug-Stammdaten verändern/löschen, Ausleihe löschen) sind zusätzlich auf die Rolle «Admin» beschränkt.
- Eingabedaten werden serverseitig validiert (keine ungeprüfte Übernahme von Client-Daten).
- Zugriffe auf die Datenbank erfolgen ausschliesslich parametrisiert über EF Core (kein manuelles String-Concatenation-SQL), um SQL-Injection auszuschliessen.
- Es werden keine Passwörter oder Secrets im Klartext im Repository abgelegt (z. B. Nutzung von `dotnet user-secrets` für den JWT-Signaturschlüssel in der Entwicklung).

---

## 10. Abzugebende Ergebnisse

1. **Quellcode** der Visual-Studio-Solution (Web-API- und Testprojekt) inkl. `.git`-Verlauf (als ZIP mit `.git`-Ordner oder als Link auf ein Remote-Repository)
2. **Technische Dokumentation** (Markdown oder Word), enthält mindestens:
   - Architekturüberblick und Setup-/Startanleitung (README, inkl. Ausführen der Tests)
   - Datenmodell inkl. Beziehung Werkzeug–Ausleihe und Beschreibung der Geschäftsregel
   - Beschreibung der Endpunkte sowie des Rollen-/Autorisierungskonzepts
   - Änderungsprotokoll aus Handlungsziel 3
   - Kurzreflexion: Was war herausfordernd, was würden Sie beim nächsten Mal anders machen?
3. **Testnachweise**: Screenshots aus Swagger UI/Postman zu allen Endpunkten inkl. Geschäftsregel-Konfliktfall und Autorisierungsfällen (`401`/`403`), sowie ein Screenshot/Log des erfolgreichen automatisierten Testlaufs
4. **Coderichtlinien-Nachweis**: kurze Notiz/Screenshot zu verwendeten Analyzer-Regeln und einem behobenen Verstoss
5. **Abschlusspräsentation** (15–20 Min.) mit Live-Demo gemäss Abschnitt 6.7; Folien (falls verwendet) sind zusätzlich einzureichen

---

## 11. Bewertung

Die Gesamtnote setzt sich aus zwei Teilnoten zusammen: der **Projektarbeit** (Gewicht 80 %) und der **Abschlusspräsentation** (Gewicht 20 %).

### 11.1 Teilnote Projektarbeit (100 Punkte, Gewicht 80 %)

| Nr. | Kriterium                                                                                                                           | Handlungsziel | Punkte  |
| --- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------- | ------- |
| 1   | Entwicklungsumgebung und Solution (inkl. Testprojekt) korrekt eingerichtet, lauffähig, dokumentiert                                 | HZ1           | 5       |
| 2   | CRUD-Endpunkte `Werkzeuge` vollständig und korrekt implementiert                                                                    | HZ2           | 8       |
| 3   | CRUD/Statuswechsel `Ausleihen` inkl. Geschäftsregel (Verfügbarkeitsprüfung, konsistente Statusaktualisierung) korrekt implementiert | HZ2           | 10      |
| 4   | Saubere Architektur: Service-Layer, Controller, DTOs, Beziehung Werkzeug–Ausleihe sauber modelliert                                 | HZ2           | 8       |
| 5   | Paginierung, Filterung und Sortierung korrekt implementiert                                                                         | HZ2           | 5       |
| 6   | API über OpenAPI/Swagger vollständig dokumentiert, ergänzende technische Dokumentation vorhanden und verständlich                   | HZ2           | 7       |
| 7   | Manuelle Tests aller Endpunkte inkl. Negativ- und Konfliktfällen nachvollziehbar dokumentiert (Screenshots)                         | HZ3           | 5       |
| 8   | Automatisierte Unit-Tests der Geschäftslogik vorhanden, sinnvoll und lauffähig                                                      | HZ3           | 6       |
| 9   | Automatisierte Integrationstests (mind. 3 Endpunkte inkl. Autorisierungsfall) vorhanden, sinnvoll und lauffähig                     | HZ3           | 6       |
| 10  | Änderungsprotokoll/Anforderungsabgleich dokumentiert                                                                                | HZ3           | 3       |
| 11  | Coderichtlinien (.editorconfig/Analyzer) eingerichtet und eingehalten, Nachweis Regelkorrektur                                      | HZ4           | 8       |
| 12  | Git-Repository mit regelmässiger, nachvollziehbarer Commit-Historie über den ganzen Entwicklungsverlauf                             | HZ5           | 8       |
| 13  | JWT-Login mit Rollen-Claim («Admin»/«Mitarbeiter») korrekt implementiert                                                            | HZ6           | 6       |
| 14  | Rollenbasierte Autorisierung korrekt auf allen Endpunkten angewendet, `401`/`403`-Nachweis vorhanden                                | HZ6           | 10      |
| 15  | Gesamteindruck: Codequalität, Struktur, Konsistenz und Vollständigkeit der Abgabe                                                   | –             | 5       |
|     | **Total**                                                                                                                           |               | **100** |

$$\text{Note}_{\text{Projekt}} = 1 + \frac{\text{erreichte Punkte}}{100} \times 5$$

### 11.2 Teilnote Abschlusspräsentation (20 Punkte, Gewicht 20 %)

| Nr. | Kriterium                                                                                                             | Punkte |
| --- | --------------------------------------------------------------------------------------------------------------------- | ------ |
| 1   | Inhaltliche Struktur und Verständlichkeit (Ausgangslage, Architektur, Ergebnisse klar dargestellt)                    | 5      |
| 2   | Live-Demo funktioniert einwandfrei und deckt Geschäftsregel sowie rollenbasierte Autorisierung (inkl. `401`/`403`) ab | 8      |
| 3   | Fachliche Tiefe: kann eigene Design-Entscheidungen begründen und Rückfragen kompetent beantworten                     | 4      |
| 4   | Zeitmanagement und Präsentationstechnik (Zeitrahmen 15–20 Min. eingehalten, klar und strukturiert vorgetragen)        | 3      |
|     | **Total**                                                                                                             | **20** |

$$\text{Note}_{\text{Präsentation}} = 1 + \frac{\text{erreichte Punkte}}{20} \times 5$$

### 11.3 Gesamtnote

$$\text{Gesamtnote} = 0{,}8 \times \text{Note}_{\text{Projekt}} + 0{,}2 \times \text{Note}_{\text{Präsentation}}$$

Die Gesamtnote wird auf 0.1 Notenpunkte gerundet (Schweizer Notenskala 1–6). Als bestanden gilt eine Gesamtnote ≥ 4.0.

---

## 12. Termine

| Meilenstein                          | Termin          |
| ------------------------------------ | --------------- |
| Projektstart                         | _______________ |
| Zwischenstand (empfohlen nach HZ1–2) | _______________ |
| Abgabe (Quellcode + Dokumentation)   | _______________ |
| Abschlusspräsentation mit Live-Demo  | _______________ |

*(Termine durch die Lehrperson/den Bildungsanbieter zu ergänzen.)*

---

## 13. Hinweise

- Der Fokus des Moduls liegt auf der **Backend-Schnittstelle**; ein Frontend ist nicht Teil dieses Auftrags und wird nicht bewertet.
- Der erhöhte Umfang (zweite Ressource mit Geschäftsregel, Rollenkonzept, automatisierte Tests) trägt dem Umstand Rechnung, dass die Studierenden ihre übrigen Ausbildungsmodule bereits abgeschlossen haben und entsprechend mehr Vorwissen (z. B. OOP, Testtechniken) mitbringen.
- Eine einfache, direkte Umsetzung ohne zusätzliche, hier nicht geforderte Architekturmuster (z. B. kein separates Repository-Pattern zusätzlich zum Service-Layer) ist ausreichend und wird nicht negativ bewertet – wichtiger sind Korrektheit, Nachvollziehbarkeit und Sicherheit.
- Die Abschlusspräsentation findet am Präsentationstermin statt; die Anwendung muss zu diesem Zeitpunkt live vorführbar sein (siehe Abschnitt 6.7).
- Bei Unklarheiten zur Aufgabenstellung ist Rücksprache mit der Lehrperson zu halten.

---

## Anhang: Kompetenzmatrix Modul 295 (gemäss modulbaukasten.ch)

| HZ  | Handlungsziel                                                                                                                                                                                                            | Referenz        | Abdeckung im Projekt                   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------- | -------------------------------------- |
| 1   | Richtet die lokale Entwicklungs- und Laufzeitumgebung so ein, dass ein vorgegebenes Projekt entwickelt werden kann.                                                                                                      | g5.1            | Abschnitt 6.1                          |
| 2   | Implementiert und dokumentiert mittels vorgegebener Technologie eine effiziente und strukturierte Back-End-Schnittstelle zur Verwaltung (CRUD) einer existierenden Datenquelle; nutzt aktuelle Schnittstellen-Standards. | g5.2            | Abschnitt 6.2, Datenquelle Abschnitt 5 |
| 3   | Überprüft Zwischenergebnisse mit den Anforderungen (funktional, nicht-funktional, Sicherheit) und nimmt laufend Korrekturen vor.                                                                                         | g5.4, g6.3–g6.8 | Abschnitt 6.3, Anforderungen 7–9       |
| 4   | Hält vorgegebene Coderichtlinien ein und überprüft laufend deren Einhaltung.                                                                                                                                             | g5.5            | Abschnitt 6.4                          |
| 5   | Legt Änderungen und Erweiterungen der Implementierung übersichtlich und zuverlässig in einem Softwareverwaltungssystem ab.                                                                                               | g5.6            | Abschnitt 6.5                          |
| 6   | Implementiert im Back-End einen aktuellen Authentifizierungsmechanismus und schützt mindestens einen Bereich vor anonymen Zugriffen.                                                                                     | g3.2, g3.4      | Abschnitt 6.6                          |
