# Spotify Local Controller – Manuel utilisateur

**Créé et testé par :** Cyb3r ([cyber-suli.hu](https://cyber-suli.hu)), avec l’aide d’[OpenAI Codex](https://developers.openai.com/learn/codex).

**Version :** 1.0.0  
**Plateforme :** Windows 10/11 et Elgato Stream Deck 7.1 ou version ultérieure  
**Langue :** français

## 1. Présentation

Spotify Local Controller est un plugin Stream Deck local destiné à l’application
Spotify pour ordinateur. La lecture utilise Windows GSMTC et le volume cible la
session audio Windows propre à Spotify. Aucun compte développeur, clé API,
OAuth, service en arrière-plan, droit administrateur, ni installation séparée
de Node.js ou .NET n’est nécessaire.

Internet n’est requis que lors du premier téléchargement du nom et de la
pochette d’une playlist.

## 2. Configuration requise

- Windows 10 1809 ou ultérieur, ou Windows 11 ;
- Stream Deck 7.1 ou ultérieur ;
- appareil Stream Deck compatible Keypad ;
- application Spotify Desktop installée.

## 3. Installation et mise à jour

Ouvrez `com.localmediacontrollers.spotify.streamDeckPlugin`, puis acceptez
l’installation. Si une ancienne version de développement bloque la mise à jour,
supprimez-la, redémarrez complètement Stream Deck et installez le nouveau
paquet. Le plugin n’installe aucun profil et ne déplace aucun bouton.

## 4. Ajout des actions

Dans Stream Deck, trouvez **Spotify Local Controller**, puis faites glisser les
actions sur des touches libres. Sélectionnez une touche pour afficher son
Property Inspector. Une action peut être utilisée plusieurs fois ; chaque
touche de playlist peut contenir une liste différente.

## 5. Langue du plugin

Sélectionnez une action Spotify, puis choisissez la **Langue du plugin** en haut
du Property Inspector. Langues disponibles : hongrois, anglais, allemand,
français, espagnol, italien et chinois simplifié. Ce choix global est conservé
après le redémarrage.

Stream Deck ne fournit pas officiellement de codes hôtes hongrois et italien.
La liste des actions peut donc suivre la langue de Stream Deck, tandis que les
panels et libellés dynamiques suivent la langue du plugin.

## 6. Actions

| Action | Fonction | Remarque |
|---|---|---|
| **Lancer Spotify** | Ouvre Spotify. | Ne lance pas la lecture. |
| **Ouvrir une playlist** | Ouvre la playlist configurée. | Ne remplace pas la file active. |
| **Titre précédent/suivant** | Se déplace dans la file Spotify active. | Cible uniquement une session Spotify non ambiguë. |
| **Lecture / pause** | Bascule la lecture. | L’icône suit l’état réel. |
| **Lecture en cours** | Affiche le titre et l’artiste. | Signale les métadonnées absentes. |
| **Baisser/augmenter Spotify** | Modifie uniquement le volume de Spotify. | Pas réglable de 1 à 50 %. |
| **Couper Spotify** | Active/désactive le son. | Conserve le niveau précédent. |
| **Mode de lecture** | Ordre, répétition du titre, aléatoire. | Affiche l’état renvoyé par Spotify. |

## 7. États Lecture / pause

- **Icône Play :** Spotify est en pause ou arrêté.
- **Icône Pause :** Spotify est en lecture.
- **Icône vert foncé propre à l’action :** aucune session Spotify fiable n’est
  disponible.

Chaque commande de lecture utilise sa propre icône sombre. La touche de
lancement reste verte ; la touche playlist conserve sa pochette ou son icône de
liste normale, car elle ne dépend pas de la session multimédia active.

### 7.1 Apparence des touches lorsque Spotify ne fonctionne pas

Si l’application Spotify n’est pas lancée ou n’a pas encore créé de session
Windows GSMTC contrôlable, les touches apparaissent comme suit :

| Touche | Apparence sans Spotify |
|---|---|
| **Lancer Spotify** | Icône Spotify verte normale et mise en évidence ; reste utilisable. |
| **Ouvrir une playlist** | Conserve la pochette téléchargée ou, sans pochette, l’icône de playlist normale. |
| **Titre précédent** | Icône précédent vert foncé. |
| **Lecture / pause** | Icône Play vert foncé ; aucune icône Pause trompeuse. |
| **Titre suivant** | Icône suivant vert foncé. |
| **Lecture en cours** | Icône d’information vert foncé. |
| **Volume − / +** | Icône de volume vert foncé correspondante. |
| **Muet** | Icône de haut-parleur vert foncé non barrée. |
| **Mode de lecture** | Icône de lecture séquentielle vert foncé. |

Les touches dépendantes de la session affichent **Spotify absent**. Dès que
Spotify démarre et qu’une session active apparaît, elles reprennent
automatiquement leur état réel mis en évidence, sans devoir les recréer.

## 8. Volume de Spotify

Sélectionnez une action Spotify standard, saisissez un entier de 1 à 50 dans
**Pas de volume (%)**, puis enregistrez. La valeur par défaut est 5 %. Seule la
session audio de Spotify change ; le volume principal de Windows et les autres
applications ne sont pas affectés.

## 9. Mode de lecture

Chaque pression alterne : ordre → répétition du titre actuel → aléatoire →
ordre. Si Spotify n’expose pas ces commandes via GSMTC, la touche indique
**Non compatible** au lieu d’annoncer un faux succès.

## 10. Création d’une touche de playlist

Dans Spotify, faites un clic droit sur la liste puis **Partager → Copier le
lien**. Maintenez Alt pour copier un URI Spotify. Formats acceptés :

- `https://open.spotify.com/playlist/...`
- `spotify:playlist:...`

Les liens courts `spotify.link` et les URL externes sont refusés.

1. Placez l’action **Ouvrir une playlist**.
2. Collez le lien ou l’URI.
3. Laissez le titre personnalisé vide pour utiliser le nom Spotify, ou saisissez
   jusqu’à 18 caractères.
4. Cliquez sur **Enregistrer**.

Le plugin récupère le nom et la pochette, applique l’image à la touche et la met
en cache localement. Aucune clé API ni connexion supplémentaire n’est requise.
En cas d’échec, l’icône standard et le titre manuel restent disponibles.

### Limitation de la file

La touche ouvre uniquement la page de la playlist. Elle ne remplace pas la file
Spotify active. Sélectionnez un titre dans la liste ouverte pour en faire le
contexte de lecture actif.

## 11. Cache local des pochettes

```text
%LOCALAPPDATA%\LocalMediaControllers\spotify-playlist-cache
```

Le cache ne contient que des images JPEG, PNG ou WebP de 2 Mo maximum, sans mot
de passe, jeton ou clé API. Pour actualiser une pochette, fermez Stream Deck,
supprimez l’image concernée, redémarrez puis enregistrez de nouveau la playlist.

## 12. Dépannage

- **Échec de l’installation :** supprimez l’ancienne version, redémarrez Stream
  Deck et installez le nouveau paquet.
- **Langue absente :** installez la version 0.6.0 ou ultérieure et redémarrez.
- **« Spotify absent » :** démarrez Spotify et lancez manuellement un titre une
  fois ; fermez les instances Spotify en double.
- **« Aucun son » :** lancez un titre et vérifiez la sortie multimédia par défaut.
- **La playlist s’ouvre mais Suivant utilise l’ancienne file :** comportement
  normal ; sélectionnez un titre de la playlist ouverte.
- **Pochette absente :** vérifiez Internet, le lien complet et l’accessibilité de
  la playlist, puis enregistrez de nouveau.

## 13. Confidentialité et sécurité

La lecture n’utilise ni Spotify Web API ni OAuth. Aucun mot de passe Spotify
n’est demandé ou stocké. Le plugin n’envoie pas de touches multimédias globales
et ne contrôle pas un autre lecteur en solution de secours. Les références de
playlist sont validées deux fois ; les métadonnées proviennent uniquement de
Spotify oEmbed et de serveurs d’images Spotify autorisés. TLS reste vérifié.

## 14. Désinstallation

Supprimez **Spotify Local Controller** dans les réglages des plugins Stream Deck.
Vous pouvez également supprimer le dossier de cache ci-dessus. Aucun réglage
audio de Spotify ou de Windows n’est modifié.

## 15. Vérification rapide

- [ ] Spotify s’ouvre depuis la touche.
- [ ] Lecture/Pause et le mode reflètent l’état réel.
- [ ] Volume et mode muet ne concernent que Spotify.
- [ ] La bonne playlist, son nom et sa pochette apparaissent.
- [ ] Le titre personnalisé remplace le nom automatique.
- [ ] La langue reste sélectionnée après redémarrage.

