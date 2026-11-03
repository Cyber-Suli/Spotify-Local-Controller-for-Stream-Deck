# Spotify Local Controller – Manuale utente

**Creato e testato da:** Cyb3r ([cyber-suli.hu](https://cyber-suli.hu)), con l’aiuto di [OpenAI Codex](https://developers.openai.com/learn/codex).

**Versione:** 1.0.0  
**Piattaforma:** Windows 10/11 ed Elgato Stream Deck 7.1 o versione successiva  
**Lingua:** italiano

## 1. Panoramica

Spotify Local Controller è un plugin locale per Stream Deck dedicato a Spotify
Desktop. I comandi di riproduzione usano Windows GSMTC, mentre il volume agisce
sulla sessione audio Windows di Spotify. Non servono account sviluppatore,
chiavi API, OAuth, servizi in background, privilegi amministrativi o
installazioni separate di Node.js o .NET.

Internet è necessario solo per il primo download del nome e della copertina di
una playlist.

## 2. Requisiti

- Windows 10 1809 o successivo, oppure Windows 11;
- Stream Deck 7.1 o successivo;
- dispositivo Stream Deck compatibile con Keypad;
- Spotify Desktop installato.

## 3. Installazione e aggiornamento

Apri `com.localmediacontrollers.spotify.streamDeckPlugin` e conferma
l’installazione. Se una vecchia versione di sviluppo impedisce l’aggiornamento,
rimuovila, riavvia completamente Stream Deck e installa il nuovo pacchetto. Il
plugin non installa profili e non riordina i tasti.

## 4. Aggiunta delle azioni

Trova **Spotify Local Controller** nell’elenco azioni di Stream Deck e trascina
le azioni sui tasti liberi. Seleziona un tasto per aprire il Property Inspector.
La stessa azione può essere usata più volte; ogni tasto playlist può contenere
una lista diversa.

## 5. Lingua del plugin

Seleziona un’azione Spotify e scegli **Lingua del plugin** in alto nel Property
Inspector. Sono disponibili ungherese, inglese, tedesco, francese, spagnolo,
italiano e cinese semplificato. La scelta globale rimane dopo il riavvio.

Stream Deck non espone ufficialmente codici host per ungherese e italiano.
L’elenco azioni può quindi seguire la lingua dell’app, mentre pannelli e testi
dinamici usano la lingua del plugin.

## 6. Azioni

| Azione | Funzione | Nota |
|---|---|---|
| **Avvia Spotify** | Apre Spotify. | Non avvia la riproduzione. |
| **Apri playlist** | Apre la playlist configurata. | Non sostituisce la coda attiva. |
| **Brano precedente/successivo** | Si sposta nella coda attiva. | Controlla solo una sessione Spotify univoca. |
| **Riproduci / pausa** | Alterna la riproduzione. | L’icona segue lo stato reale. |
| **In riproduzione** | Mostra titolo e artista. | Segnala metadati mancanti. |
| **Volume Spotify giù/su** | Modifica solo Spotify. | Incremento 1–50%. |
| **Disattiva audio Spotify** | Attiva/disattiva l’audio. | Mantiene il livello precedente. |
| **Modalità di riproduzione** | Ordine, ripeti brano, casuale. | Mostra lo stato riferito da Spotify. |

## 7. Stati Riproduci / pausa

- **Icona Play:** Spotify è in pausa o arrestato.
- **Icona Pause:** Spotify è in riproduzione.
- **Icona verde scuro specifica dell’azione:** non è disponibile una sessione
  Spotify affidabile.

Ogni controllo di riproduzione usa la propria icona scura. Il tasto di avvio
rimane verde; il tasto playlist conserva la copertina o la normale icona elenco,
perché non dipende dalla sessione multimediale attiva.

### 7.1 Aspetto dei tasti senza Spotify in esecuzione

Se Spotify non è in esecuzione o non ha ancora creato una sessione Windows
GSMTC controllabile, i tasti appaiono così:

| Tasto | Aspetto senza Spotify |
|---|---|
| **Avvia Spotify** | Normale icona Spotify verde evidenziata; rimane utilizzabile. |
| **Apri playlist** | Mantiene la copertina scaricata o, senza copertina, la normale icona playlist. |
| **Brano precedente** | Icona precedente verde scuro. |
| **Riproduci / pausa** | Icona Play verde scuro; non mostra un Pause ingannevole. |
| **Brano successivo** | Icona successivo verde scuro. |
| **Brano attuale** | Icona informativa verde scuro. |
| **Volume − / +** | La rispettiva icona del volume verde scuro. |
| **Muto** | Icona altoparlante verde scuro non barrata. |
| **Modalità di riproduzione** | Icona di riproduzione sequenziale verde scuro. |

I tasti dipendenti dalla sessione mostrano **Spotify assente**. Quando Spotify
si avvia e compare una sessione attiva, tornano automaticamente al loro stato
reale evidenziato, senza doverli aggiungere di nuovo.

## 8. Volume di Spotify

Seleziona un’azione normale, inserisci un intero da 1 a 50 in **Incremento
volume (%)** e salva. Il valore predefinito è 5%. Viene modificata solo la
sessione di Spotify, non il volume principale di Windows o altre app.

## 9. Modalità di riproduzione

Ogni pressione passa tra: ordine → ripeti brano corrente → casuale → ordine. Se
Spotify non espone ripetizione e casuale tramite GSMTC, il tasto mostra **Non
supportato**.

## 10. Creazione di un tasto playlist

In Spotify fai clic destro sulla lista e scegli **Condividi → Copia link**.
Tieni premuto Alt per copiare un URI. Formati supportati:

- `https://open.spotify.com/playlist/...`
- `spotify:playlist:...`

I link brevi `spotify.link` e gli URL esterni vengono rifiutati.

1. Posiziona **Apri playlist**.
2. Incolla link o URI.
3. Lascia vuoto il titolo personalizzato per usare il nome Spotify, oppure
   inserisci fino a 18 caratteri.
4. Premi **Salva**.

Il plugin scarica nome e copertina, assegna l’immagine al tasto e la memorizza
localmente. Non servono chiavi API o accessi aggiuntivi. In caso di errore
restano disponibili l’icona predefinita e il titolo manuale.

### Limite della coda

Il tasto apre soltanto la pagina della playlist e non sostituisce la coda attiva
di Spotify. Seleziona un brano dalla lista aperta per renderla il contesto di
riproduzione attivo.

## 11. Cache locale delle copertine

```text
%LOCALAPPDATA%\LocalMediaControllers\spotify-playlist-cache
```

La cache contiene solo immagini JPEG, PNG o WebP fino a 2 MB, mai password,
token o chiavi API. Per aggiornare una copertina, chiudi Stream Deck, elimina
l’immagine interessata, riavvia e salva nuovamente la playlist.

## 12. Risoluzione dei problemi

- **Installazione non riuscita:** rimuovi il vecchio plugin, riavvia Stream Deck
  e installa il nuovo pacchetto.
- **Lingua assente:** installa la versione 0.6.0 o successiva e riavvia.
- **“Spotify assente”:** avvia Spotify e riproduci manualmente un brano una
  volta; chiudi eventuali istanze duplicate.
- **“Nessun audio”:** riproduci un brano e verifica l’uscita multimediale
  predefinita.
- **La playlist si apre ma Successivo usa la vecchia coda:** è previsto;
  seleziona un brano dalla lista aperta.
- **Copertina assente:** verifica Internet, il link completo e l’accessibilità
  della playlist, quindi salva di nuovo.

## 13. Privacy e sicurezza

La riproduzione non usa Spotify Web API o OAuth. Non vengono richieste o salvate
password Spotify. Il plugin non invia tasti multimediali globali e non controlla
altri player come ripiego. I riferimenti playlist vengono validati due volte; i
metadati arrivano solo da Spotify oEmbed e host immagini autorizzati. La verifica
TLS rimane attiva.

## 14. Disinstallazione

Rimuovi **Spotify Local Controller** dalle impostazioni plugin di Stream Deck.
Puoi anche eliminare la cartella cache indicata. Nessuna impostazione audio di
Spotify o Windows viene modificata.

## 15. Controllo rapido

- [ ] Spotify si apre dal tasto.
- [ ] Riproduci/Pausa e la modalità riflettono lo stato reale.
- [ ] Volume e muto riguardano solo Spotify.
- [ ] Playlist, nome e copertina sono corretti.
- [ ] Il titolo personalizzato sostituisce quello automatico.
- [ ] La lingua rimane selezionata dopo il riavvio.

