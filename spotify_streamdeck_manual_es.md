# Spotify Local Controller – Manual de usuario

**Creado y probado por:** Cyb3r ([cyber-suli.hu](https://cyber-suli.hu)), con la ayuda de [OpenAI Codex](https://developers.openai.com/learn/codex).

**Versión:** 1.0.0  
**Plataforma:** Windows 10/11 y Elgato Stream Deck 7.1 o posterior  
**Idioma:** español

## 1. Descripción general

Spotify Local Controller es un plugin local de Stream Deck para Spotify
Desktop. La reproducción usa Windows GSMTC y el volumen se aplica a la sesión de
audio de Spotify. No requiere cuenta de desarrollador, clave API, OAuth,
servicio en segundo plano, permisos de administrador ni instalaciones separadas
de Node.js o .NET.

Internet solo es necesario para descargar por primera vez el nombre y la
portada de una lista.

## 2. Requisitos

- Windows 10 1809 o posterior, o Windows 11;
- Stream Deck 7.1 o posterior;
- dispositivo Stream Deck compatible con Keypad;
- Spotify Desktop instalado.

## 3. Instalación y actualización

Abre `com.localmediacontrollers.spotify.streamDeckPlugin` y acepta la
instalación. Si una versión de desarrollo anterior impide actualizar, elimina
el plugin antiguo, reinicia completamente Stream Deck e instala el paquete
nuevo. El plugin no instala perfiles ni reorganiza los botones.

## 4. Añadir acciones

Busca **Spotify Local Controller** en Stream Deck y arrastra las acciones a
teclas libres. Selecciona una tecla para abrir su Property Inspector. Una acción
puede usarse varias veces; cada tecla de lista puede guardar una lista diferente.

## 5. Idioma del plugin

Selecciona una acción de Spotify y elige **Idioma del plugin** en la parte
superior del Property Inspector. Se admiten húngaro, inglés, alemán, francés,
español, italiano y chino simplificado. La selección es global y permanece tras
reiniciar.

Stream Deck no publica oficialmente códigos de host para húngaro e italiano.
Por ello, la lista de acciones puede seguir el idioma del host mientras que los
paneles y textos dinámicos usan el idioma del plugin.

## 6. Acciones

| Acción | Función | Nota |
|---|---|---|
| **Abrir Spotify** | Inicia Spotify. | No inicia la reproducción. |
| **Abrir lista** | Abre la lista configurada. | No reemplaza la cola activa. |
| **Canción anterior/siguiente** | Se mueve por la cola activa. | Solo controla una sesión Spotify inequívoca. |
| **Reproducir / pausar** | Alterna la reproducción. | El icono sigue el estado real. |
| **Reproduciendo ahora** | Muestra título y artista. | Indica si faltan metadatos. |
| **Bajar/subir volumen** | Cambia solo Spotify. | Paso configurable de 1–50 %. |
| **Silenciar Spotify** | Activa/desactiva el silencio. | Conserva el volumen anterior. |
| **Modo de reproducción** | Orden, repetir canción y aleatorio. | Muestra el estado informado por Spotify. |

## 7. Estados de reproducción

- **Icono Play:** Spotify está en pausa o detenido.
- **Icono Pause:** Spotify está reproduciendo.
- **Icono verde oscuro propio de la acción:** no hay una sesión Spotify fiable.

Cada control de reproducción utiliza su propio icono oscuro. El botón de inicio
permanece verde; el botón de playlist conserva su portada o el icono normal de
lista porque no depende de la sesión multimedia activa.

### 7.1 Apariencia de los botones sin Spotify en ejecución

Si Spotify no está en ejecución o todavía no ha creado una sesión Windows GSMTC
controlable, los botones se muestran así:

| Botón | Apariencia sin Spotify |
|---|---|
| **Iniciar Spotify** | Icono verde normal y resaltado de Spotify; sigue disponible. |
| **Abrir playlist** | Conserva la portada descargada o, sin portada, el icono normal de playlist. |
| **Pista anterior** | Icono anterior verde oscuro. |
| **Reproducir / pausa** | Icono Play verde oscuro; no muestra un Pause engañoso. |
| **Pista siguiente** | Icono siguiente verde oscuro. |
| **Reproducción actual** | Icono de información verde oscuro. |
| **Bajar / subir volumen** | El icono de volumen verde oscuro correspondiente. |
| **Silenciar** | Icono de altavoz verde oscuro sin tachar. |
| **Modo de reproducción** | Icono de reproducción secuencial verde oscuro. |

Los botones dependientes de la sesión muestran **Sin Spotify**. Cuando Spotify
se inicia y aparece una sesión activa, vuelven automáticamente a su estado real
resaltado; no es necesario volver a colocarlos.

## 8. Volumen de Spotify

Selecciona una acción normal, introduce un entero de 1 a 50 en **Paso de
volumen (%)** y guárdalo. El valor predeterminado es 5 %. Solo cambia la sesión
de Spotify; no modifica el volumen principal de Windows ni otras aplicaciones.

## 9. Modo de reproducción

Cada pulsación cambia: en orden → repetir canción actual → aleatorio → en orden.
Si Spotify no ofrece repetición y aleatorio mediante GSMTC, la tecla muestra
**No compatible**.

## 10. Crear una tecla de lista

En Spotify, haz clic derecho en la lista y selecciona **Compartir → Copiar
enlace**. Mantén Alt para copiar un URI. Se admiten:

- `https://open.spotify.com/playlist/...`
- `spotify:playlist:...`

Se rechazan enlaces cortos `spotify.link` y URL ajenas.

1. Coloca **Abrir lista**.
2. Pega el enlace o URI.
3. Deja vacío el título personalizado para usar el nombre de Spotify, o escribe
   hasta 18 caracteres.
4. Pulsa **Guardar**.

El plugin descarga nombre y portada, usa la portada como imagen de la tecla y la
guarda en caché local. No necesita clave API ni inicio de sesión adicional. Si
falla, se mantienen el icono predeterminado y el título manual.

### Limitación de la cola

La tecla solo navega hasta la página de la lista. No reemplaza la cola activa de
Spotify. Selecciona una canción de la lista abierta para convertirla en el
contexto de reproducción activo.

## 11. Caché local de portadas

```text
%LOCALAPPDATA%\LocalMediaControllers\spotify-playlist-cache
```

La caché contiene únicamente imágenes JPEG, PNG o WebP de hasta 2 MB; nunca
contraseñas, tokens ni claves API. Para renovar una portada, cierra Stream Deck,
elimina la imagen correspondiente, reinicia y guarda de nuevo la lista.

## 12. Solución de problemas

- **Falla la instalación:** elimina el plugin anterior, reinicia Stream Deck e
  instala el paquete nuevo.
- **Falta el selector de idioma:** instala la versión 0.6.0 o posterior y reinicia.
- **«Sin Spotify»:** inicia Spotify y reproduce manualmente una canción una vez;
  cierra instancias duplicadas.
- **«Sin audio»:** reproduce una canción y comprueba la salida multimedia
  predeterminada.
- **La lista se abre pero Siguiente usa la cola antigua:** es normal; selecciona
  una canción de la lista abierta.
- **Falta la portada:** comprueba Internet, el enlace completo y el acceso a la
  lista; después vuelve a guardar.

## 13. Privacidad y seguridad

La reproducción no usa Spotify Web API ni OAuth. No se solicita ni almacena la
contraseña de Spotify. El plugin no envía teclas multimedia globales ni controla
otro reproductor como alternativa. Las referencias se validan dos veces; los
metadatos solo proceden de Spotify oEmbed y servidores de imágenes autorizados.
La verificación TLS permanece activa.

## 14. Desinstalación

Elimina **Spotify Local Controller** desde los ajustes de plugins de Stream
Deck. Opcionalmente elimina la carpeta de caché indicada. No se cambia ninguna
configuración de audio de Spotify o Windows.

## 15. Lista de comprobación

- [ ] Spotify se abre desde la tecla.
- [ ] Reproducir/Pausar y el modo reflejan el estado real.
- [ ] Volumen y silencio solo afectan a Spotify.
- [ ] La lista, el nombre y la portada son correctos.
- [ ] El título personalizado sustituye al automático.
- [ ] El idioma se conserva tras reiniciar.

