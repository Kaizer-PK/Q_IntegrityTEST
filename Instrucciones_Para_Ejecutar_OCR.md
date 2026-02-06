# Instrucciones OCR para `demoV3` (Windows)

Estas instrucciones permiten instalar las dependencias necesarias para que la nueva funcionalidad PDF/OCR en `app.py` funcione correctamente.

## Requisitos del sistema (Windows)
- Python 3.8+ (preferible 3.10+)
- Administrador (para instalación de binarios opcionales)

## Paquetes Python (virtualenv/venv recomendado)
Abrir un terminal (PowerShell) en la carpeta del proyecto y ejecutar:

```powershell
python -m pip install --upgrade pip
pip install PyMuPDF pdf2image pytesseract ocrmypdf langdetect
# Opcionales útiles:
pip install pillow
```

## Binarios del sistema (requeridos/alt)
- Tesseract OCR
  - Recomendado: usar Chocolatey:
    ```powershell
    choco install -y tesseract
    ```
  - Alternativa: descargar desde: https://github.com/tesseract-ocr/tesseract
  - Asegúrate de tener los datos de idioma `spa` (normalmente vienen con la instalación de choco).

- Poppler (necesario para `pdf2image` en Windows)
  - Con Chocolatey:
    ```powershell
    choco install -y poppler
    ```
  - O descargar binarios y añadir la carpeta `bin` a la variable de entorno `PATH`.

- (Opcional) ocrmypdf
  - Requiere dependencias (qpdf, ghostscript). Si prefieres usar `ocrmypdf`:
    ```powershell
    pip install ocrmypdf
    choco install -y qpdf
    choco install -y ghostscript
    ```

## Variables de entorno útiles
- `POPPLER_PATH` (si instalaste Poppler en una ruta no incluida en PATH): ruta a la carpeta `bin` de Poppler, por ejemplo "C:\\Program Files\\poppler-xx\\bin".
- `TESSERACT_CMD` (si `tesseract` no está en PATH): ruta completa al ejecutable `tesseract.exe`.

Puedes exportarlas en PowerShell:

```powershell
setx POPPLER_PATH "C:\\Program Files\\poppler-23.05.0\\Library\\bin"
setx TESSERACT_CMD "C:\\Program Files\\Tesseract-OCR\\tesseract.exe"
```

> Cierra y vuelve a abrir la terminal para que los cambios a `setx` surtan efecto.

## Verificaciones rápidas
- Verificar Tesseract:
  ```powershell
  tesseract --version
  ```
- Verificar Poppler (ejemplo `pdftoppm`):
  ```powershell
  pdftoppm -v
  ```

## Notas
- El resultado del OCR se cachea en un archivo lateral `archivo.pdf.ocr.txt` en el mismo directorio para acelerar re-procesos.



