# ASUS ROG Strix laptop keyboard (SignalRGB)

Plugin de SignalRGB para el teclado de la laptop ASUS ROG Strix (USB `0B05:19B6`), más una copia del plugin
oficial `ASUS_Multidevice_Controller.js` **sin** la entrada `0x19B6`, para que no le quite el teclado.

## El problema
El plugin oficial `ASUS_Multidevice_Controller.js` (que no funciona con este teclado) también declara `0x19B6`.
SignalRGB lo **descarga en cada arranque** a
`%LOCALAPPDATA%\WhirlwindFX\SignalRgb\cache\plugin_cdn\main\Plugins\Asus\`, así que borrarlo de la carpeta de la
app no sirve: vuelve y se queda con el teclado.

Orden en que SignalRGB carga los plugins (para el mismo nombre de archivo gana el último):

1. carpeta de la app (`%LOCALAPPDATA%\VortxEngine\app-x.y.z\Signal-x64\Plugins`)
2. Add-ons (`%LOCALAPPDATA%\WhirlwindFX\SignalRgb\cache\addons`)
3. plugins oficiales descargados (`...\cache\plugin_cdn`)
4. **carpeta de usuario `Plugins`** ← gana

## Instalación (la que funciona)
Copiar `Asus_Strix_Laptop.js` y `ASUS_Multidevice_Controller.js` a la carpeta **Plugins** de la carpeta de
usuario de SignalRGB, y reiniciar SignalRGB.

- La carpeta de usuario está en el registro: `HKCU\Software\WhirlwindFX\SignalRgb` → `UserDirectory`.
  En la ROG es `C:\Users\ferna\OneDrive\ENTN\Fotos de página principal\Documentos2\WhirlwindFX\Plugins`.
- En el registro de SignalRGB debe salir `Custom Plugin File Loaded for Path: …/Plugins/Asus_Strix_Laptop.js`,
  y en Devices → ROG Strix → Inspector: `plugin Asus_Strix_Laptop.js`, `origin User`.

Como Add-on **no** basta: los plugins descargados del CDN le ganan a los Add-ons.

## Mantenimiento
La copia de `ASUS_Multidevice_Controller.js` no se actualiza sola (es la del CDN del 22 oct 2026). Si algún
otro aparato ASUS lo necesita actualizado: copiar el del CDN, quitar la línea `0x19B6: "Aura device",` y
reemplazarlo en la carpeta Plugins de usuario.

Basado en el plugin "ROG Strix Scar (2022)" y en `ASUS_Multidevice_Controller.js`, ambos de WhirlwindFX.
