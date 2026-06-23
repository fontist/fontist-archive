# fontist-archive

Pre-built woff2 specimens and Unicode coverage data for fonts in [fontist/formulas](https://github.com/fontist/formulas).

## Contents

```
coverage/           ← Unicode coverage JSON per font (codepoints, blocks, features)
fonts/              ← woff2 specimens (redistributable fonts only, OTS-safe)
fonts.json          ← Font registry: canonical name → all formula paths
font-metadata.json  ← Manifest: which fonts have coverage/specimen data
```

## How It's Built

The [generate_font_metadata.rb](https://github.com/fontist/formulas/blob/main/process/generate_font_metadata.rb) script in formulas:
1. Downloads font files from formula URLs
2. Extracts Unicode coverage (cmap table)
3. Subsets + converts to woff2 via [Fontisan](https://github.com/fontist/fontisan)
4. Re-encodes woff2 via fontTools for browser OTS compatibility

## Usage

Websites (e.g., [fontist.org](https://github.com/fontist/fontist.github.io)) fetch this data at build time:

```bash
# Clone or download as tarball
git clone --depth 1 https://github.com/fontist/fontist-archive.git

# Or fetch specific files
curl -O https://raw.githubusercontent.com/fontist/fontist-archive/main/coverage/inter.json
```

## Update Schedule

Rebuilt when formulas are added or updated. Triggered by formulas CI.
