# Issue 3: [Video] Decodificador nativo FFmpeg para cinemáticas de Switch 2

- **Title ID:** `All Switch 2 Titles`
- **Labels:** `video`, `services`, `switch2`
- **Status:** Parche disponible (`eden-ns2-bananza-fixes.patch`)

## Descripción
Los juegos de Switch 2 como Donkey Kong Bananza utilizan un decodificador nativo de video a través de `native_video_decoder.cpp` que requiere contexto FFmpeg y soporte para H.264 / AV1.

## Solución
Integrar los cambios del parche oficial de PR 4588 (`eden-ns2-bananza-fixes.patch`):
- `ffmpeg_context` y `ffmpeg_decoder` en `native_video_decoder.cpp`.
- Ajuste de `NUM_STORAGE_BUFFERS = 32`.
