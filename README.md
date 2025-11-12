# u22-resultados-bot
Este proyecto automatiza la detección de nuevos resultados de partidos U22 en la web de la FEB y envía una notificación directa a Telegram cuando hay actualizaciones.
Monitorización automática de resultados U22

Automatización con IA + Python + GitHub Actions + Telegram

La arquitectura se basa en tres pilares:

Python para el scraping y la lógica de detección de cambios.

GitHub Actions como orquestador en la nube (sin infraestructura ni coste).

Bot de Telegram como canal de alerta privado.

Con este flujo, el sistema revisa periódicamente las páginas de cada partido y envía un mensaje instantáneo cuando se publica un nuevo marcador o cambia un resultado anterior.

Arquitectura general:

GitHub Actions (cron)
      ↓
Python Script (main.py)
      ↓
BeautifulSoup + Regex
      ↓
Comparación con state.json
      ↓
Telegram Bot → Notificación en tu móvil

El proyecto combina scraping, persistencia de estado, y mensajería automatizada, todo bajo un flujo reproducible y mantenido en GitHub.
Razonamiento y objetivo:

El propósito no era “hacer un bot”, sino resolver un problema de seguimiento manual: cada jornada U22 implica revisar decenas de enlaces y pestañas. El valor de esta solución radica en:

Eficiencia: elimina vigilancia manual.

Escalabilidad: se adapta fácilmente a más partidos o ligas.

Reproducción: todo el flujo está versionado y documentado.

Costo cero: se ejecuta con infraestructura gratuita de GitHub.

Estructura de archivos:

| Archivo                               | Descripción                                                               |
| ------------------------------------- | ------------------------------------------------------------------------- |
| `main.py`                             | Script Python que consulta los enlaces y envía notificaciones a Telegram. |
| `partidos.json`                       | Lista de URLs a monitorizar (uno por partido).                            |
| `state.json`                          | Registro histórico del último estado detectado (autogenerado).            |
| `.github/workflows/check_results.yml` | Configuración de GitHub Actions (cron + ejecución periódica).             |
| `README.md`                           | Documentación del proyecto.                                               |
| `LICENSE`                             | Licencia MIT (libre uso con atribución).                                  |

Dependencias:
Python 3.10+

requests

beautifulsoup4

Instalación rápida local
pip install -r requirements.txt

Variables de entorno_:
Debes configurar en tu entorno (o en GitHub Secrets) los siguientes valores:

| Variable             | Descripción                                                  |
| -------------------- | ------------------------------------------------------------ |
| `TELEGRAM_BOT_TOKEN` | Token del bot creado con @BotFather                          |
| `TELEGRAM_CHAT_ID`   | ID del chat (usuario o grupo) donde se enviarán los mensajes |


