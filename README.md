# A01785013 — Dashboard de abandono estudiantil

Aplicación Dash con datos sintéticos y Pipeline de scikit-learn para explorar alertas académicas y simular riesgo de abandono. Uso exclusivamente educativo.

## Ejecución local

```bash
python -m pip install -r requirements.txt
python train_model.py
python app.py
```

Abre http://127.0.0.1:8050

## Despliegue en Render

1. Sube el contenido de esta carpeta a la **raíz** de un repositorio de GitHub (no subas la carpeta contenedora como subdirectorio).
2. En Render selecciona **New > Web Service**, conecta el repositorio y configura:
   - Name: `a01785013`
   - Language: Python
   - Branch: `main`
   - Build Command: `pip install -r requirements.txt && python train_model.py`
   - Start Command: `gunicorn app:server --bind 0.0.0.0:$PORT --workers 1 --timeout 120`
   - Instance: Free (si está disponible)
3. Crea el servicio y comprueba que los logs indiquen un despliegue exitoso.
4. Abre la URL pública y prueba filtros y predicciones.

También se incluye `render.yaml` para configurar el servicio como Blueprint si lo prefieres.

## Notas

El CSV y el modelo se generan durante el build. No se requiere subir datos reales ni secretos. El CSV entregado por el alumno no es necesario en GitHub: el despliegue regenera los datos sintéticos con semilla 42 para asegurar compatibilidad con el modelo.
