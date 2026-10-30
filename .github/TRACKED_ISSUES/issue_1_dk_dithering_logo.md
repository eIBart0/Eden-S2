# Issue 1: [Shader] Artifact visual de dithering en el logo de Donkey Kong Bananza

- **Title ID:** `040074A01BF12000`
- **Labels:** `shader`, `switch2`, `visual-artifact`
- **Status:** En investigación (Hipótesis de Claude)

## Descripción
En la pantalla de título de Donkey Kong Bananza, el logo aparece con un granulado/punteado regular ("vidrio esmerilado") y flecos de color.

## Evidencia Técnica
- **Lecturas no mapeadas instrumentadas**:
  - `0xde642000` (4096 bytes a los 13.7 s)
  - `0xde644000` (49152 bytes a los 13.7 s)
  - `0xde63c000` (4096 bytes a los 40.5 s)
- **Causa raíz probable**: Huecos de memoria de textura/LUT que nunca fueron mapeados por el host. Al devolver ceros, la máscara de dithering queda vacía.

## Próximos pasos
1. Prueba de `shaderFloat16 = false`.
2. Reintentar o rellenar lecturas no mapeadas para validar si desaparece el granulado.
