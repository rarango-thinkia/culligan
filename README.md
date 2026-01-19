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

**Si te pide contraseña al entrar a la URL:** Usa la contraseña definida en tu archivo `.env` (o la que se configura en *Tienda Online > Preferencias*).

## 3. Subir Cambios a Shopify (Publicar)

Cuando hayas terminado tus cambios y quieras subirlos a la tienda en la nube:

```bash
npm run push
```

El CLI te preguntará:
1.  A qué tema quieres subir los cambios.
    - Selecciona el tema **Live (Publicado)** si quieres que los clientes lo vean de inmediato.
    - O selecciona un tema **Unpublished** (o crea uno nuevo) para subirlo como borrador y revisarlo antes de publicar.

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
