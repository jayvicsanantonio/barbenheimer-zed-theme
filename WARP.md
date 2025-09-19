# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

Project overview
- Zed Editor theme extension with three variants: Barbenheimer Dreamhouse (light), Barbenheimer Bunker (dark), and Barbenheimer Nuclear Sunrise (high-contrast dark).
- Pure JSON theme; no JS/TS build system or test runner.

High-level architecture
- extension.toml
  - Extension metadata: id=barbenheimer, version, authors, description, repository.
  - Version in this file drives releases; bump before tagging or manual publish.
- themes/barbenheimer.json
  - Single source of truth for all three themes, following Zed’s theme schema (see $schema at top).
  - Each theme object defines UI surface colors, editor styling, terminal ANSI colors, and a comprehensive syntax color map.
  - Variants share a coordinated palette with a pink accent family and contextual adjustments per theme.
- assets/
  - Preview images referenced by the README and marketplace listing (barbenheimer-*.webp).
- .github/workflows/release.yml
  - CI workflow that publishes on git tag push matching v* using huacnlee/zed-extension-action@v1.
  - Inputs: extension-name: barbenheimer, push-to: jayvicsanantonio/extensions; requires COMMITTER_TOKEN secret.
- Docs for AI/dev agents
  - README.md: Theme descriptions, palettes, installation guidance.
  - CLAUDE.md and AGENTS.md: Emphasize no automated tests, visual QA in Zed, JSON schema compliance, two-space indentation, and keeping assets in sync with palette changes.

Commands you’ll commonly use
- Live preview during development (hot reload in a local Zed instance)
  zed extension dev --dir .

- Package a distributable archive for local testing
  zed extension package .

- Manual publish via CLI (useful for ad-hoc releases after bumping version in extension.toml)
  zed extension publish .

- CI-driven release (preferred)
  1) Update version in extension.toml
  2) Create and push a semver tag starting with v
     git tag vX.Y.Z
     git push origin vX.Y.Z
  The GitHub Action will build and publish the extension using the configured action and token.

Testing and validation
- There is no automated test suite. Perform visual QA in Zed:
  - Use live dev mode, switch across all three variants, and verify UI chrome, syntax scopes, terminal colors, and accessibility contrast.
- Theme JSON adheres to https://zed.dev/schema/themes/v0.1.0.json (also referenced via $schema in themes/barbenheimer.json). If you add or rename keys, ensure they match the schema.

Notes and conventions specific to this repo
- Keep JSON indented with two spaces and follow the existing grouping order (surface → editor → terminal → syntax).
- When palettes or structure change, update preview images in assets/ and adjust README if necessary.
