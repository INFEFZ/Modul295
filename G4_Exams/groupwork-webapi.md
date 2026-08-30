|               |                                           |                                        |
| ------------- | ----------------------------------------- | -------------------------------------- |
| **Modul 295** | **Backend für Applikationen realisieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

# Gruppenarbeit – ASP.NET Core WebAPI-Grundlagen und Authentifizierung (Selbststudium für Nachholende)

## 1. Übersicht

|                             |                                                                                                                                                                          |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Modul**                   | 295 – Backend für Applikationen realisieren                                                                                                                              |
| **Zielgruppe**              | Modul-Nachholende                                                                                                                                                        |
| **Ersetzt**                 | 1:1-Durchgang der Kursinhalte von Tag 3 und Tag 4 (gemäss [G1_Agenda](https://github.com/INFEFZ/Modul295/tree/main/G1_Agenda))                                           |
| **Sozialform**              | Gruppenarbeit (5 Gruppen à ca. 2–4 Studierende, je nach Klassengrösse anzupassen)                                                                                        |
| **Format**                  | Flipped Classroom: selbständige Erarbeitung + gegenseitige Präsentation mit Live-Codebeispiel, anschliessend individuelle Vertiefung anhand der bestehenden Kursaufgaben |
| **Vorbereitungszeit**       | ca. 3–5 Std. pro Gruppe (siehe Abschnitt 4)                                                                                                                              |
| **Präsentationsdauer**      | 20–25 Min. pro Gruppe + ca. 5 Min. Fragerunde                                                                                                                            |
| **Individuelle Vertiefung** | ca. 8.5 Std. (bestehende Einzelaufgaben aus dem Kurs, siehe Abschnitt 5)                                                                                                 |
| **Bewertung**               | Unbenotet – wie bereits beim Auftrag zu Tag 1/2 vereinbart, dient dem Wissensaufbau                                                                                      |

Dieser Auftrag baut direkt auf den bisherigen Gruppenarbeit-Auftrag zu Tag 1/2 auf und deckt nun **Agenda Tag 3** und **Agenda Tag 4** ab. Anders als bei Tag 1/2 enthalten diese beiden Tage bereits eine Reihe konkreter, im Kurs vordefinierter **Einzelaufgaben** (Pizza-Tutorial, UserAPI, Movie-API, API-Key- und JWT-Implementierung). Diese bleiben bewusst als **individuelle Vertiefung nach den Gruppenpräsentationen** bestehen – die Gruppenarbeit selbst vermittelt die dazu nötigen Konzepte, ersetzt aber nicht das eigenständige Programmieren, das im Original-Kurskonzept explizit als Einzelarbeit vorgesehen ist.

---

## 2. Ausgangslage

Tag 3 vertieft die an Tag 1 nur eingeführten ASP.NET-Core-WebAPI-Grundlagen (Ordner [B5_Core](https://github.com/INFEFZ/Modul295/tree/main/B5_Core)): Aufbau von `Program.cs`, Dependency-Injection-Container, Controller- und Action-Methoden, Routing, Parameterbinding, DTO-Muster und REST-Namenskonventionen. Tag 4 behandelt Authentifizierung (Ordner [B6_Auth](https://github.com/INFEFZ/Modul295/tree/main/B6_Auth)): eine Übersicht gängiger Strategien (Basic, API-Key, JWT/Bearer, OAuth 2.0, Session) sowie deren praktische Umsetzung mit Custom Middleware bzw. JWT.

Interessanterweise ist die Auth-Theorie im Original-Kurs bereits als **Gruppenarbeit mit Kurzpräsentation** angelegt (vgl. Aufgabe „WebAPI Authentifikation" in [B6_Auth](https://github.com/INFEFZ/Modul295/blob/main/B6_Auth/README.md)). Dieser Auftrag übernimmt diese Idee, erweitert sie aber auf die gesamten Tage 3 und 4 und passt Umfang sowie Tiefe an den Umstand an, dass hier keine vorgängige Instruktion durch die Lehrperson stattfindet.

---

## 3. Ablauf

### 3.1 Gruppenarbeitsphase *(3–5 Std. pro Gruppe, siehe Zeitangaben in Abschnitt 4)*

Jede Gruppe erarbeitet sich ihr zugeteiltes Thema (siehe Abschnitt 4) selbständig anhand der verlinkten Kursunterlagen und erstellt:

1. Ein **Theorie-Handout in Markdown** (nicht PowerPoint – entsprechend der bestehenden Modul-Konvention), das die Kernpunkte des Themas verständlich zusammenfasst.
2. Ein **lauffähiges Live-Codebeispiel** in Visual Studio/C#, das das Thema praktisch zeigt (siehe Vorschläge je Gruppe in Abschnitt 4). Bei den Auth-Praxis-Gruppen (4 und 5) darf dabei auf den im README bereits vorhandenen Beispielcode aufgebaut werden – der Fokus liegt auf dem **Verstehen und Erklären**, nicht auf dem Neuerfinden.
3. **Mindestens 3 Verständnisfragen inkl. Musterantworten**, mit denen die Gruppe am Ende ihrer Präsentation die Klasse aktiv einbindet.

### 3.2 Präsentationstag *(ca. 2.5 Std. gesamt für 5 Gruppen)*

| Gruppe | Thema                                                 |
| ------ | ----------------------------------------------------- |
| 1      | ASP.NET Core WebAPI Basiselemente                     |
| 2      | Controller, Action-Methoden & REST-Namenskonventionen |
| —      | Pause                                                 |
| 3      | Authentifizierungs-Strategien im Überblick            |
| 4      | API-Key-Authentifizierung in der Praxis               |
| 5      | JWT-Authentifizierung in der Praxis                   |

---

## 4. Gruppeneinteilung und Themen

### Gruppe 1 – ASP.NET Core WebAPI Basiselemente

**Kursordner:** [B5_Core](https://github.com/INFEFZ/Modul295/blob/main/B5_Core/README.md)

**Vorbereitungszeit:** ca. 4 Std.

**Zu behandelnde Inhalte:**

- Aufbau und Zweck von `Program.cs` als Einstiegspunkt (Services registrieren, Middleware-Pipeline, `app.Run()`)
- Dependency-Injection-Container (`builder.Services`, z. B. `AddControllers()`, `AddSwaggerGen()`)
- Swagger/OpenAPI-Einbindung (`AddEndpointsApiExplorer`, `UseSwagger`, `UseSwaggerUI`)
- Konventionsbasiertes Routing vs. Attribut-Routing, Aufbau der Controller-Klasse (`ControllerBase`, `[Route("api/[controller]")]`)

**Vorschlag Live-Codebeispiel:** Ein neues WebAPI-Projekt von Grund auf in Visual Studio erstellen, `Program.cs` Zeile für Zeile erklären, einen einfachen Controller mit `[Route]`-Attribut hinzufügen und über Swagger UI live testen.

**Leitfragen zur Selbstprüfung:** Was passiert genau zwischen `builder.Build()` und `app.Run()`? Warum wird Swagger UI nur in der Entwicklungsumgebung aktiviert? Was ist der Unterschied zwischen konventionsbasiertem und Attribut-Routing?

### Gruppe 2 – Controller, Action-Methoden & REST-Namenskonventionen

**Kursordner:** [B5_Core](https://github.com/INFEFZ/Modul295/blob/main/B5_Core/README.md)

**Vorbereitungszeit:** ca. 4–5 Std.

**Zu behandelnde Inhalte:**

- Action-Methoden und HTTP-Attribute (`[HttpGet]`, `[HttpPost]`, `[HttpPut]`, `[HttpDelete]`)
- Parameterbinding: `[FromRoute]`, `[FromBody]`, `[FromQuery]`
- DTO-Klassen: Zweck (kein direktes Zurückgeben von Entitäten), Beispiel Company/CompanyDto
- Validierungsattribute (`[Required]`, `[MaxLength]` usw.)
- REST-Namenskonventionen: Substantive statt Verben, pluralisierte Ressourcen, Bindestriche statt Unterstriche, Query-Strings für Sortierung/Filterung, Hierarchie zwischen Ressourcen (`/api/companies/{companyId}/employees`)

**Vorschlag Live-Codebeispiel:** Live einen GET-, POST-, PUT- und DELETE-Endpunkt für eine einfache Ressource implementieren, dabei eine DTO-Klasse einsetzen und mit Postman testen; anhand von 2–3 schlechten vs. guten URL-Beispielen die Namenskonventionen erklären.

**Leitfragen zur Selbstprüfung:** Warum sollte man keine Entitäten direkt zurückgeben, sondern DTOs verwenden? Wann verwendet man `[FromBody]` statt `[FromRoute]`? Was ist an `/api/user/GetUser({UserId})` problematisch, und wie sähe die korrekte REST-Route aus?

### Gruppe 3 – Authentifizierungs-Strategien im Überblick

**Kursordner:** [B6_Auth](https://github.com/INFEFZ/Modul295/blob/main/B6_Auth/README.md)

**Vorbereitungszeit:** ca. 4–5 Std.

**Zu behandelnde Inhalte:** Vergleichende Übersicht der fünf im Kurs behandelten Strategien – für jede Strategie: Voraussetzungen, Ablauf/Datenaustausch, wie Sicherheit gewährleistet wird, Vor- und Nachteile, typische Einsatzgebiete:

- Basisauthentifizierung (Base64, Authorization-Header)
- Token-basierte Authentifizierung / JWT (Aufbau: Header, Payload, Signatur)
- API-Key & Secret
- OAuth 2.0 (Grundidee, Authorization Server, Access/Refresh Token)
- Session-basierte Authentifizierung

**Vorschlag Live-Codebeispiel:** Ein dekodiertes JWT (z. B. via [jwt.io](https://jwt.io)) live zeigen und Header/Payload/Signatur erklären; einen Basic-Auth-Header live Base64-dekodieren, um die fehlende Verschlüsselung zu veranschaulichen.

**Leitfragen zur Selbstprüfung:** Warum ist Basic Authentication ohne HTTPS gefährlich? Was bedeutet «stateless» bei JWT, und welchen Vorteil bringt das? Wann eignet sich API-Key-Authentifizierung, wann eher OAuth 2.0?

### Gruppe 4 – API-Key-Authentifizierung in der Praxis

**Kursordner:** [B6_Auth](https://github.com/INFEFZ/Modul295/blob/main/B6_Auth/README.md)

**Vorbereitungszeit:** ca. 3 Std.

**Zu behandelnde Inhalte:**

- Generierung eines API-Keys (`RandomNumberGenerator`)
- Custom Middleware-Konzept in ASP.NET Core (`RequestDelegate`, `InvokeAsync`)
- Ablesen des API-Keys aus `appsettings.json` via `IConfiguration`
- Registrierung der Middleware in `Program.cs` (`app.UseMiddleware<...>()`)
- Rückgabe von `401 Unauthorized` bei fehlendem/ungültigem Key

**Vorschlag Live-Codebeispiel:** Die im Kurs-README bereits vorgegebene `ApiKeyMiddleware`-Klasse live in einem neuen WebAPI-Projekt einbauen und registrieren; mit Postman drei Fälle zeigen: kein Key, falscher Key, korrekter Key.

**Leitfragen zur Selbstprüfung:** Was macht `InvokeAsync` in einer Custom Middleware konkret? Warum wird der API-Key über `IConfiguration` statt fest im Code hinterlegt? Wo in der Middleware-Pipeline muss `UseMiddleware<ApiKeyMiddleware>()` platziert werden, damit es wirkt?

### Gruppe 5 – JWT-Authentifizierung in der Praxis

**Kursordner:** [B6_Auth](https://github.com/INFEFZ/Modul295/blob/main/B6_Auth/README.md)

**Vorbereitungszeit:** ca. 3–4 Std.

**Zu behandelnde Inhalte:**

- Ablauf: Login mit Username/Passwort → JWT erhalten → JWT bei geschützten Endpunkten mitschicken
- `AccountController` (Login-Endpunkt, JWT-Erzeugung) und `TestController` (Endpunkt mit `[AllowAnonymous]` vs. `[Authorize]`)
- Notwendigkeit von `app.UseAuthentication()` **vor** `app.UseAuthorization()` in `Program.cs`
- Bezug zur JWT-Struktur aus Gruppe 3 (Header/Payload/Signatur) in der konkreten Implementierung

**Vorschlag Live-Codebeispiel:** Das vom Dozenten bereitgestellte Übungsprojekt öffnen (Zugangsdaten siehe verlinkte Aufgabenbeschreibung in B6_Auth, Kapitel 3.3), den Login live mit Postman durchführen, das erhaltene JWT in den Authorization-Header eines nachfolgenden Requests einsetzen und den Unterschied zwischen dem `[AllowAnonymous]`- und dem `[Authorize]`-Endpunkt demonstrieren.

**Leitfragen zur Selbstprüfung:** Warum schlägt der Aufruf eines `[Authorize]`-Endpunkts ohne Token mit `401` fehl? Was passiert, wenn `UseAuthentication()` vergessen wird? Wie unterscheidet sich diese Implementierung von der API-Key-Middleware aus Gruppe 4?

---

## 5. Individuelle Vertiefungsaufgaben (im Anschluss an die Präsentationen)

Diese Aufgaben sind bereits vollständig im Kurs-Repository beschrieben (inkl. Klassendiagrammen, OpenAPI-Spezifikationen und Musterlösungselementen) und werden **unverändert einzeln** bearbeitet – die Gruppenarbeit liefert dazu die theoretische Grundlage.

**Aus Tag 3** ([B5_Core](https://github.com/INFEFZ/Modul295/blob/main/B5_Core/README.md#3-aufgaben)):

| Aufgabe                                                   | Bemerkung                                        |
| --------------------------------------------------------- | ------------------------------------------------ |
| Tutorial Pizza REST-API                                   | Schritt-für-Schritt-Tutorial via Microsoft Learn |
| User REST-API (UserApi)                                   | Gemäss vorgegebenem Klassendiagramm/OpenAPI      |
| Movie REST-API mit SQL-Datenbank (MoviesAPIv1)            | EF Core Code-First                               |
| Movie REST-API mit Service u. DTO-Klassen (MoviesAPIv2)   | Service-Layer + DTO, DI                          |
| *(Optional)* Ski-Service Migration Node.js → ASP.NET Core | Bezug zu Modul 294                               |

**Aus Tag 4** ([B6_Auth](https://github.com/INFEFZ/Modul295/blob/main/B6_Auth/README.md#3-aufgaben)):

| Aufgabe                                  | Zeitbedarf | Bemerkung                                         |
| ---------------------------------------- | ---------- | ------------------------------------------------- |
| API-Key Authentifikation Implementierung | 80 Min.    | Custom Middleware, WeatherForecast-Projekt        |
| JWT Authentifikation                     | 80 Min.    | Vorgegebenes GitHub-Projekt mit TODO-Markierungen |

**Gesamt (ohne optionale Aufgabe):** ca. 530 Min. ≈ **8.5 Std.** – vergleichbar mit dem Aufwand, den reguläre Studierende an Tag 3/4 ohnehin individuell investieren.

---

## 6. Erfüllungskriterien (unbenotet)

- Handout liegt in **Markdown-Format** vor (nicht PowerPoint) und deckt alle in Abschnitt 4 genannten Kernpunkte ab.
- Mindestens **ein lauffähiges Live-Codebeispiel** wurde während der Präsentation tatsächlich ausgeführt.
- Die Präsentation wurde im vorgesehenen Zeitrahmen (20–25 Min.) durchgeführt.
- Mindestens **3 Verständnisfragen inkl. Musterantworten** wurden erstellt und der Klasse gestellt.
- Alle Gruppenmitglieder waren erkennbar an Recherche und Präsentation beteiligt.
- Im Anschluss wurden die individuellen Vertiefungsaufgaben gemäss Abschnitt 5 bearbeitet.

Die Lehrperson kann diese Kriterien als einfache Checkliste (erfüllt/nicht erfüllt) pro Gruppe bzw. Person festhalten.

---

## 7. Hinweise

- Dieser Auftrag setzt den Gruppenarbeit-Auftrag zu Tag 1/2 fort und verwendet dieselbe Bewertungslogik (unbenotet) und dasselbe Format (Markdown-Handout, Live-Codebeispiel, Verständnisfragen).
- Gruppe 4 und 5 (Auth-Praxis) dürfen und sollen auf dem im Kurs bereits vorhandenen Beispielcode aufbauen – Ziel ist das Verstehen und verständliche Erklären, nicht das Neuerfinden der Middleware bzw. JWT-Logik.
- Die in Gruppe 2 und 3 vermittelten Konzepte (DTOs, Service-Layer, JWT, rollenbasierte Autorisierung) sind direkte Voraussetzung für die anschliessende Projektarbeit («ToolTrack API» bzw. «HelpDesk AI API») – ein Verweis darauf in der Präsentation schafft einen sinnvollen Bezug.
- Die Gruppeneinteilung (5 Gruppen) ist ein Vorschlag und kann je nach Anzahl Nachholender angepasst werden.
- Bei Unklarheiten zu den Kursunterlagen ist Rücksprache mit der Lehrperson zu halten.

---

## Quellen

- [Modul-295-Repository](https://github.com/INFEFZ/Modul295)
- [Agenda Tag 3](https://github.com/INFEFZ/Modul295/blob/main/G1_Agenda/agenda-day-3.md)
- [Agenda Tag 4](https://github.com/INFEFZ/Modul295/blob/main/G1_Agenda/agenda-day-4.md)
- [B5_Core – ASP.NET Core WebAPI Basiselemente](https://github.com/INFEFZ/Modul295/blob/main/B5_Core/README.md)
- [B6_Auth – REST API Authentication](https://github.com/INFEFZ/Modul295/blob/main/B6_Auth/README.md)
