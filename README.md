🚀 Instalador de aplicaciones para Windows (PowerShell + Chocolatey / winget)

Script interactivo en PowerShell para instalar y actualizar aplicaciones esenciales en Windows usando Chocolatey o winget, pensado para funcionar incluso en PowerShell 2.0 y ayudar a migrar suave hacia PowerShell 7.

Te muestra un menú cómodo en consola, con barra de progreso y logs en vivo mientras instala.

✨ Características principales

✅ Funciona desde PowerShell 2.0 (ideal para equipos viejos / recién formateados).

🧰 Soporta dos gestores de paquetes:

Chocolatey

winget

🧩 Catálogo de aplicaciones preconfiguradas, listas para instalar (navegador, utilidades, desarrollo, multimedia, gaming, runtimes .NET, etc.).

⚙️ Opción para instalar TODO el catálogo con un solo comando.

🎯 Opción para elegir solo algunas apps por número.

⬆️ Opción para actualizar todo lo ya instalado (upgrade masivo):

choco upgrade all -y

winget upgrade --all ...

🧪 Utilidad integrada para instalar/actualizar PowerShell 7 y:

Configurarlo como perfil predeterminado en Windows Terminal.

Crear/ajustar settings.json de Windows Terminal de forma segura (con respaldo .bak).

👮 Verificación de que se está ejecutando como Administrador.

📡 Ajuste de TLS para evitar problemas al descargar desde internet.

🖥️ Panel de progreso en la parte inferior de la consola, que muestra en vivo la salida de choco / winget.

🧱 Catálogo de aplicaciones incluidas

El arreglo $Apps incluye, entre otras:

🌐 Web / Nube

Google Chrome

Google Drive

💼 Comunicaciones / Productividad

Discord

TeamViewer

TeamSpeak

Thunderbird (ESR/estable según canal)

🎮 Gaming / Launchers / Monitoreo

Steam

EA app

MSI Afterburner

RivaTuner Statistics Server (RTSS)

🎧 Multimedia / Edición / Streaming

VLC media player

HandBrake

OBS Studio

REAPER (x64)

ImageMagick

FFmpeg

yt-dlp

💻 Desarrollo / Virtualización

Node.js LTS

Python 3.12 (x64)

PowerShell 7 (x64)

VirtualBox

Tesseract OCR

🧩 Runtimes / Sistema

7-Zip

.NET Framework 4.8

.NET Desktop Runtime 9 (x64)

.NET Desktop Runtime 8 (x64)

Puedes extender fácilmente el catálogo editando el arreglo $Apps en el script.

⚙️ Requisitos

🪟 Windows 10/11 (recomendado; algunas cosas funcionarán también en 7/8 con limitaciones).

📡 Conexión a internet para descargar paquetes.

👮 PowerShell ejecutado como Administrador.

Opcional pero recomendado:

Windows Terminal

Permitir ejecución de scripts en la sesión actual.

▶️ Cómo usarlo

Descarga el script en una carpeta, por ejemplo:
C:\Tools\instalador-apps.ps1

Abre PowerShell como Administrador:

Click derecho en el icono de PowerShell → “Ejecutar como administrador”.

(Opcional) Permite scripts en la sesión actual:

Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force


Ejecuta el script:

cd C:\Tools
.\instalador-apps.ps1


Verás primero algo como:

=====================================
  PowerShell actual : 5.1.x (Desktop)
=====================================


Si tu versión es muy vieja, el script te lo advierte y te ofrece actualizar.

🧭 Flujo del script

🔍 Detecta la versión de PowerShell (Mostrar-VersionPS).

👮 Verifica que seas Administrador (EsAdmin).

🔐 Ajusta protocolo TLS si hace falta.

📦 Te pide elegir un gestor:

==============r02====================
  Instalador de Aplicaciones (PS2.0)
=====================================

Elige el gestor de paquetes:
  1) Chocolatey
  2) winget
  0) Salir


Si el gestor elegido no está instalado:

Para Chocolatey, lo descarga y configura (Instalar-Choco).

Para winget, abre la Microsoft Store para instalar App Installer (Instalar-Winget).

Una vez listo el gestor, aparece el menú principal:

Gestor activo: choco
Acciones:
  1) Listar catálogo
  2) Instalar TODO el catálogo
  3) Instalar apps seleccionadas
  4) Actualizar TODO (ya instaladas)
  5) Actualizar PowerShell (7 recomendado / info 5.1)
  9) Cambiar de gestor
  0) Salir


Durante las instalaciones, se abre un panel de progreso en la parte inferior de la consola, donde se van escribiendo las salidas de choco / winget en tiempo real.

🧿 Actualización de PowerShell y Windows Terminal

La opción “Actualizar PowerShell (5)” del menú:

Si eliges instalar PowerShell 7:

Usa choco o winget según el gestor activo.

Llama a Set-WindowsTerminalDefaultPwsh para:

Buscar pwsh.exe.

Verificar que exista wt (Windows Terminal).

Leer o crear settings.json.

Crear o modificar un perfil "PowerShell 7".

Establecerlo como defaultProfile.

Generar respaldo de settings.json con timestamp.

Si eliges información sobre PowerShell 5.1:

Abre la página oficial de WMF 5.1 (https://aka.ms/wmf5download).

🔐 Notas de seguridad

Este script no descarga instaladores directamente; delega la descarga e instalación en Chocolatey o winget, que usan sus propias fuentes y validaciones.

Aun así, es buena práctica:

Revisar el catálogo $Apps.

Confirmar que los IDs (ChocoId, WingetId) correspondan a paquetes confiables.

Usarlo en entornos donde tengas control del equipo (no en producción sin pruebas).

🛠 Personalización

Añadir o quitar aplicaciones del catálogo modificando el arreglo $Apps.

Cambiar títulos y textos de los menús según tu estilo.

Ajustar la lógica de progreso o el alto del panel ($script:PaneHeight) si usas consolas más pequeñas.

✅ Pendientes / Ideas futuras

 Exportar un log a archivo con todo lo instalado / actualizado.

 Añadir categorías personalizadas por usuario.

 Integrar comprobaciones de versión antes de intentar instalar.

 Modo “silencioso” sin preguntas, para automatizar despliegues.
