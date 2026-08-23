|               |                                           |                                        |
| ------------- | ----------------------------------------- | -------------------------------------- |
| **Modul 295** | **Backend für Applikationen realisieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

# **Projekt «ToolTrack API» – Digitale Werkzeugverwaltung für einen Handwerksbetrieb**

## 1. Übersicht

|                   |                                                                                                                                        |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Modul**         | 295 – Backend für Applikationen realisieren                                                                                            |
| **Kompetenz**     | Implementiert mittels vorgegebener Technologie eine Back-End-Schnittstelle, welche aktuelle Schnittstellen-Standards einhält.          |
| **Kompetenzfeld** | Web Engineering                                                                                                                        |
| **Sozialform**    | Einzelarbeit                                                                                                                           |
| **Zeitaufwand**   | ca. 10–12 Stunden Umsetzung + ca. 1 Stunde Vorbereitung der Abschlusspräsentation                                                      |
| **Technologie**   | Visual Studio 2022 (oder neuer), C#, ASP.NET Core Web API (aktuelle .NET-LTS-Version), Entity Framework Core, SQLite, Git              |
| **Abgabe**        | Quellcode (inkl. Git-Historie) + technische Dokumentation + Testnachweise + Abschlusspräsentation mit Live-Demo (15–20 Min., bewertet) |

Dieser Projektauftrag deckt alle sechs Handlungsziele des Moduls 295 sowie die zugehörigen handlungsnotwendigen Kenntnisse gemäss Modulidentifikation (modulbaukasten.ch) vollständig ab. Die Zuordnung ist in Abschnitt 6 und im Bewertungsraster (Abschnitt 11) ersichtlich. Ergänzend schliesst der Auftrag mit einer bewerteten Abschlusspräsentation inkl. Live-Demo ab (Abschnitt 6.7).

---

## 2. Ausgangslage

Der fiktive Handwerksbetrieb **Stäubli Bau & Haustechnik AG** verwaltet seine Werkzeuge und Maschinen bisher in einer Excel-Liste. Das führt regelmässig zu Problemen: Niemand weiss genau, wo sich ein Werkzeug befindet, ob es verfügbar ist oder ob es sich noch in Reparatur befindet. Die Geschäftsleitung hat entschieden, eine erste digitale Lösung einzuführen – zunächst als reine **Backend-Schnittstelle (API)**, die später von einer Web- oder Mobile-Anwendung genutzt werden kann.

Die IT-Abteilung hat bereits eine kleine SQLite-Datenbank mit einer Tabelle `Werkzeuge` sowie ein paar Testdaten bereitgestellt (siehe Abschnitt 5). Ihre Aufgabe ist es, darauf aufbauend eine vollständige, dokumentierte und abgesicherte Back-End-Schnittstelle zu realisieren.

---

## 3. Auftrag

Realisieren Sie als Einzelarbeit mit **Visual Studio und C#** eine **ASP.NET Core Web API**, die den lesenden und schreibenden Zugriff (CRUD) auf die vorgegebene Werkzeug-Datenquelle ermöglicht, aktuelle Schnittstellen-Standards einhält, dokumentiert ist, definierte Coderichtlinien erfüllt, in einem Softwareverwaltungssystem versioniert wird und mindestens einen Bereich vor anonymem Zugriff schützt.

---

## 4. Rahmenbedingungen

