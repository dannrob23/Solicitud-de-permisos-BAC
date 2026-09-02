# Reporte público — Historial de Solicitudes de Ingreso

Página de consulta (solo lectura) para publicar en **Streamlit Community Cloud**.

## Contenido
- `reporte.py` — la app de consulta.
- `base.db` — copia SANITIZADA del historial (solo campos visibles, sin correos internos, asuntos ni notas).
- `requirements.txt`, `.streamlit/config.toml`.

## Desplegar en Streamlit Cloud (una vez)

1. Crea un repositorio **PRIVADO** en GitHub (GitHub → New repository → Private). No lo inicialices con archivos (README/LICENSE) para evitar conflictos.
2. Conecta este folder al repositorio (desde una terminal en esta carpeta `publico`):

   ```
   git remote add origin https://github.com/TU_USUARIO/NOMBRE_REPO.git
   git branch -M main
   git push -u origin main
   ```

3. Entra a https://share.streamlit.io y crea cuenta con el mismo usuario de GitHub.
4. **New app** → elige el repositorio → Branch `main` → Main file `reporte.py` → **Deploy**.
5. Copia la URL que te da Streamlit (quedará tipo `https://TU_USUARIO-NOMBRE.streamlit.app`) y compártela con tus compañeros.

### Contraseña de consulta (recomendado)
En Streamlit Cloud: **Settings → Secrets** y pega:

```
consulta = {password = "elige-una-contrasena"}
```

Con ese secreto, el reporte pedirá contraseña. Sin él, queda abierto para quien tenga la URL.

## Actualizar los datos (cada vez que cambies estados)
En tu PC, ejecuta con doble clic `sincronizar_publico.bat` (en la carpeta principal, PERMISOS).
Esto exporta la base local a `publico/base.db`, hace commit y push; Streamlit Cloud
actualiza la app automáticamente en pocos minutos.

> Importante: la base pública solo contiene datos del historial. Aún así, mantenla
> en un repositorio privado y pon contraseña, porque contiene nombres de funcionarios
> y oficinas de la compañía.
