# Spotify Local Controller – User Manual

**Created and tested by:** Cyb3r ([cyber-suli.hu](https://cyber-suli.hu)), with the assistance of [OpenAI Codex](https://developers.openai.com/learn/codex).

**Version:** 1.0.0  
**Platform:** Windows 10/11 and Elgato Stream Deck 7.1 or later  
**Language:** English

## 1. Overview

Spotify Local Controller is a local Stream Deck plugin for the Spotify desktop
app. Playback commands use Windows GSMTC, while volume commands target Spotify's
own Windows audio session. No Spotify developer account, API key, OAuth login,
background service, administrator rights, firewall change, or separate Node.js
or .NET installation is required.

An internet connection is needed only when a playlist name and cover are first
downloaded. Playback control remains local.

## 2. Requirements

- Windows 10 1809 or later, or Windows 11;
- Elgato Stream Deck 7.1 or later;
- a Keypad-compatible Stream Deck device;
- Spotify Desktop installed.

## 3. Installation and updates

1. Open `com.localmediacontrollers.spotify.streamDeckPlugin`.
2. Approve the installation in Stream Deck.
3. If an update cannot be installed over a development build, remove the old
   Spotify Local Controller, restart Stream Deck, then install the new package.

The plugin does not install a profile or rearrange existing buttons.

## 4. Adding actions

Open Stream Deck, find **Spotify Local Controller** in the action list, and drag
the required actions onto free keys. Select a placed key to open its Property
Inspector. The same action can be used more than once; each playlist key can
store a different playlist.

## 5. Plugin language

Select any placed Spotify action and choose **Plugin language** at the top of the
Property Inspector. Available languages are Hungarian, English, German, French,
Spanish, Italian, and Simplified Chinese. The selection applies globally and is
preserved after restarting Stream Deck.

Stream Deck itself does not officially expose Hungarian or Italian host locale
codes. Therefore, action-list names may follow the Stream Deck host language,
while Property Inspectors and dynamic key labels use the plugin language.

## 6. Actions

| Action | Function | Notes |
|---|---|---|
| **Launch Spotify** | Opens Spotify. | Does not start playback. |
| **Open playlist** | Opens the configured playlist in Spotify. | Does not replace the active queue. |
| **Previous track** | Skips to the previous item. | Targets only an unambiguous Spotify session. |
| **Play / pause** | Toggles playback. | The icon follows the actual state. |
| **Next track** | Skips to the next active-queue item. | Opening a playlist alone does not change the queue. |
| **Now playing** | Shows track title and artist. | Reports when metadata is unavailable. |
| **Spotify volume down/up** | Changes only Spotify's volume. | Step size is configurable from 1–50%. |
| **Mute Spotify** | Toggles Spotify mute. | Preserves the previous volume level. |
| **Playback mode** | Cycles sequential, repeat track, and shuffle. | Shows the state reported by Spotify. |

## 7. Play/pause states

- **Play icon:** Spotify is paused or stopped.
- **Pause icon:** Spotify is playing.
- **Action-specific dark-green icon:** no reliable Spotify session is available.

The plugin does not display a misleading state when Spotify is unavailable.
Every playback controller uses its own dark icon. The launch key stays green,
while the playlist key keeps its cover or normal list icon because it does not
depend on the active media session.

### 7.1 Button skins without Spotify running

If the Spotify application is not running, or it has not yet created a
controllable Windows GSMTC session, the keys appear as follows:

| Key | Appearance without Spotify |
|---|---|
| **Launch Spotify** | Normal highlighted green Spotify icon; remains usable. |
| **Open playlist** | Keeps the downloaded cover, or the normal playlist icon when no cover is available. |
| **Previous track** | Dark-green previous-track icon. |
| **Play / pause** | Dark-green Play icon; no misleading Pause icon is shown. |
| **Next track** | Dark-green next-track icon. |
| **Now playing** | Dark-green information icon. |
| **Volume down / up** | The corresponding dark-green volume icon. |
| **Mute** | Dark-green, uncrossed speaker icon. |
| **Playback mode** | Dark-green sequential-playback icon. |

Session-dependent keys display **No Spotify**. After Spotify starts and an
active session appears, they automatically return to their actual highlighted
states; the keys do not need to be added again.

## 8. Spotify volume

Select a normal Spotify action, enter an integer from 1 to 50 in **Volume step
(%)**, then select **Save volume step**. The default is 5%. Only Spotify's active
audio session is changed; Windows master volume and other apps are untouched.

## 9. Playback mode

Each press cycles through: sequential → repeat current track → shuffle →
sequential. If Spotify does not expose repeat and shuffle through GSMTC, the key
shows **Not supported** instead of reporting a false success.

## 10. Creating a playlist key

### 10.1 Copying the link

In Spotify Desktop, right-click a playlist and select **Share → Copy link**.
Holding Alt lets Spotify copy a URI. Supported formats are:

- `https://open.spotify.com/playlist/...`
- `spotify:playlist:...`

`spotify.link` short links and non-Spotify URLs are rejected.

### 10.2 Configuring the key

1. Place the **Open playlist** action.
2. Paste the link into **Playlist link or URI**.
3. Leave **Custom button title** empty to use the Spotify name, or enter a title
   of up to 18 characters.
4. Select **Save**.

The plugin downloads the playlist name and cover, assigns the cover to the key,
and caches it locally. No API key or separate Spotify login is required. If the
download fails, the default playlist icon and manual title remain usable.

### 10.3 Queue limitation

The key only navigates to the playlist page. It does not replace Spotify's
active playback queue. Select a track from the opened playlist in Spotify to
make that playlist the active playback context.

## 11. Local cover cache

Downloaded covers are stored in:

```text
%LOCALAPPDATA%\LocalMediaControllers\spotify-playlist-cache
```

The cache contains images only—no password, token, or API key. Supported formats
are JPEG, PNG, and WebP up to 2 MB. To refresh a changed cover, close Stream
Deck, remove that playlist's cached image, restart Stream Deck, and save the
playlist setting again.

## 12. Troubleshooting

### Installation fails

Remove the previous plugin, restart Stream Deck, and install the new package.

### Plugin language is missing

Version 0.6.0 or later is required. Reinstall it and restart Stream Deck.

### The key says “No Spotify”

Start Spotify and manually play a track once to create its Windows media
session. Close duplicate Spotify instances and restart Spotify or Stream Deck if
necessary.

### The key says “No audio”

Play a track once and confirm that Spotify uses the default multimedia output.
Custom per-app output routing may not work in every configuration.

### The playlist opens but Next uses the old queue

This is expected: opening is navigation, not queue replacement. Select a track
from the opened playlist.

### The playlist cover is missing

Check the internet connection, use a full Spotify playlist URL or URI, verify
that the playlist is accessible, and save the setting again.

## 13. Privacy and security

- Playback control does not use Spotify Web API or OAuth.
- No Spotify password is requested or stored.
- The plugin does not send global media keys or control another player as a
  fallback.
- Playlist references are validated in both plugin and native layers.
- Metadata comes only from Spotify oEmbed and approved Spotify image hosts.
- TLS certificate verification remains enabled.

## 14. Uninstallation

Remove **Spotify Local Controller** from Stream Deck's plugin settings. To remove
cached covers as well, delete:

```text
%LOCALAPPDATA%\LocalMediaControllers\spotify-playlist-cache
```

Uninstallation does not change Spotify or Windows audio settings.

## 15. Quick checklist

- [ ] Spotify launches from the key.
- [ ] Play/Pause follows the actual state.
- [ ] Previous and Next control only Spotify.
- [ ] Volume and mute affect only Spotify.
- [ ] Playback mode cycles through all supported states.
- [ ] Playlist keys open the correct playlists.
- [ ] Playlist names and covers load automatically.
- [ ] Custom titles override automatic names.
- [ ] The selected plugin language survives a restart.

