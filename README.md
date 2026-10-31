# 🎃 Halloween Photo

Una réplica y adaptación de [Christmas Photo](https://github.com/SofiaBargues/christmas-photo), el editor de fotos navideñas creado por Sofia Bargues. Esta versión conserva el flujo de subir una foto, transformarla con IA, comparar y compartir, y lo reinventa para Halloween.

[Probar la web](https://halloween-photo-seven.vercel.app/) · [Proyecto original de Navidad](https://christmas-photo.vercel.app/)

![Ejemplo de una foto transformada para Halloween](https://halloween-photo-seven.vercel.app/demo-after.png)

## Qué cambia respecto al original

- Disfraces, calabazas iluminadas, telarañas y luz cinematográfica naranja y violeta.
- Murciélagos que revolotean y aletean por la página, con un interruptor y soporte para movimiento reducido.
- Música original de suspenso: campanas inquietantes, graves y un pulso lento, sintetizada en el navegador. Se activa solo al pulsar el botón de sonido.
- Textos, favicon, descargas y tarjetas para compartir adaptados a Halloween.
- Máximo de dos intentos de generación diarios por IP, aplicado en el servidor mediante Redis en todos los entornos.
- Resultados compartidos que caducan a los 30 días.

La IA recibe instrucciones para conservar las caras, expresiones, poses y la composición de la foto. El resultado generado puede variar.

## Tecnologías

Next.js 16, React 19, TypeScript, Tailwind CSS, Framer Motion, Vercel AI SDK con Google Gemini a través de AI Gateway, Vercel Blob y Upstash Redis.

## Ejecutar en local

Requiere Node.js 20.9+ y pnpm.

```sh
git clone https://github.com/SofiaBargues/halloween-photo.git
cd halloween-photo
pnpm install
```

Crea un archivo .env.local con estas variables:

```env
AI_GATEWAY_API_KEY=your_vercel_ai_gateway_key
BLOB_READ_WRITE_TOKEN=your_blob_token
HALLOWEEN_KV_REST_API_URL=your_upstash_rest_url
HALLOWEEN_KV_REST_API_TOKEN=your_upstash_rest_token
```

También se admiten KV_REST_API_URL y KV_REST_API_TOKEN como alternativa para Redis.

```sh
pnpm dev
```

Abre [localhost:3000](http://localhost:3000). La música está desactivada al entrar.

## Despliegue

Halloween tiene su propio proyecto de Vercel, halloween-photo, y su dirección gratuita [halloween-photo-seven.vercel.app](https://halloween-photo-seven.vercel.app/). El proyecto original de Navidad permanece separado.

```sh
pnpm dlx vercel login
pnpm dlx vercel link --project halloween-photo
pnpm dlx vercel deploy --prod
```

Configura las variables de entorno en Vercel antes de desplegar. No subas .env.local ni credenciales al repositorio.

## Almacenamiento y compatibilidad

Las nuevas imágenes se guardan bajo halloween/ en Blob. Redis almacena los enlaces durante 30 días y controla la cuota por IP. El prefijo histórico christmas-photo del contador se conserva para mantener continuidad. Los registros de la antigua base desinstalada no se migraron a la nueva base.

## Imagen de demostración y créditos

La imagen de arriba se creó con imagegen a partir de public/demo-before.png: conservar identidad, cara, gafas, auriculares, pose y composición de la habitación; añadir un disfraz de bruja violeta, calabazas, telarañas, murciélagos y luz naranja/violeta; sin gore ni texto.

Proyecto original y adaptación: [Sofia Bargues](https://github.com/SofiaBargues).

