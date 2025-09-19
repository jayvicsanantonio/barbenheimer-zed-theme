# Repository Guidelines

## Project Structure & Module Organization
Everything ships from `themes/barbenheimer.json`, which defines the Barbenheimer Bunker, Dreamhouse, and Nuclear Sunrise variants expected by Zed's theme schema. Preview images that accompany marketplace listings live in `assets/` (`barbenheimer-*.webp`). Extension metadata resides in `extension.toml`; update the version there before publishing. Shared documentation, licensing, and conduct guidelines stay at the repo root.

## Build, Test, and Development Commands
`zed extension package .` builds a distributable archive for local testing. Use `zed extension publish .` only after validating a release build; it pushes the version declared in `extension.toml`. During theme tweaking, run `zed extension dev --dir .` to hot-reload the theme in a local Zed instance without re-packaging.

## Coding Style & Naming Conventions
Keep JSON indented with two spaces and fields ordered to mirror the current grouping (surface colors, editor colors, scopes). Color keys follow Zed's dotted naming—reuse the existing patterns rather than inventing new namespaces. Image assets should remain WebP, lower-case, hyphen-separated filenames. When updating metadata, prefer plain English, sentence-case descriptions.

## Testing Guidelines
There is no automated test suite; rely on visual QA. Launch Zed with `zed extension dev --dir .`, switch through all three variants, and verify syntax scopes, UI chrome, terminal colors, and accessibility contrast. Update `assets/` screenshots whenever palettes change so the marketplace listing reflects the current look. If you alter schema fields, validate against `https://zed.dev/schema/themes/v0.1.0.json` to catch typos early.

## Commit & Pull Request Guidelines
Commit messages in this repo are short, imperative statements (e.g., "Fix Barbenheimer Bunker"). Follow that style and keep each commit scoped to a focused change. For pull requests, describe the motivation, list notable color or structural changes, and attach before/after screenshots from Zed. Link GitHub issues when relevant and confirm that `extension.toml` and packaged artifacts stay in sync before requesting review.
