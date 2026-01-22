# Culligan Shopify Theme

Documentación para el desarrollo local y despliegue del tema de Shopify.

## 1. Configuración Inicial

Asegúrate de tener el archivo `.env` en la raíz del proyecto con la contraseña de la tienda:

```env
SHOPIFY_STORE_PASSWORD=tu_contraseña_aqui
```

> **Nota:** Este archivo `.env` es ignorado por Git para seguridad.

## 2. Desarrollo Local (Probar cambios)

Para trabajar en el tema y ver los cambios en tiempo real:

```bash
npm run dev
```

Esto:

- Iniciará un servidor local.
- Te dará una URL (ej. `http://127.0.0.1:9292`) para previsualizar la tienda.
- Sincronizará automáticamente (hot-reload) cualquier cambio que hagas en el código CSS, Liquid o JS.

**Si te pide contraseña al entrar a la URL:** Usa la contraseña definida en tu archivo `.env` (o la que se configura en _Tienda Online > Preferencias_).

## 3. Subir Cambios a Shopify (Publicar)

Cuando hayas terminado tus cambios y quieras subirlos a la tienda en la nube:

```bash
npm run push
```

El CLI te preguntará:

1.  A qué tema quieres subir los cambios.
    - Selecciona el tema **Live (Publicado)** si quieres que los clientes lo vean de inmediato.
    - O selecciona un tema **Unpublished** (o crea uno nuevo) para subirlo como borrador y revisarlo antes de publicar.
1.  **Select a theme to push to (Elige el destino):**
    - **Live (Horizon):** ⚠️ ¡Cuidado! Esto actualiza la tienda pública visible para todos los clientes. Úsalo solo para versiones finales.
    - **Unpublished / Development:** Recomendado para subir funcionalidades en prueba (como el nuevo funnel de suscripción). Si no existe, elige `[Create a new theme]` y ponle un nombre como "Testing Funnel".

1.  **Confirmación:**
    - Si eliges Live, te pedirá confirmación explícita ("Yes, confirm changes").

**Ejemplo de flujo para esta nueva funcionalidad:**

1.  Sube cambios a un tema borrador: `npm run push` -> Elige "Subscription Draft".
2.  Comparte el enlace del borrador para revisión.
3.  Una vez aprobado, haz `npm run push` -> Elige "Horizon (Live)".

## 4. Control de Versiones (Git)

Para guardar tu historial de cambios en GitHub:

```bash
# 1. Agregar archivos modificados
git add .

# 2. Guardar (Commit) con un mensaje descriptivo
git commit -m "Descripción de lo que hiciste"

# 3. Subir a GitHub
git push
```

## 5. Solución de Problemas

### Error de Acceso a la Tienda (Access denied / Don't have access)

Si al ejecutar `npm run dev` obtienes un error indicando que no tienes acceso a la tienda (`Looks like you don't have access this dev store`), es probable que tu sesión haya caducado o no se haya iniciado correctamente.

**Solución:**

1. Ejecuta el siguiente comando para iniciar sesión manualmente en el navegador:
   ```bash
   npm exec shopify auth login
   ```
2. Sigue los pasos en el navegador para iniciar sesión con tu cuenta de Shopify.
3. Vuelve a ejecutar `npm run dev`.
