# 🎃 Halloween Photo

A Halloween replica and adaptation of [Christmas Photo](https://github.com/SofiaBargues/christmas-photo), the AI Christmas photo editor created by Sofia Bargues. This version keeps the original upload, transform, compare and share workflow and reimagines it for Halloween.

[Try the app](https://halloween-photo-seven.vercel.app/) · [Original Christmas app](https://christmas-photo.vercel.app/)

![Halloween Photo Editor website preview](https://halloween-photo-seven.vercel.app/screenshot.png?v=2)

## What's different from the original?

- Halloween costumes, glowing pumpkins, cobwebs and cinematic orange and violet lighting.
- Bats that flutter and flap around the page, with an effects toggle and reduced-motion support.
- Original suspense music with eerie bells, low drones and a slow pulse, synthesized in the browser. Playback starts only when you press the sound button.
- Halloween copy, favicon, download names and social sharing cards.
- A maximum of two generation attempts per day per IP, enforced on the server through Redis in every environment.
- Shareable results that expire after 30 days.

The AI is instructed to preserve faces, expressions, poses and the photo's composition. Generated results may vary.

## Tech stack

Next.js 16, React 19, TypeScript, Tailwind CSS, Framer Motion, Vercel AI SDK with Google Gemini through AI Gateway, Vercel Blob and Upstash Redis.

## Run locally

Requires Node.js 20.9+ and pnpm.

```sh
git clone https://github.com/SofiaBargues/halloween-photo.git
cd halloween-photo
pnpm install
```

Create a .env.local file with these variables:

```env
AI_GATEWAY_API_KEY=your_vercel_ai_gateway_key
BLOB_READ_WRITE_TOKEN=your_blob_token
HALLOWEEN_KV_REST_API_URL=your_upstash_rest_url
HALLOWEEN_KV_REST_API_TOKEN=your_upstash_rest_token
```

KV_REST_API_URL and KV_REST_API_TOKEN are also supported as fallback Redis settings.

```sh
pnpm dev
```

Open [localhost:3000](http://localhost:3000). Music is off by default.

## Deployment

Halloween has its own Vercel project, halloween-photo, and a free address at [halloween-photo-seven.vercel.app](https://halloween-photo-seven.vercel.app/). The original Christmas project remains separate.

```sh
pnpm dlx vercel login
pnpm dlx vercel link --project halloween-photo
pnpm dlx vercel deploy --prod
```

Configure the environment variables in Vercel before deploying. Do not commit .env.local or credentials.

## Storage and compatibility

New images are stored under halloween/ in Blob. Redis stores result links for 30 days and tracks usage per IP. The historical christmas-photo rate-limit prefix is retained for continuity. Records from the old, uninstalled database were not migrated to the new database.

## Screenshot, demo image and credits

The screenshot above shows the Halloween app and its before/after comparison. The demo portrait was created with imagegen from public/demo-before.png. Editing prompt: preserve the subject's identity, face, glasses, headphones, pose and room composition; add a purple witch-inspired costume, glowing pumpkins, cobwebs, bats and cinematic orange/violet lighting; no gore, text or watermark.

Original project and Halloween adaptation by [Sofia Bargues](https://github.com/SofiaBargues).


