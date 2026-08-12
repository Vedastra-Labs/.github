# Vedastra Brand Assets

Org identity assets for the `Vedastra-Labs` GitHub organisation.

## `vedastra-avatar.svg`

The Vedastra brand mark — a white four-pointed star (✦) on brand-purple
(`#6d28d9`), rounded square. This is the **source of truth**; it matches the
generated favicon in `vedastra-web/app/icon.tsx`.

**Used for:** the GitHub org profile picture (set manually at
Organization Settings → Profile → Profile picture).

### Regenerate a PNG (e.g. for the 512×512 org avatar)

Rasterize with `sharp` (available in `vedastra-platform/node_modules`):

```bash
cd vedastra-platform
node -e 'const s=require("sharp");s(require("fs").readFileSync("../.github/brand/vedastra-avatar.svg"),{density:300}).resize(512,512).png().toFile("vedastra-avatar-512.png").then(i=>console.log(i))'
```

Do not commit the generated PNG — regenerate on demand from this SVG.
