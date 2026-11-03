# Spotify Local Controller – Benutzerhandbuch

**Erstellt und getestet von:** Cyb3r ([cyber-suli.hu](https://cyber-suli.hu)), mit Unterstützung von [OpenAI Codex](https://developers.openai.com/learn/codex).

**Version:** 1.0.0  
**Plattform:** Windows 10/11 und Elgato Stream Deck 7.1 oder neuer  
**Sprache:** Deutsch

## 1. Überblick

Spotify Local Controller ist ein lokales Stream-Deck-Plugin für die Spotify-
Desktop-App. Wiedergabebefehle verwenden Windows GSMTC, Lautstärkebefehle die
eigene Windows-Audiositzung von Spotify. Es werden kein Entwicklerkonto, API-
Schlüssel, OAuth, Hintergrunddienst, Administratorrecht sowie keine separate
Node.js- oder .NET-Installation benötigt.

Nur der erste Abruf von Playlistname und Cover benötigt Internet.

## 2. Voraussetzungen

- Windows 10 1809 oder neuer bzw. Windows 11;
- Stream Deck 7.1 oder neuer;
- Keypad-kompatibles Stream-Deck-Gerät;
- installierte Spotify-Desktop-App.

## 3. Installation und Aktualisierung

Öffne `com.localmediacontrollers.spotify.streamDeckPlugin` und bestätige die
Installation. Falls eine ältere Entwicklungsversion das Update verhindert,
entferne das alte Plugin, starte Stream Deck vollständig neu und installiere das
neue Paket. Das Plugin installiert kein Profil und verschiebt keine Tasten.

## 4. Aktionen hinzufügen

Öffne Stream Deck, suche **Spotify Local Controller** und ziehe die gewünschten
Aktionen auf freie Tasten. Eine ausgewählte Taste zeigt rechts den Property
Inspector. Aktionen können mehrfach verwendet werden; jede Playlist-Taste kann
eine andere Liste speichern.

## 5. Plugin-Sprache

Wähle eine Spotify-Taste aus und stelle oben im Property Inspector die
**Plugin-Sprache** ein. Verfügbar sind Ungarisch, Englisch, Deutsch, Französisch,
Spanisch, Italienisch und vereinfachtes Chinesisch. Die globale Auswahl bleibt
nach einem Neustart erhalten.

Stream Deck stellt offiziell keine ungarischen oder italienischen Host-
Sprachcodes bereit. Deshalb kann die Aktionsliste der Host-Sprache folgen,
während Property Inspector und dynamische Tastentexte die Plugin-Sprache nutzen.

## 6. Aktionen

| Aktion | Funktion | Hinweis |
|---|---|---|
| **Spotify starten** | Öffnet Spotify. | Startet keine Wiedergabe. |
| **Playlist öffnen** | Öffnet die festgelegte Playlist. | Ersetzt nicht die aktive Warteschlange. |
| **Vorheriger/Nächster Titel** | Wechselt innerhalb der aktiven Spotify-Warteschlange. | Steuert nur eine eindeutige Spotify-Sitzung. |
| **Wiedergabe / Pause** | Schaltet Wiedergabe um. | Das Symbol folgt dem echten Status. |
| **Aktueller Titel** | Zeigt Titel und Interpret. | Meldet fehlende Metadaten. |
| **Spotify leiser/lauter** | Ändert nur Spotify. | Schrittweite 1–50%. |
| **Spotify stummschalten** | Schaltet die Stummschaltung um. | Der Pegel bleibt erhalten. |
| **Wiedergabemodus** | Reihenfolge, Titelwiederholung, Zufall. | Zeigt den von Spotify gemeldeten Status. |

## 7. Wiedergabestatus

- **Play-Symbol:** Spotify pausiert oder ist gestoppt.
- **Pause-Symbol:** Spotify spielt.
- **Aktionsbezogenes dunkelgrünes Symbol:** keine zuverlässige Spotify-Sitzung
  verfügbar.

Jede Wiedergabesteuerung verwendet ihr eigenes dunkles Symbol. Die Starttaste
bleibt grün; die Playlist-Taste behält ihr Cover oder normales Listensymbol, da
sie nicht von der aktiven Mediensitzung abhängt.

### 7.1 Tasten-Skins ohne laufendes Spotify

Wenn Spotify nicht läuft oder noch keine steuerbare Windows-GSMTC-Sitzung
erstellt hat, werden die Tasten wie folgt dargestellt:

| Taste | Darstellung ohne Spotify |
|---|---|
| **Spotify starten** | Normales hervorgehobenes grünes Spotify-Symbol; bleibt verwendbar. |
| **Playlist öffnen** | Behält das geladene Cover oder ohne Cover das normale Playlist-Symbol. |
| **Vorheriger Titel** | Dunkelgrünes Zurück-Symbol. |
| **Wiedergabe / Pause** | Dunkelgrünes Play-Symbol; kein irreführendes Pause-Symbol. |
| **Nächster Titel** | Dunkelgrünes Weiter-Symbol. |
| **Aktueller Titel** | Dunkelgrünes Informationssymbol. |
| **Lautstärke leiser / lauter** | Das jeweils passende dunkelgrüne Lautstärkesymbol. |
| **Stummschalten** | Dunkelgrünes, nicht durchgestrichenes Lautsprechersymbol. |
| **Wiedergabemodus** | Dunkelgrünes Symbol für Reihenfolge. |

Sitzungsabhängige Tasten zeigen **Kein Spotify**. Sobald Spotify läuft und eine
aktive Sitzung vorhanden ist, wechseln sie automatisch in ihren tatsächlichen,
hervorgehobenen Zustand; die Tasten müssen nicht neu angelegt werden.

## 8. Spotify-Lautstärke

Wähle eine normale Spotify-Aktion, trage unter **Lautstärkeschritt (%)** eine
ganze Zahl von 1 bis 50 ein und speichere sie. Standard sind 5%. Nur Spotifys
aktive Audiositzung wird geändert; Windows-Hauptlautstärke und andere Apps
bleiben unverändert.

## 9. Wiedergabemodus

Jeder Tastendruck schaltet weiter: Reihenfolge → aktuellen Titel wiederholen →
Zufall → Reihenfolge. Wenn Spotify Wiederholung oder Zufall nicht über GSMTC
freigibt, zeigt die Taste **Nicht unterstützt**.

## 10. Playlist-Taste einrichten

Kopiere in Spotify über Rechtsklick → **Teilen → Link kopieren** den Link. Mit
Alt kann eine Spotify-URI kopiert werden. Unterstützt werden:

- `https://open.spotify.com/playlist/...`
- `spotify:playlist:...`

Kurzlinks über `spotify.link` und fremde URLs werden abgewiesen.

1. Platziere **Playlist öffnen**.
2. Füge Link oder URI ein.
3. Lasse den eigenen Titel leer, um den Spotify-Namen zu verwenden, oder gib
   höchstens 18 Zeichen ein.
4. Wähle **Speichern**.

Name und Cover werden geladen, das Cover wird als Tastenbild gesetzt und lokal
zwischengespeichert. API-Schlüssel und zusätzliche Anmeldung sind nicht nötig.
Bei einem Fehler bleiben Standardsymbol und manueller Titel verfügbar.

### Warteschlangenbegrenzung

Die Taste navigiert nur zur Playlist. Sie ersetzt nicht Spotifys aktive
Warteschlange. Wähle in der geöffneten Playlist einen Titel aus, damit sie zum
aktiven Wiedergabekontext wird.

## 11. Lokaler Cover-Cache

```text
%LOCALAPPDATA%\LocalMediaControllers\spotify-playlist-cache
```

Der Cache enthält nur JPEG-, PNG- oder WebP-Bilder bis 2 MB, keine Passwörter,
Tokens oder API-Schlüssel. Für ein aktualisiertes Cover Stream Deck schließen,
die betreffende Cache-Datei entfernen, Stream Deck starten und die Playlist-
Einstellung erneut speichern.

## 12. Fehlerbehebung

- **Installation fehlgeschlagen:** altes Plugin entfernen, Stream Deck neu
  starten, neues Paket installieren.
- **Plugin-Sprache fehlt:** Version 0.6.0 oder neuer installieren und Stream Deck
  neu starten.
- **„Kein Spotify“:** Spotify starten und einmal manuell einen Titel abspielen;
  doppelte Spotify-Instanzen schließen.
- **„Kein Audio“:** einmal abspielen und das Standard-Multimedia-Ausgabegerät
  prüfen.
- **Playlist öffnet, aber „Nächster Titel“ nutzt die alte Warteschlange:** Das ist
  vorgesehen; einen Titel aus der geöffneten Playlist auswählen.
- **Cover fehlt:** Internet, vollständigen Playlist-Link und Erreichbarkeit der
  Liste prüfen, danach erneut speichern.

## 13. Datenschutz und Sicherheit

Die Wiedergabesteuerung verwendet weder Spotify Web API noch OAuth. Das Plugin
fragt kein Spotify-Passwort ab, sendet keine globalen Medientasten und steuert
keinen anderen Player als Ersatz. Playlistangaben werden doppelt validiert;
Metadaten stammen nur von Spotify oEmbed und freigegebenen Spotify-Bildservern.
Die TLS-Prüfung bleibt aktiv.

## 14. Deinstallation

Entferne **Spotify Local Controller** in den Plugin-Einstellungen von Stream
Deck. Optional kann der oben genannte Cache-Ordner gelöscht werden. Spotify- und
Windows-Audioeinstellungen werden nicht verändert.

## 15. Kurzprüfung

- [ ] Spotify startet über die Taste.
- [ ] Play/Pause und die Modussymbole zeigen den echten Status.
- [ ] Lautstärke und Stummschaltung betreffen nur Spotify.
- [ ] Playlist, Name und Cover stimmen.
- [ ] Eigene Titel überschreiben den automatischen Namen.
- [ ] Die Sprache bleibt nach einem Neustart erhalten.

