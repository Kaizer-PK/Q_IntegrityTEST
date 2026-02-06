# Instrucciones mínimas: usar OCR en `demoV3` (Windows)

Pasos obligatorios para que la funcionalidad PDF→OCR de `app.py` funcione en otro equipo.

1) Crear y activar entorno virtual (recomendado):
   python -m venv .venv
   .\.venv\Scripts\activate

2) Instalar dependencias Python:
   python -m pip install --upgrade pip
   pip install PyMuPDF pdf2image pytesseract langdetect
   # (opcional) ocrmypdf: pip install ocrmypdf

3) Instalar binarios del sistema:
   - Tesseract OCR (debe disponer del idioma 'spa'). Verificar:
     tesseract --version
   - Poppler (contiene pdftoppm) para `pdf2image`. Verificar:
     pdftoppm -v
   Si los binarios no están en PATH, definir variables (PowerShell):
     setx POPPLER_PATH "C:\\ruta\\a\\poppler\\bin"
     setx TESSERACT_CMD "C:\\Program Files\\Tesseract-OCR\\tesseract.exe"
   (Cerrar y volver a abrir la terminal después de setx.)

4) Ejecutar la app:
   pip install streamlit
   streamlit run app.py
   - En Pantalla 8: seleccionar PDF y, si quieres reprocesar páginas con texto, marcar "Forzar OCR".

Notas:
- El resultado del OCR se guarda en `archivo.pdf.ocr.txt` (misma carpeta que el PDF) para evitar reprocesos.
- Si vas a usar `ocrmypdf` también instala `qpdf` y `ghostscript` para optimizaciones (opcionales).

Si quieres que reemplace el archivo original por esta versión, dímelo y lo hago; si prefieres que lo deje como copia, ya está en `README_OCR_MINIMO.md`.