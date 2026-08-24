|               |                                           |                                        |
| ------------- | ----------------------------------------- | -------------------------------------- |
| **Modul 295** | **Backend für Applikationen realisieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

# Gruppenarbeit – Modul 295, Tag 1 & 2 (Selbststudium für Nachholende)

## Eigenständige Erarbeitung der Grundlagen «Backend für Applikationen realisieren» in Gruppenarbeit mit Peer-Präsentation

---

## 1. Übersicht

|                        |                                                                                                                                                                                              |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Modul**              | 295 – Backend für Applikationen realisieren                                                                                                                                                  |
| **Zielgruppe**         | Modul-Nachholende                                                                                                                                                                            |
| **Ersetzt**            | 1:1-Durchgang der Kursinhalte von Tag 1 und Tag 2 (gemäss [G1_Agenda](https://github.com/INFEFZ/Modul295/tree/main/G1_Agenda))                                                               |
| **Sozialform**         | Gruppenarbeit (5 Gruppen à ca. 2–4 Studierende, je nach Klassengrösse anzupassen)                                                                                                            |
| **Format**             | Flipped Classroom: selbständige Erarbeitung + gegenseitige Präsentation mit Live-Codebeispiel                                                                                                |
| **Vorbereitungszeit**  | ca. 4–5 Std. pro Gruppe                                                                                                                                                                      |
| **Präsentationsdauer** | 20–25 Min. pro Gruppe + ca. 5 Min. Fragerunde                                                                                                                                                |
| **Bewertung**          | Unbenotet – dient dem Wissensaufbau, analog zum bestehenden «Themen-Input»-Format des Moduls (siehe [topic-input.md](https://github.com/INFEFZ/Modul295/blob/main/G1_Agenda/topic-input.md)) |

Dieser Auftrag basiert direkt auf den Inhalten von **Agenda Tag 1** und **Agenda Tag 2** Ihres Modul-295-Kurses. Da die Nachholenden die Inhalte nicht mehr 1:1 im Klassenverband durchgehen, erarbeiten sie sich die fachlichen Themen in Gruppen selbständig und vermitteln sie anschliessend gegenseitig – mit Theorie-Handout, Live-Codebeispiel und Verständnisfragen. Der bereits bestehende Grundsatz Ihres Moduls «Präsentationen in Markdown, nicht PowerPoint» gilt auch hier.

---

## 2. Ausgangslage

Die Nachholenden haben die übrigen Module ihrer Ausbildung bereits abgeschlossen und bringen entsprechend Vorwissen mit (Programmierung, OOP, ggf. Datenbanken). Was ihnen fehlt, ist der spezifische Inhalt von Modul 295. Statt die fünf Kurstage 1:1 vorzutragen, erarbeiten sich die Studierenden die fachlichen Kernthemen von Tag 1 und Tag 2 in Gruppen und tragen ihr Wissen der Klasse vor – so wie es im Modul mit dem bestehenden «Themen-Input»-Format bereits für einzelne Themen vorgesehen ist, hier jedoch als vollständiger Ersatz für den Frontalunterricht dieser zwei Tage.

Die administrativen und einführenden Teile von Tag 1 (Modulübersicht/Handlungsziele, Prüfungsformat, Software-Installation, E-Books) eignen sich nicht für eine Gruppenpräsentation und werden separat behandelt (siehe Abschnitt 3).

---

## 3. Ablauf

### 3.1 Kickoff durch die Lehrperson *(ca. 30–45 Min., nicht Teil der Gruppenarbeit)*

Zu Beginn führt die Lehrperson kurz selbst durch die nicht-fachlichen Programmpunkte von Tag 1:

- **Modulübersicht / Handlungsziele:** Kompetenz und die sechs Handlungsziele des Moduls (siehe [Modulidentifikation](https://www.modulbaukasten.ch/module/295/1/de-DE?title=Backend-f%C3%BCr-Applikationen-realisieren)).
- **Prüfungen / Projektarbeit:** Vorstellung des Projektauftrags, mit dem das Modul abschliesst (die bereits erstellten Aufträge «ToolTrack API» bzw. «HelpDesk AI API» für Nachholende, ca. 20–25 Std.).
- **Software-Installation:** Verweis auf [G2_Requirements](https://github.com/INFEFZ/Modul295/tree/main/G2_Requirements) als Selbstcheck – die Studierenden installieren die Entwicklungsumgebung **vor** Beginn der Gruppenarbeit eigenständig.
- **E-Books/Literatur:** Kurzer Hinweis auf [G3_EBooks](https://github.com/INFEFZ/Modul295/tree/main/G3_EBooks) als Nachschlagewerk während der Gruppenarbeit.

### 3.2 Gruppenarbeitsphase *(4–5 Std. pro Gruppe, ausserhalb des Unterrichts oder als betreute Arbeitszeit)*

Jede Gruppe erarbeitet sich ihr zugeteiltes Thema (siehe Abschnitt 4) selbständig anhand der verlinkten Kursunterlagen und erstellt:

1. Ein **Theorie-Handout in Markdown** (nicht PowerPoint – entsprechend der bestehenden Modul-Konvention), das die Kernpunkte des Themas verständlich zusammenfasst.
2. Ein **lauffähiges Live-Codebeispiel** in Visual Studio/C#, das das Thema praktisch zeigt (siehe Vorschläge je Gruppe in Abschnitt 4).
3. **Mindestens 3 Verständnisfragen inkl. Musterantworten**, mit denen die Gruppe am Ende ihrer Präsentation die Klasse aktiv einbindet (z. B. als kurze Frage-Runde oder Kahoot-ähnliches Quiz).

### 3.3 Präsentationstag *(ca. 2.5 Std. gesamt für 5 Gruppen)*

Jede Gruppe präsentiert ihr Thema der Klasse: Theorie-Überblick, Live-Codebeispiel, anschliessend Verständnisfragen an die Klasse.

| Gruppe | Thema                                |
| ------ | ------------------------------------ |
| 1      | REST & OpenAPI/Swagger               |
| 2      | ASP.NET Core WebAPI Grundlagen       |
| 3      | Protokollierung & Versionsverwaltung |
| 4      | Datenbankzugriff mit ADO.NET         |
| 5      | Entity Framework Core & LINQ         |

---

## 4. Gruppeneinteilung und Themen

### Gruppe 1 – REST & OpenAPI/Swagger

**Kursordner:** [B1_OpenAPI](https://github.com/INFEFZ/Modul295/tree/main/B1_OpenAPI), [B2_REST](https://github.com/INFEFZ/Modul295/tree/main/B2_REST)

**Zu behandelnde Inhalte:**

- REST-Prinzipien (zustandslos, Ressourcen, HTTP-Verben GET/POST/PUT/DELETE)
- Wichtige HTTP-Statuscodes und wann sie verwendet werden
- JSON als Austauschformat; Serialisierung/Deserialisierung in C#
- Zweck und Aufbau der OpenAPI-Spezifikation, Swagger UI

**Vorschlag Live-Codebeispiel:** Eine C#-Klasse mit `System.Text.Json` serialisieren/deserialisieren; anschliessend die Swagger-UI-Seite eines kleinen bestehenden WebAPI-Projekts zeigen und erklären, wie sie aus dem Code entsteht.

**Leitfragen zur Selbstprüfung:** Was bedeutet «zustandslos» bei REST? Welcher HTTP-Statuscode gehört zu welcher CRUD-Operation? Wozu dient OpenAPI konkret, wenn der Code doch schon dokumentiert wäre?

### Gruppe 2 – ASP.NET Core WebAPI Grundlagen

**Kursordner:** [B3_WebAPI](https://github.com/INFEFZ/Modul295/tree/main/B3_WebAPI) (inkl. [.NET CLI](https://github.com/INFEFZ/Modul295/blob/main/B3_WebAPI/dotnet-cli.md))

**Zu behandelnde Inhalte:**

- Aufbau eines ASP.NET-Core-WebAPI-Projekts (`Program.cs`, Projektstruktur)
- Controller-basierte API vs. Minimal API
- Routing und HTTP-Attribute (`[Route]`, `[HttpGet]`, `[HttpPost]` usw.)
- Parameterbindung (Route-, Query-, Body-Parameter)
- Grundprinzip Dependency Injection
- Wichtige .NET-CLI-Befehle (`dotnet new webapi`, `dotnet run`, `dotnet add package`)

**Vorschlag Live-Codebeispiel:** Live in Visual Studio einen minimalen Controller mit zwei Endpunkten erstellen, über Swagger UI testen, und einen einfachen Service per Dependency Injection registrieren und im Controller nutzen.

**Leitfragen zur Selbstprüfung:** Worin unterscheiden sich Minimal API und Controller-basierte API? Wie gelangt ein Wert aus der URL in die Methode? Was macht Dependency Injection und warum lohnt sich der Einsatz?

### Gruppe 3 – Protokollierung & Versionsverwaltung

**Kursordner:** [B4_Logging](https://github.com/INFEFZ/Modul295/tree/main/B4_Logging), [E1_Git](https://github.com/INFEFZ/Modul295/tree/main/E1_Git)

**Zu behandelnde Inhalte:**

- Zweck von Logging (Nachvollziehbarkeit, Fehlersuche)
- `ILogger` in ASP.NET Core, Log-Level (Trace/Debug/Information/Warning/Error/Critical)
- Git-Grundlagen: Repository, Commit, Branch, Push/Pull, `.gitignore`
- Gute Commit-Messages und ein sinnvoller Commit-Rhythmus

**Vorschlag Live-Codebeispiel:** `ILogger` in einem Controller einsetzen und die Konsolenausgabe zeigen; parallel dazu live ein kleines Git-Repository initialisieren, eine `.gitignore` für ein .NET-Projekt einrichten und einen Commit erstellen/pushen.

**Leitfragen zur Selbstprüfung:** Wann verwendet man welchen Log-Level? Warum braucht ein .NET-Projekt eine passende `.gitignore`? Was macht eine Commit-Historie gut nachvollziehbar?

### Gruppe 4 – Datenbankzugriff mit ADO.NET

**Kursordner:** [D1_ADO.NET](https://github.com/INFEFZ/Modul295/tree/main/D1_ADO.NET)

**Zu behandelnde Inhalte:**

- Architektur von ADO.NET (Connection, Command, DataReader/DataAdapter)
- Verbindungsaufbau zu einer Datenbank
- SQL-Befehle aus C# ausführen
- Parametrisierte Queries als Schutz vor SQL-Injection

**Vorschlag Live-Codebeispiel:** Live-Code, das mit reinem ADO.NET eine SQL-Abfrage gegen eine kleine SQLite-Datenbank ausführt und die Resultate ausliest – einmal korrekt parametrisiert, einmal (nur zur Illustration!) mit String-Concatenation, um die Gefahr sichtbar zu machen.

**Leitfragen zur Selbstprüfung:** Warum sind parametrisierte Queries wichtig? Was unterscheidet `DataReader` von `DataAdapter`? Welche Nachteile hat der direkte ADO.NET-Zugriff im Vergleich zu einem OR-Mapper?

### Gruppe 5 – Entity Framework Core & LINQ

**Kursordner:** [D2_ADO.EF](https://github.com/INFEFZ/Modul295/tree/main/D2_ADO.EF)

**Zu behandelnde Inhalte:**

- Grundidee eines OR-Mappers
- EF-Core-Grundbausteine: `DbContext`, `DbSet`, Entity, Migration
- Database-First vs. Code-First
- LINQ-Grundlagen: Query-Syntax vs. Methoden-Syntax, häufige Operatoren (`Where`, `Select`, `OrderBy`, `Join`)

**Vorschlag Live-Codebeispiel:** Live ein einfaches Entity-Modell definieren, `DbContext` registrieren, eine LINQ-Abfrage ausführen und das Resultat ausgeben.

**Leitfragen zur Selbstprüfung:** Was unterscheidet Database-First von Code-First? Wie wird aus einer LINQ-Query am Ende SQL? Welche Vorteile bringt EF Core gegenüber reinem ADO.NET – und welche Nachteile?

---

## 5. Erfüllungskriterien (unbenotet)

Da dieser Auftrag unbenotet bleibt, gelten anstelle eines Bewertungsrasters folgende Mindestanforderungen, damit die Gruppenarbeit ihren Zweck als Ersatz für den Frontalunterricht erfüllt:

- Handout liegt in **Markdown-Format** vor (nicht PowerPoint) und deckt alle in Abschnitt 4 genannten Kernpunkte ab.
- Mindestens **ein lauffähiges Live-Codebeispiel** wurde während der Präsentation tatsächlich ausgeführt (nicht nur Code gezeigt).
- Die Präsentation wurde im vorgesehenen Zeitrahmen (20–25 Min.) durchgeführt.
- Mindestens **3 Verständnisfragen inkl. Musterantworten** wurden erstellt und der Klasse gestellt.
- Alle Gruppenmitglieder waren erkennbar an Recherche und Präsentation beteiligt.

Die Lehrperson kann diese Kriterien als einfache Checkliste (erfüllt/nicht erfüllt) pro Gruppe festhalten.

---

## 6. Hinweise

- Handouts und Codebeispiele werden analog zum bestehenden «Themen-Input»-Format abgelegt (z. B. im Kurs-Repository oder in OneNote), damit sie für alle Studierenden als Nachschlagewerk verfügbar bleiben.
- Die hier erarbeiteten Themen (insbesondere ASP.NET Core WebAPI, Entity Framework Core, Logging, Git) sind direkte Voraussetzung für die anschliessende Projektarbeit («ToolTrack API» bzw. «HelpDesk AI API»); ein Verweis darauf in der Präsentation von Gruppe 2 und Gruppe 5 schafft einen sinnvollen Bezug.
- Die Gruppeneinteilung (5 Gruppen) ist ein Vorschlag und kann je nach Anzahl Nachholender angepasst werden – z. B. Zusammenlegen von Gruppe 3 mit Gruppe 1 oder 2 bei einer sehr kleinen Klasse.
- Bei Unklarheiten zu den Kursunterlagen ist Rücksprache mit der Lehrperson zu halten.

---

## Quellen

- [Modul-295-Repository](https://github.com/INFEFZ/Modul295)
- [Agenda Tag 1](https://github.com/INFEFZ/Modul295/blob/main/G1_Agenda/agenda-day-1.md)
- [Agenda Tag 2](https://github.com/INFEFZ/Modul295/blob/main/G1_Agenda/agenda-day-2.md)
- [Themen-Input-Konvention](https://github.com/INFEFZ/Modul295/blob/main/G1_Agenda/topic-input.md)
