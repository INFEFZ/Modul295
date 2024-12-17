|               |                                           |                                        |
| ------------- | ----------------------------------------- | -------------------------------------- |
| **Modul 295** | **Backend für Applikationen realisieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

- [1. .NET CLI](#1-net-cli)
  - [1.1. Einführung](#11-einführung)
  - [1.2. Wichtige CLI-Befehle](#12-wichtige-cli-befehle)

# 1. .NET CLI

## 1.1. Einführung

Die .NET CLI (Command-Line Interface) ist ein plattformübergreifendes Tool, das Entwicklern hilft, .NET-Projekte zu erstellen, zu verwalten und auszuführen. Sie wird über den Befehl dotnet aufgerufen und ist ein Kernbestandteil des .NET SDK. Mit der .NET CLI können Sie Projekte erstellen, Pakete verwalten, Build- und Veröffentlichungsprozesse automatisieren und vieles mehr – alles direkt aus der Kommandozeile.

## 1.2. Wichtige CLI-Befehle

Erstellen eines neuen Projekts:
> `dotnet new <template> -n <Projektname>`

- Beispiele
- Konsolenanwendung: `dotnet new console -n MyConsoleApp`
  - Web-API: `dotnet new webapi --use-controllers --output TodoApi --framework net8.0`

Wiederherstellen von Abhängigkeiten:
> `dotnet restore`

- Lädt alle im Projekt definierten NuGet-Pakete herunter.

Build-Prozess:
> `dotnet build`

- Erstellt die Anwendung und prüft auf Kompilierungsfehler.

Ausführen der Anwendung:
> `dotnet run`

- Beispiel: `dotnet run --launch-profile https`

- Startet die Anwendung.

Projekt veröffentlichen:
> `dotnet publish -c Release -o <Zielverzeichnis>`

- Erstellt eine bereitstellbare Version der Anwendung.

Unit-Tests ausführen:
> `dotnet test`

- Führt Tests in Testprojekten aus.

Verwalten von NuGet-Paketen:

Paket hinzufügen:
> `dotnet add package <Paketname>`

- Beispiel:
- `dotnet add package Microsoft.EntityFrameworkCore.InMemory`
- `dotnet add package Microsoft.EntityFrameworkCore.Design`
- `dotnet add package Microsoft.EntityFrameworkCore.SqlServer`
- `dotnet add package Microsoft.EntityFrameworkCore.Tools`

Paket entfernen:
> `dotnet remove package <Paketname>`

Projekt- oder Lösungsinformationen anzeigen:
> `dotnet list <objekt> <optionen>`

- Beispiel: dotnet list package zeigt die installierten Pakete an.

Vertrauen Sie dem HTTPS-Entwicklungszertifikat, indem Sie den folgenden Befehl ausführen:
> `dotnet dev-certs https --trust`
