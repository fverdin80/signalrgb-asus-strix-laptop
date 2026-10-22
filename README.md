# ASUS ROG Strix laptop keyboard (SignalRGB add-on)

[![Add To Installation](https://marketplace.signalrgb.com/resources/add-extension-256.png 'Add to My SignalRGB Installation')](signalrgb://addon/install?url=https://github.com/fverdin80/signalrgb-asus-strix-laptop)

Plugin de SignalRGB para el teclado de la laptop ASUS ROG Strix (USB `0B05:19B6`).

Se instala como **Add-on** a propósito: SignalRGB carga los plugins en este orden
(el último gana para el mismo VID:PID):

1. carpeta de la app (`%LOCALAPPDATA%\VortxEngine\app-x.y.z\Signal-x64\Plugins`)
2. plugins oficiales descargados (`%LOCALAPPDATA%\WhirlwindFX\SignalRgb\cache\plugin_cdn`)
3. **Add-ons** (`%LOCALAPPDATA%\WhirlwindFX\SignalRgb\cache\addons`)

El plugin oficial `ASUS_Multidevice_Controller.js` (que no funciona con este teclado) declara el mismo
`0x19B6` y se vuelve a descargar en cada arranque, así que borrarlo de la carpeta de la app no sirve.
Como Add-on, este plugin se carga al final y se queda con el teclado.

## Instalar
Clic en el botón de arriba (o abrir `signalrgb://addon/install?url=https://github.com/fverdin80/signalrgb-asus-strix-laptop`)
y aceptar en SignalRGB.

Basado en el plugin "ROG Strix Scar (2022)" de WhirlwindFX.

## ASUS_Multidevice_Controller.js (copia modificada)
El plugin oficial se procesa después de este y se queda con `0x19B6`. Para evitarlo, este Add-on incluye una
copia del oficial **con el mismo nombre** (los Add-ons sustituyen archivos con el mismo nombre) y **sin** la
entrada `0x19B6: "Aura device"`. Todo lo demás es idéntico a la versión del CDN del 22 oct 2026.

Contra: esa copia ya no se actualiza sola. Para actualizarla, copiar de nuevo
`%LOCALAPPDATA%\WhirlwindFX\SignalRgb\cache\plugin_cdn\main\Plugins\Asus\ASUS_Multidevice_Controller.js`,
quitar la línea `0x19B6: "Aura device",` y hacer push.