- **Sozialform:** Einzelarbeit
- **Zeitrahmen:** ca. 10–12 Stunden Umsetzung (siehe Zeitbudget je Handlungsziel in Abschnitt 6) plus ca. 1 Stunde Vorbereitung der Abschlusspräsentation
- **Abschlusspräsentation:** 15–20 Minuten pro Person, inkl. Live-Demo der lauffähigen Anwendung, wird bewertet (siehe Abschnitt 6.7 und 11.2)
- **Entwicklungsumgebung:** Visual Studio 2022 oder neuer, aktuelle LTS-Version von .NET (z. B. .NET 8 oder .NET 10)
- **Datenzugriff:** Entity Framework Core mit SQLite-Provider
- **Schnittstellen-Standard:** RESTful API mit JSON, dokumentiert über OpenAPI/Swagger
- **Authentifizierung:** JWT (JSON Web Token)
- **Versionsverwaltung:** Git (lokal oder auf GitHub/GitLab/Azure DevOps)
- **Vorgegebene Datenquelle:** SQLite-Datenbank `tooltrack.db`, Schema und Seed-Daten gemäss Abschnitt 5
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
```

> Hinweis: Die Studierenden erstellen darauf aufbauend ihr C#-Datenmodell (`Werkzeug`) sowie den `DbContext` passend zu diesem bestehenden Schema (Database-First-Gedanke, auch wenn technisch via EF Core Code-First-Mapping umgesetzt).

---

## 6. Aufgabenstellung im Detail

### 6.1 Handlungsziel 1 – Entwicklungsumgebung einrichten *(ca. 1 Std.)*

- Installieren/prüfen Sie die benötigten Komponenten: Visual Studio mit ASP.NET-Workload, aktuelle .NET-SDK-Version, EF Core Tools, ggf. DB-Browser für SQLite.
- Erstellen Sie ein neues ASP.NET Core Web-API-Projekt (leeres oder Minimal-API-Template) in Visual Studio.
- Legen Sie die Projektstruktur an (z. B. Ordner `Models`, `Data`, `Controllers`, `DTOs`, `Services`).
- Binden Sie die vorgegebene SQLite-Datenbank (`tooltrack.db`) über eine Connection-String-Konfiguration in `appsettings.json` ein.
- Dokumentieren Sie kurz (in der README), welche Komponenten installiert wurden und wie das Projekt lokal zum Laufen gebracht wird.

### 6.2 Handlungsziel 2 – Backend-Schnittstelle implementieren und dokumentieren *(ca. 4–5 Std.)*

Implementieren Sie eine strukturierte REST-API zur Verwaltung der Werkzeuge mit folgenden Endpunkten:

| Methode | Route                 | Zweck                                                                   |
| ------- | --------------------- | ----------------------------------------------------------------------- |
| GET     | `/api/werkzeuge`      | Liste aller Werkzeuge (mit optionalem Filter, z. B. `?verfuegbar=true`) |
| GET     | `/api/werkzeuge/{id}` | Einzelnes Werkzeug abrufen                                              |
| POST    | `/api/werkzeuge`      | Neues Werkzeug erfassen                                                 |
| PUT     | `/api/werkzeuge/{id}` | Werkzeug aktualisieren                                                  |
| DELETE  | `/api/werkzeuge/{id}` | Werkzeug löschen                                                        |

Anforderungen an die Umsetzung:

- Sauber getrennte Schichten: Controller, Datenzugriff (EF Core `DbContext`), Datenmodell/DTOs.
- Verwendung von DTOs für Ein-/Ausgabe (kein direktes Durchreichen des Entity-Modells nach aussen).
- Aussagekräftige HTTP-Statuscodes (200, 201, 204, 400, 404 usw.) und konsistente Fehlerantworten (z. B. `ProblemDetails`).
- Dokumentation der Schnittstelle über **OpenAPI/Swagger** (z. B. Swashbuckle), inkl. Beispielwerten und Beschreibung der Endpunkte.
- Ergänzende schriftliche Dokumentation (Markdown oder Word): Architekturüberblick, Datenmodell, Beschreibung der Endpunkte, eingesetzte Technologien.

### 6.3 Handlungsziel 3 – Anforderungen überprüfen, Korrekturen vornehmen *(ca. 1.5 Std.)*

- Testen Sie jeden Endpunkt manuell über Swagger UI oder Postman/Insomnia; dokumentieren Sie die Tests mit Screenshots (Request + Response).
- Prüfen Sie die Eingabevalidierung (z. B. leere Pflichtfelder, ungültiges Datum, negative IDs) mit Data Annotations oder FluentValidation und testen Sie mindestens 3 Negativfälle.
- Führen Sie eine kurze Selbstüberprüfung gegen die funktionalen, nicht-funktionalen und Sicherheitsanforderungen (Abschnitte 7–9) durch und halten Sie in der Dokumentation fest, was Sie dabei korrigiert haben (z. B. „Anfangs fehlte die Validierung des Datumsformats – ergänzt am ...").
- Ein einfaches Änderungsprotokoll (Tabelle mit Datum/Befund/Korrektur) genügt.

### 6.4 Handlungsziel 4 – Coderichtlinien einhalten *(ca. 1 Std.)*

- Aktivieren Sie eine `.editorconfig`-Datei mit den Microsoft C#-Coding-Conventions (Namensgebung PascalCase/camelCase, Klammernstil, `var`-Verwendung usw.).
- Aktivieren Sie die integrierten .NET-Analyzer bzw. binden Sie zusätzlich `StyleCop.Analyzers` ein, sodass Verstösse laufend im Editor angezeigt werden.
- Beheben Sie alle Warnungen/Regelverstösse; dokumentieren Sie kurz, welche Regeln Sie angewendet haben und wie Sie Verstösse korrigiert haben (Vorher/Nachher-Beispiel genügt).

### 6.5 Handlungsziel 5 – Versionsverwaltung *(laufend, ca. 0.5 Std. initialer Aufwand)*

- Initialisieren Sie zu Projektbeginn ein Git-Repository (inkl. passender `.gitignore` für Visual-Studio-/.NET-Projekte).
- Committen Sie **regelmässig** in nachvollziehbaren, thematisch sinnvollen Schritten (nicht ein einziger Commit am Schluss) mit aussagekräftigen Commit-Messages.
- Die Commit-Historie muss den Entwicklungsverlauf über alle Handlungsziele hinweg sichtbar machen (Setup, CRUD-Endpunkte, Validierung, Coderichtlinien, Authentifizierung).
- Abgabe inkl. `.git`-Ordner oder als Link auf ein Remote-Repository.

### 6.6 Handlungsziel 6 – Authentifizierung implementieren *(ca. 2–2.5 Std.)*

- Implementieren Sie einen `POST /api/auth/login`-Endpunkt, der Benutzername/Passwort entgegennimmt (fest hinterlegte oder in `appsettings.json` konfigurierte Testbenutzer genügen) und bei Erfolg ein **JWT** zurückgibt.
- Schützen Sie die schreibenden Endpunkte (`POST`, `PUT`, `DELETE` auf `/api/werkzeuge`) mit `[Authorize]`, sodass diese nur mit gültigem Token nutzbar sind. Die lesenden Endpunkte (`GET`) dürfen öffentlich bleiben.
- Konfigurieren Sie JWT-Bearer-Authentication (Issuer, Audience, Signaturschlüssel) in `Program.cs`.
- Weisen Sie in der Dokumentation und mit einem Screenshot nach, dass ein Zugriff ohne Token auf einen geschützten Endpunkt mit `401 Unauthorized` abgelehnt wird und mit gültigem Token funktioniert.

### 6.7 Abschlusspräsentation mit Live-Demo *(15–20 Min., ca. 1 Std. Vorbereitung)*

Zum Abschluss präsentieren Sie Ihr Projekt vor der Klasse bzw. der Lehrperson. Die Präsentation ist Teil der Bewertung (siehe Abschnitt 11.2) und zeigt, dass Sie Ihre Lösung nicht nur umgesetzt, sondern auch verstanden und begründet haben.

**Dauer:** 15–20 Minuten, gefolgt von einer kurzen Fragerunde (ca. 5 Min.).

**Empfohlener Ablauf:**

| Teil | Inhalt                                                                                                                                                               | Richtzeit    |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| 1    | Ausgangslage und Auftrag kurz einordnen (Stäubli Bau & Haustechnik AG, Ziel der API)                                                                                 | ca. 2 Min.   |
| 2    | Architektur- und Datenmodellüberblick (Schichten, `Werkzeug`-Entität, eingesetzte Technologien)                                                                      | ca. 3 Min.   |
| 3    | **Live-Demo CRUD:** alle fünf Endpunkte über Swagger UI oder Postman live vorführen (inkl. mind. 1 Negativfall, z. B. ungültige Eingabe)                             | ca. 5–6 Min. |
| 4    | **Live-Demo Authentifizierung:** Login-Endpunkt aufrufen, JWT anzeigen, Zugriff auf geschützten Endpunkt zuerst ohne Token (`401`), dann mit gültigem Token (Erfolg) | ca. 3–4 Min. |
| 5    | Kurzer Rückblick: Herausforderungen, Umgang mit Coderichtlinien/Tests, was beim nächsten Mal anders gemacht würde                                                    | ca. 2–3 Min. |
| 6    | Fragen der Lehrperson/Klasse                                                                                                                                         | ca. 5 Min.   |

**Anforderungen an die Demo:**

- Die Anwendung muss zum Präsentationstermin lokal lauffähig sein (kein reines Zeigen von Folien/Code-Ausschnitten anstelle einer echten Ausführung).
- Es wird empfohlen, die Demo-Umgebung (Visual Studio, gestartete API, Swagger UI/Postman, ggf. DB-Browser) vor der Präsentation vorzubereiten und einmal durchzuspielen.
- Folien sind optional und dürfen schlank gehalten werden (z. B. 3–5 Folien für Ausgangslage/Architektur); der Schwerpunkt liegt auf der Live-Demo.
- Rückfragen zu Design-Entscheidungen (z. B. „Warum DTOs?", „Wie funktioniert die Token-Prüfung?") müssen aus dem Stand plausibel beantwortet werden können.

---

## 7. Funktionale Anforderungen

- Alle fünf CRUD-Operationen auf der Ressource `Werkzeuge` sind vollständig und korrekt implementiert.
- Die API liefert und akzeptiert Daten im JSON-Format.
- Filterung der Liste nach Verfügbarkeit ist möglich.
- Nicht vorhandene Ressourcen liefern `404 Not Found`, ungültige Anfragen `400 Bad Request`.

## 8. Nicht-funktionale Anforderungen

- Klare Schichtentrennung (Controller / Datenzugriff / Modelle).
- Nachvollziehbare, konsistente Namensgebung gemäss Coderichtlinien.
- Aussagekräftiges Logging (mind. Start der Anwendung, Fehlerfälle).
- API-Dokumentation ist über Swagger UI aufrufbar und aktuell.

## 9. Sicherheitsanforderungen

- Schreibender Zugriff ist ausschliesslich mit gültigem JWT möglich (Handlungsziel 6).
- Eingabedaten werden serverseitig validiert (keine ungeprüfte Übernahme von Client-Daten).
- Zugriffe auf die Datenbank erfolgen ausschliesslich parametrisiert über EF Core (kein manuelles String-Concatenation-SQL), um SQL-Injection auszuschliessen.
- Es werden keine Passwörter oder Secrets im Klartext im Repository abgelegt (z. B. Nutzung von `dotnet user-secrets` für den JWT-Signaturschlüssel in der Entwicklung).

---

## 10. Abzugebende Ergebnisse

1. **Quellcode** der Visual-Studio-Solution inkl. `.git`-Verlauf (als ZIP mit `.git`-Ordner oder als Link auf ein Remote-Repository)
2. **Technische Dokumentation** (Markdown oder Word), enthält mindestens:
   - Architekturüberblick und Setup-/Startanleitung (README)
   - Datenmodell und Beschreibung der Endpunkte
   - Beschreibung des Authentifizierungskonzepts
   - Änderungsprotokoll aus Handlungsziel 3
   - Kurzreflexion: Was war herausfordernd, was würden Sie beim nächsten Mal anders machen?
3. **Testnachweise**: Screenshots aus Swagger UI/Postman zu allen Endpunkten, inkl. mind. 3 Negativtests und dem Nachweis von `401 Unauthorized` ohne Token
4. **Coderichtlinien-Nachweis**: kurze Notiz/Screenshot zu verwendeten Analyzer-Regeln und einem behobenen Verstoss
5. **Abschlusspräsentation** (15–20 Min.) mit Live-Demo gemäss Abschnitt 6.7; Folien (falls verwendet) sind zusätzlich einzureichen

---

## 11. Bewertung

Die Gesamtnote setzt sich aus zwei Teilnoten zusammen: der **Projektarbeit** (Gewicht 80 %) und der **Abschlusspräsentation** (Gewicht 20 %).

### 11.1 Teilnote Projektarbeit (100 Punkte, Gewicht 80 %)

Die Bewertung der Projektarbeit erfolgt anhand des folgenden Kriterienrasters, das die Kompetenz und alle sechs Handlungsziele des Moduls 295 abdeckt.

| Nr. | Kriterium                                                                                               | Handlungsziel | Punkte  |
| --- | ------------------------------------------------------------------------------------------------------- | ------------- | ------- |
| 1   | Entwicklungsumgebung korrekt eingerichtet, Projekt lauffähig, Setup dokumentiert                        | HZ1           | 5       |
| 2   | Alle 5 CRUD-Endpunkte vollständig und korrekt implementiert                                             | HZ2           | 15      |
| 3   | Saubere Schichtenarchitektur (Controller/Data/DTOs), aktueller REST-Standard eingehalten                | HZ2           | 10      |
| 4   | API über OpenAPI/Swagger dokumentiert, ergänzende technische Dokumentation vorhanden und verständlich   | HZ2           | 10      |
| 5   | Manuelle Tests aller Endpunkte inkl. Negativfälle nachvollziehbar dokumentiert (Screenshots)            | HZ3           | 8       |
| 6   | Eingabevalidierung funktional und mit Anforderungen abgeglichen, Änderungsprotokoll vorhanden           | HZ3           | 7       |
| 7   | Coderichtlinien (.editorconfig/Analyzer) eingerichtet und eingehalten, Nachweis Regelkorrektur          | HZ4           | 10      |
| 8   | Git-Repository mit regelmässiger, nachvollziehbarer Commit-Historie über den ganzen Entwicklungsverlauf | HZ5           | 10      |
| 9   | JWT-Login-Endpunkt korrekt implementiert und funktionsfähig                                             | HZ6           | 8       |
| 10  | Schreibende Endpunkte korrekt mit `[Authorize]` geschützt, `401`-Nachweis vorhanden                     | HZ6           | 12      |
| 11  | Gesamteindruck: Codequalität, Struktur, Vollständigkeit und Verständlichkeit der Abgabe                 | –             | 5       |
|     | **Total**                                                                                               |               | **100** |

$$\text{Note}_{\text{Projekt}} = 1 + \frac{\text{erreichte Punkte}}{100} \times 5$$

### 11.2 Teilnote Abschlusspräsentation (20 Punkte, Gewicht 20 %)

| Nr. | Kriterium                                                                                                      | Punkte |
| --- | -------------------------------------------------------------------------------------------------------------- | ------ |
| 1   | Inhaltliche Struktur und Verständlichkeit (Ausgangslage, Architektur, Ergebnisse klar dargestellt)             | 5      |
| 2   | Live-Demo funktioniert einwandfrei und deckt CRUD-Operationen sowie Authentifizierung (inkl. `401`-Fall) ab    | 8      |
| 3   | Fachliche Tiefe: kann eigene Design-Entscheidungen begründen und Rückfragen kompetent beantworten              | 4      |
| 4   | Zeitmanagement und Präsentationstechnik (Zeitrahmen 15–20 Min. eingehalten, klar und strukturiert vorgetragen) | 3      |
|     | **Total**                                                                                                      | **20** |

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
- Eine einfache, direkte Umsetzung ohne zusätzliche Architekturmuster (z. B. kein separates Repository-Pattern) ist für den Einstieg ausreichend und wird nicht negativ bewertet – wichtiger sind Korrektheit, Nachvollziehbarkeit und Sicherheit.
- Bei Unklarheiten zur Aufgabenstellung ist Rücksprache mit der Lehrperson zu halten.
- Die Abschlusspräsentation findet am Präsentationstermin statt; die Anwendung muss zu diesem Zeitpunkt live vorführbar sein (siehe Abschnitt 6.7).
