# Control Bienestar 2026

Sitio publicado: <https://felipepardobarrera.github.io/CONTROL-SALA-CUNA-Y-JARDIN/>

Segunda versión independiente del sistema web para controlar gasto real, presupuesto base y proyecciones de:

- Jardin infantil
- Sala cuna
- Monto directo sala cuna

La aplicación permite registrar facturas o resoluciones, cargar documentos PDF, administrar proveedores, revisar alertas, editar el presupuesto base mensual y construir escenarios futuros. Esta versión incorpora una navegación reorganizada, accesos rápidos y almacenamiento independiente del sistema original.

## Separación del sistema original

Este proyecto utiliza identificadores de almacenamiento y una base documental propios. Abrirlo en el mismo navegador que el sistema anterior no mezcla pagos, proveedores, proyecciones ni archivos PDF entre ambas aplicaciones.

## Requisitos

- Node.js 18 o superior
- Python 3, solo si se usara lectura automatica de PDF
- Paquete Python `pypdf`, solo si se usara lectura automatica de PDF

## Instalacion rapida

1. Clonar el repositorio:

```bash
git clone URL_DEL_REPOSITORIO
cd control-presupuestario-sala-cuna-jardin
```

2. Instalar dependencia de PDF, si corresponde:

```bash
pip install -r requirements.txt
```

3. Crear el archivo de datos inicial:

```bash
copy data\control-presupuestario.example.json data\control-presupuestario.json
```

En Linux o servidor no Windows:

```bash
cp data/control-presupuestario.example.json data/control-presupuestario.json
```

4. Iniciar el sistema:

```bash
npm start
```

5. Abrir en el navegador:

```text
http://127.0.0.1:8123/
```

Para compartir dentro de la red, usar la direccion que aparece en la consola, por ejemplo:

```text
http://IP_DEL_SERVIDOR:8123/
```

## Variables de configuracion

Opcionalmente se pueden configurar estas variables:

| Variable | Uso | Ejemplo |
| --- | --- | --- |
| `PORT` | Puerto donde se publica la aplicacion | `8123` |
| `PUBLIC_HOST` | IP o nombre visible para otros usuarios | `10.10.30.20` |
| `DATA_PATH` | Ruta del archivo central de datos | `D:\control\data.json` |
| `PYTHON_EXE` | Ruta de Python para leer PDF | `C:\Python312\python.exe` |
| `BACKUP_CSV_PATH` | Ruta opcional de respaldo CSV para restauracion | `D:\respaldos\control.csv` |

Ejemplo en PowerShell:

```powershell
$env:PORT="8123"
$env:PUBLIC_HOST="10.10.30.20"
$env:DATA_PATH="D:\control-presupuestario\control-presupuestario.json"
npm start
```

## Datos reales

La publicación incluye el presupuesto base, pero no contiene pagos, proveedores, datos personales ni archivos PDF del sistema anterior. La información operativa se incorpora desde la aplicación o mediante una importación autorizada en el servidor de uso.

Para respaldar los cambios posteriores, usar la opción de respaldo/exportación de la aplicación o copiar manualmente el archivo `data/control-presupuestario.json` en una ubicación segura.

## Estructura

```text
index.html       Pantalla principal
styles.css       Diseno visual
app.js           Logica del sistema en navegador
server.js        Servidor local/central
extract_pdfs.py  Lectura de texto desde PDF
data/            Datos compartidos del sistema
```

## Uso recomendado en servidor

1. Mantener el repositorio en una carpeta del servidor.
2. Configurar `DATA_PATH` apuntando a una carpeta con respaldo.
3. Ejecutar `npm start`.
4. Compartir a los usuarios el enlace `http://IP_DEL_SERVIDOR:8123/`.
5. Si se actualiza el codigo desde GitHub, reiniciar el servidor.
