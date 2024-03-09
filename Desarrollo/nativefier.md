# Nativefier
## Descripción
Este software permite convertir una aplicación web alojada bajo un dominio en una aplicación de escritorio nativa. Esta capacidad proporciona una experiencia similar a una aplicación nativa mientras se mantiene la flexibilidad y el alcance de una aplicación web.

Además, se detalla cómo configurar un "Launcher" en Ubuntu, lo que permite un acceso rápido y fácil a la aplicación de escritorio nativa directamente desde el sistema operativo.

## Requisitos previos

Antes de proceder, asegúrate de tener instalados npm y Node.js en tu sistema. Estos son requisitos indispensables para ejecutar el proceso de empaquetado de la aplicación web PHP en una aplicación de escritorio.

## Instalación

```bash
npm install nativefier -g
```
## Uso
#### Ejecución del comando en el directorio de destino
Asegúrate de ejecutar el comando en el directorio donde deseas que se genere la carpeta con la aplicación. Esto garantizará que la aplicación se coloque en la ubicación deseada y facilitará su acceso y gestión posterior.
```bash
nativefier --name "NombreDeTuApp" "https://tudominio.com/tuaplicacion.php"
```
#### Añadir una entrada para el lanzador en Ubuntu
Después de completar la generación de la carpeta con la aplicación, es recomendable añadir una entrada para el lanzador si estás utilizando Ubuntu. Esto facilitará el acceso rápido a la aplicación desde el lanzador de aplicaciones.
```bash
cd ~/.local/share/applications/
```

#### Crear un archivo .desktop para el lanzador

Una vez completado, crea un archivo llamado `nombre_de_la_app.desktop` para configurar el lanzador según tus necesidades específicas. Este archivo proporciona detalles sobre cómo se mostrará la aplicación en el lanzador de aplicaciones y puede personalizarse según tus preferencias.
```bash
[Desktop Entry]
Version=1.0
Type=Application
Name=GitHub
GenericName=GitHub
Comment=Open GitHub in web browser
Exec=xdg-open https://github.com
Icon=github-icon
Terminal=false
Categories=Network;WebBrowser;
MimeType=x-scheme-handler/http;x-scheme-handler/https;
```