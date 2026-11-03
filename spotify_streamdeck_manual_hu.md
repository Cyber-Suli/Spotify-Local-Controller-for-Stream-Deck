# Spotify Local Controller – felhasználói kézikönyv

**Létrehozta és tesztelte:** Cyb3r ([cyber-suli.hu](https://cyber-suli.hu)), az [OpenAI Codex](https://developers.openai.com/learn/codex) közreműködésével.

**Verzió:** 1.0.0  
**Platform:** Windows 10/11 és Elgato Stream Deck 7.1 vagy újabb  
**Nyelv:** magyar

## 1. Áttekintés

A Spotify Local Controller egy helyi Stream Deck plugin a Spotify asztali
alkalmazás vezérléséhez. A lejátszási műveletek a Windows GSMTC rendszerén, a
hangerőműveletek pedig a Spotify saját Windows-hangmunkamenetén keresztül
működnek.

A plugin használatához nem kell:

- Spotify fejlesztői fiók vagy API-kulcs;
- OAuth-bejelentkezés;
- külön háttérszolgáltatás;
- rendszergazdai jogosultság;
- tűzfal- vagy Spotify-beállítás módosítása;
- Node.js vagy .NET külön telepítése a végfelhasználói gépre.

A playlist nevének és borítójának első lekéréséhez internetkapcsolat szükséges.
A lejátszás vezérlése ettől függetlenül helyben történik.

## 2. Rendszerkövetelmények

- Windows 10 1809 vagy újabb, illetve Windows 11;
- Elgato Stream Deck alkalmazás 7.1 vagy újabb;
- Stream Deck vagy más Keypad-kompatibilis Stream Deck eszköz;
- telepített Spotify Desktop alkalmazás.

## 3. Telepítés és frissítés

1. Zárd be a Spotify-t, ha éppen telepítés vagy frissítés közben problémát
   tapasztalsz.
2. Dupla kattintással nyisd meg a
   `com.localmediacontrollers.spotify.streamDeckPlugin` fájlt.
3. Fogadd el a telepítést a Stream Deck alkalmazásban.
4. Ha a Stream Deck telepítési hibát jelez egy korábbi fejlesztői verzió fölé
   telepítéskor:
   - távolítsd el a korábbi **Spotify Local Controller** plugint;
   - indítsd újra teljesen a Stream Deck alkalmazást;
   - telepítsd újra az új csomagot.

A plugin nem telepít automatikus profilt, és nem rendezi át a meglévő Stream
Deck-gombokat.

## 4. Műveletek elhelyezése

1. Nyisd meg a Stream Deck alkalmazást.
2. Az actionlistában keresd meg a **Spotify Local Controller** kategóriát.
3. Húzd a kívánt műveletet egy szabad gombra.
4. A gombra kattintva a jobb oldali Property Inspector panelen jelennek meg a
   hozzá tartozó beállítások.

Ugyanaz a művelet több gombra is elhelyezhető. Ez különösen a playlist-gomboknál
hasznos, mert minden példányhoz másik lista rendelhető.

## 5. Nyelv beállítása

1. Kattints bármelyik elhelyezett Spotify Local Controller gombra.
2. A Property Inspector tetején nyisd le a **Plugin nyelve** mezőt.
3. Válassz a következő nyelvek közül:
   - magyar;
   - angol;
   - német;
   - francia;
   - spanyol;
   - olasz;
   - egyszerűsített kínai.

A nyelv globális: minden Spotify-gombra és mindkét beállítópanelre érvényes. A
választás újraindítás után is megmarad.

> A Stream Deck actionlista nyelvét maga a Stream Deck alkalmazás kezeli. A host
> hivatalosan nem támogat magyar és olasz nyelvkódot, ezért az actionlista nyelve
> eltérhet a plugin paneljén kiválasztott nyelvtől. A Property Inspector és a
> dinamikus gombfeliratok ettől még a kiválasztott nyelven működnek.

## 6. A rendelkezésre álló műveletek

| Művelet | Funkció | Megjegyzés |
|---|---|---|
| **Spotify indítása** | Megnyitja a Spotify alkalmazást. | Nem indít el automatikusan zenét. |
| **Lejátszási lista megnyitása** | Megnyitja a beállított playlistet a Spotifyban. | Nem módosítja az aktív lejátszási sort. |
| **Előző szám** | Az előző elemre lép az aktív Spotify-sorban. | Csak az egyértelmű Spotify-munkamenetet vezérli. |
| **Lejátszás / szünet** | Vált a lejátszás és szünet között. | Az ikon követi a tényleges állapotot. |
| **Következő szám** | A következő elemre lép az aktív Spotify-sorban. | A playlist puszta megnyitása nem cseréli le a sort. |
| **Aktuális szám** | Megjeleníti a szám címét és előadóját. | Ha nincs adat, ezt a gomb jelzi. |
| **Spotify hangerő le** | Csökkenti kizárólag a Spotify hangerejét. | A globális Windows-hangerőt nem módosítja. |
| **Spotify hangerő fel** | Növeli kizárólag a Spotify hangerejét. | A lépés 1–50% között állítható. |
| **Spotify némítás** | Némítja vagy visszakapcsolja a Spotify-t. | A korábbi hangerőszint megmarad. |
| **Lejátszási mód** | Vált a sorban, számismétlés és véletlen mód között. | A Spotify által visszajelzett tényleges állapotot mutatja. |

## 7. Lejátszás / szünet állapotai

- **Play ikon:** a Spotify szünetel vagy leállt.
- **Pause ikon:** a Spotify éppen lejátszik.
- **Saját sötétzöld ikon:** nem található vezérelhető Spotify-munkamenet, vagy
  az állapot nem határozható meg megbízhatóan.

A plugin nem mutat megtévesztő Play vagy Pause állapotot, ha a Spotify nem
elérhető. Ilyenkor a lejátszásvezérlők mind a saját sötétített ikonjukkal
jelennek meg. Az indítógomb zöld marad, a playlist-gomb pedig megtartja a
borítóját vagy a normál listaikont, mert nem az aktív munkamenetből kapja.

### 7.1. Gombskinek a Spotify futtatása nélkül

Ha a Spotify alkalmazás nem fut, vagy még nem hozott létre vezérelhető Windows
GSMTC-munkamenetet, a gombok a következőképpen jelennek meg:

| Gomb | Spotify nélküli megjelenés |
|---|---|
| **Spotify indítása** | Normál, kiemelt zöld Spotify-ikon; továbbra is használható. |
| **Lejátszási lista megnyitása** | Megtartja a letöltött borítót, vagy borító nélkül a normál listaikont. |
| **Előző szám** | Sötétzöld előzőszám-ikon. |
| **Lejátszás / szünet** | Sötétzöld Play ikon; nem jelenít meg félrevezető Pause ikont. |
| **Következő szám** | Sötétzöld következőszám-ikon. |
| **Aktuális szám** | Sötétzöld információs ikon. |
| **Hangerő le / fel** | A megfelelő sötétzöld hangerőikon. |
| **Némítás** | Sötétzöld, át nem húzott hangszóróikon. |
| **Lejátszási mód** | Sötétzöld sorban-lejátszási ikon. |

A munkamenettől függő gombok ilyenkor **Nincs Spotify** feliratot mutatnak. A
Spotify elindítása és egy aktív munkamenet létrejötte után automatikusan
visszaváltanak a tényleges, kiemelt állapotukra; nem kell őket újra elhelyezni.

## 8. Spotify-hangerő beállítása

A hangerő fel és hangerő le gombok lépésköze közös, globális beállítás.

1. Kattints bármelyik Spotify-gombra, amely a normál állapotpanelt használja.
2. A **Hangerőlépés (%)** mezőben adj meg egy egész számot 1 és 50 között.
3. Kattints a **Hangerőlépés mentése** gombra.

Az alapérték 5%. A hangerőműveletek csak a Spotify aktív Windows-
hangmunkamenetét kezelik. Más alkalmazás és a Windows fő hangereje nem változik.

## 9. Lejátszási mód

A **Lejátszási mód** gomb minden megnyomáskor a következő állapotra vált:

1. sorban;
2. aktuális szám ismétlése;
3. véletlen lejátszás;
4. vissza sorban módba.

Az ikon és a felirat mindig a Spotify által visszajelzett állapotot követi. Ha a
Spotify aktuális verziója nem jelenti támogatottnak az ismétlés és véletlen mód
vezérlését, a gomb **Nem támogatott** állapotot mutat, és nem jelez hamis sikert.

## 10. Playlist-gomb létrehozása

### 10.1. Link másolása

1. Nyisd meg a kívánt lejátszási listát a Spotify Desktop alkalmazásban.
2. Kattints jobb gombbal a listára.
3. Válaszd a **Megosztás → Hivatkozás másolása** lehetőséget.

A plugin az alábbi formátumokat fogadja el:

- `https://open.spotify.com/playlist/...`
- `spotify:playlist:...`

A `spotify.link` rövidlinkek és a nem Spotify-címek biztonsági okból nem
támogatottak.

### 10.2. Gomb beállítása

1. Húzd a **Lejátszási lista megnyitása** műveletet egy gombra.
2. Kattints a gombra.
3. Illeszd be a linket a **Lejátszási lista linkje vagy URI-ja** mezőbe.
4. Az **Egyéni gombfelirat** mezőt hagyd üresen az automatikus Spotify-névhez,
   vagy adj meg legfeljebb 18 karakteres saját feliratot.
5. Kattints a **Mentés** gombra.

Sikeres mentés után a plugin:

- lekéri a playlist nevét;
- letölti a Spotify által biztosított borítót;
- beállítja a borítót a Stream Deck gomb képének;
- helyben gyorsítótárazza a képet;
- egyéni felirat hiányában a Spotify-nevet használja.

Az automatikus névhez és borítóhoz nem kell API-kulcs vagy külön Spotify-
bejelentkezés. Az első lekéréshez internetkapcsolat szükséges. Sikertelen
lekérésnél az alap playlist ikon és a kézzel megadott felirat marad használatban.

### 10.3. Fontos működési korlátozás

A playlist-gomb csak megnyitja a lista oldalát a Spotifyban. Nem cseréli le az
aktív queue-t, ezért a **Következő szám** és **Lejátszás / szünet** gomb továbbra
is a korábbi aktív lejátszási környezetet vezérelheti.

A megnyitott listáról válassz ki egy számot a Spotifyban. Ettől a playlist lesz
az aktív lejátszási környezet.

## 11. Playlist-borítók helyi tárolása

A sikeresen letöltött borítók helye:

```text
%LOCALAPPDATA%\LocalMediaControllers\spotify-playlist-cache
```

A cache csak képfájlokat tartalmaz; Spotify-jelszó, token vagy API-kulcs nem
kerül bele. A plugin JPEG, PNG és WebP képet fogad el, legfeljebb 2 MB méretben.

Ha egy playlist borítója megváltozott, de a régi kép maradt látható:

1. zárd be a Stream Deck alkalmazást;
2. töröld az adott playlisthez tartozó képfájlt a fenti cache-könyvtárból;
3. indítsd újra a Stream Decket;
4. nyisd meg a playlist-gomb beállításait, majd mentsd el újra a linket.

## 12. Hibajelzések és hibaelhárítás

### A plugin új verziója nem települ

Távolítsd el a korábbi verziót, indítsd újra a Stream Deck alkalmazást, majd
telepítsd az új `.streamDeckPlugin` fájlt.

### Nem látható a „Plugin nyelve” mező

Valószínűleg egy korábbi pluginverzió fut. Ellenőrizd, hogy a 0.6.0 vagy újabb
verzió van telepítve, majd indítsd újra a Stream Deck alkalmazást.

### A gomb „Nincs Spotify” állapotot mutat

- Indítsd el a Spotify Desktop alkalmazást.
- Indíts el kézzel egy számot, hogy létrejöjjön a Windows médiamunkamenet.
- Ha több Spotify-verzió vagy munkamenet fut egyszerre, zárd be a feleslegeset.
- Indítsd újra a Spotify-t, majd szükség esetén a Stream Deck alkalmazást.

### A hangerőgomb „Nincs hang” állapotot mutat

- Indíts el kézzel egy számot, hogy létrejöjjön a Spotify hangmunkamenete.
- Ellenőrizd, hogy a Spotify az alapértelmezett multimédiás kimeneten szól-e.
- Az egyedi alkalmazás-kimeneti átirányítás bizonyos konfigurációkban nem
  támogatott.

### A playlist megnyílik, de a Következő gomb a régi sorban lép

Ez a tervezett működés. A playlist megnyitása navigáció, nem queue-váltás.
Válassz ki kézzel egy számot a megnyitott listáról.

### Nem jelenik meg a playlist borítója

- Ellenőrizd az internetkapcsolatot.
- Használj teljes `open.spotify.com/playlist/...` linket vagy Spotify URI-t.
- Ellenőrizd, hogy a lista elérhető-e a Spotifyban.
- Mentsd el újra a playlist beállítását.
- Hiba esetén a gomb továbbra is használható az alapértelmezett ikonnal.

### Az actionlista és a Property Inspector más nyelven jelenik meg

Az actionlista nyelvét a Stream Deck alkalmazás, a panel és a dinamikus
gombfeliratok nyelvét pedig a plugin saját nyelvválasztója kezeli. Magyar és
olasz host-lokalizáció hiányában a két felület nyelve eltérhet.

## 13. Adatvédelem és biztonság

- A lejátszásvezérlés nem használ Spotify Web API-t vagy OAuthot.
- A plugin nem kér és nem tárol Spotify-jelszót.
- Nem küld globális médiabillentyűt, és nem vezérel automatikusan másik
  médialejátszót.
- A Spotify-munkamenetet az alkalmazásazonosító alapján választja ki.
- A playlist-linket a plugin és a natív bridge is ellenőrzi.
- A név és borító kizárólag a Spotify nyilvános oEmbed szolgáltatásából, illetve
  engedélyezett Spotify-képkiszolgálóról tölthető le.
- A TLS-tanúsítványok ellenőrzése nincs kikapcsolva.

## 14. Eltávolítás

1. Nyisd meg a Stream Deck alkalmazás pluginbeállításait.
2. Távolítsd el a **Spotify Local Controller** plugint.
3. Ha a gyorsítótárazott playlist-borítókat is törölni szeretnéd, kézzel
   eltávolíthatod ezt a könyvtárat:

```text
%LOCALAPPDATA%\LocalMediaControllers\spotify-playlist-cache
```

Az eltávolítás nem módosítja a Spotify vagy a Windows hangbeállításait.

## 15. Gyors ellenőrzőlista

- [ ] A Spotify elindul a Stream Deck gombról.
- [ ] A Play/Pause ikon követi a tényleges állapotot.
- [ ] Az előző és következő gomb csak a Spotify-t vezérli.
- [ ] A hangerőgombok csak a Spotify hangerejét módosítják.
- [ ] A némítás visszakapcsolásakor megmarad a korábbi hangerő.
- [ ] A lejátszási mód végigvált a három támogatott állapoton.
- [ ] A playlist-gomb a megfelelő listát nyitja meg.
- [ ] A playlist neve és borítója automatikusan megjelenik.
- [ ] Az egyéni playlist-felirat felülírja az automatikus nevet.
- [ ] A plugin nyelve magyarra állítható és újraindítás után megmarad.

