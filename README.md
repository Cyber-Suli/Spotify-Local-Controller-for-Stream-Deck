# Spotify Local Controller for Stream Deck

Local-only Spotify control for Elgato Stream Deck on Windows. The plugin uses
Windows GSMTC for playback and Spotify's own Windows audio session for volume,
so it requires no Spotify Web API, developer account, API key, OAuth login, or
cloud control service.

**Created and tested by:** Cyb3r ([cyber-suli.hu](https://cyber-suli.hu)), with
the assistance of [OpenAI Codex](https://developers.openai.com/learn/codex).

> This is an independent community project and is not affiliated with,
> endorsed by, or sponsored by Spotify or Elgato.

## Download

Download the latest `.streamDeckPlugin` package from
[GitHub Releases](https://github.com/Cyber-Suli/Spotify-Local-Controller-for-Stream-Deck/releases).

## Features

- Launch the Spotify desktop application.
- Play or pause, skip to the previous track, and skip to the next track.
- Display the current track title and artist.
- Change or mute Spotify's volume without changing the Windows master volume.
- Configure the volume step from 1% to 50%.
- Cycle between sequential playback, repeat-current-track, and shuffle modes.
- Open a configurable Spotify playlist from a Stream Deck key.
- Download and cache a playlist name and cover automatically.
- Show truthful, action-specific inactive icons when Spotify is unavailable.
- Use the plugin in Hungarian, English, German, French, Spanish, Italian, or
  Simplified Chinese.

## Requirements

- Windows 10 version 1809 or later, or Windows 11;
- Elgato Stream Deck 7.1 or later;
- a Keypad-compatible Stream Deck device;
- Spotify Desktop for Windows.

No separate Node.js or .NET installation is required. The plugin does not
require administrator rights, firewall changes, or a background cloud service.

## Installation

1. Download `com.localmediacontrollers.spotify.streamDeckPlugin` from the
   latest release.
2. Open the downloaded file.
3. Approve the installation in the Stream Deck application.
4. Find **Spotify Local Controller** in the action list and drag the required
   actions onto free keys.

If installation over an older development build fails, remove the previous
plugin, restart Stream Deck, and install the new package again.

## Available actions

| Action | Function |
|---|---|
| Launch Spotify | Opens Spotify without starting playback. |
| Open playlist | Opens a configured playlist in the Spotify application. |
| Previous track | Skips to the previous Spotify item. |
| Play / pause | Toggles playback and follows the actual state. |
| Next track | Skips to the next item in the active queue. |
| Now playing | Displays the current track title and artist. |
| Spotify volume down / up | Changes only Spotify's Windows audio session. |
| Mute Spotify | Toggles Spotify mute while preserving its volume level. |
| Playback mode | Cycles sequential, repeat-current-track, and shuffle modes. |

## Playlist behavior

Playlist keys accept full Spotify playlist URLs and `spotify:playlist:` URIs.
The playlist name and cover are downloaded and cached locally. An internet
connection is required only when this information is first retrieved.

Opening a playlist navigates Spotify to that playlist; it does not replace the
current playback queue. Select a track from the opened playlist to start using
it as the active playback context.

## User manuals

- [English](spotify_streamdeck_manual_en.md)
- [Magyar](spotify_streamdeck_manual_hu.md)
- [Deutsch](spotify_streamdeck_manual_de.md)
- [Français](spotify_streamdeck_manual_fr.md)
- [Español](spotify_streamdeck_manual_es.md)
- [Italiano](spotify_streamdeck_manual_it.md)
- [简体中文](spotify_streamdeck_manual_zh_CN.md)

## Privacy and security

- Playback control does not use Spotify Web API or OAuth.
- No Spotify password, access token, or API key is requested or stored.
- The plugin targets only an unambiguous Spotify media session.
- It does not fall back to global media keys or control another player.
- Spotify volume commands do not change other applications or the Windows
  master volume.
- Playlist metadata comes only from Spotify oEmbed and approved Spotify image
  hosts over TLS.

## Support

If you encounter a problem, first consult the troubleshooting section of the
manual. Reproducible bugs and feature suggestions can be submitted through
[GitHub Issues](https://github.com/Cyber-Suli/Spotify-Local-Controller-for-Stream-Deck/issues).

## License

This software is licensed under the
[PolyForm Noncommercial License 1.0.0](LICENSE.md). It may be used, modified,
and shared for permitted noncommercial purposes. Commercial use requires prior
permission from the licensor. The copyright and required attribution notices
must be preserved when copies are distributed.

Spotify and the Spotify logo are trademarks of Spotify AB. Elgato and Stream
Deck are trademarks of their respective owners.
