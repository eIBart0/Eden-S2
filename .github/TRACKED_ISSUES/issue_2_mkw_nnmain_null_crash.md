# Issue 2: [Crash] Mario Kart World falla en nnMain con salto a dirección nula (0x0)

- **Title ID:** `0400C3F00006E000`
- **Labels:** `crash`, `kernel`, `switch2`
- **Status:** Confirmado en Base y Update

## Descripción
Al arrancar `Drive.nss` (Mario Kart World), la ejecución falla en los primeros segundos lanzando una excepción `Cannot execute instruction at unmapped address 0x00000000000000`.

## Evidencia Técnica
- **Backtrace**:
  `nnrtld 000000710000008C`
  `nnSdk 0000007100115DC8 nn::init::Start()`
  `Drive.nss 0000007100CF23B0`
  `Drive.nss 00000071000F04EC` -> instrucción `blr x8` con `x8 = 0x0`.
- **Causa raíz**: Intento de invocar una función virtual no inicializada o vtable nula en `Drive.nss` a través de un puntero nulo leído de memoria no mapeada.
