# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Zed Editor theme extension called "Barbenheimer Theme" inspired by the cultural phenomenon of the same name. The project contains three theme variants that combine Barbie's playful aesthetics with Oppenheimer's dramatic tones:

- **Barbenheimer Dreamhouse** (light theme): Vibrant pinks with grounding tones
- **Barbenheimer Bunker** (dark theme): Muted hues with subtle pink highlights
- **Barbenheimer Nuclear Sunrise** (high-contrast dark theme): Bold colors with maximum readability

## Repository Structure

```
.
├── extension.toml          # Extension metadata and configuration
├── themes/
│   └── barbenheimer.json  # Theme definitions with all three variants
├── assets/                # Theme preview images
└── .github/workflows/     # GitHub Actions for automated publishing
```

## Development Commands

This is a pure theme extension with no build system. The following operations are available:

- **Publishing**: Handled automatically via GitHub Actions when tags are pushed
- **Testing**: Install locally in Zed and switch between theme variants
- **Validation**: Theme JSON follows Zed's theme schema at `https://zed.dev/schema/themes/v0.1.0.json`

## Theme Architecture

The `themes/barbenheimer.json` file contains all theme definitions following Zed's theme specification:

- Each theme variant is a complete object within the `themes` array
- Themes include comprehensive styling for UI elements, syntax highlighting, and terminal colors
- Color palettes are carefully coordinated between light and dark variants
- All themes share the signature pink accent color (`#F672AC` family) with contextual variations

## Publishing Process

Publishing is automated via GitHub Actions (`.github/workflows/release.yml`):
1. Create and push a git tag starting with 'v' (e.g., `v1.3.2`)
2. GitHub Action automatically publishes to the Zed Extensions registry
3. Uses `huacnlee/zed-extension-action@v1` for the publishing workflow

## Extension Configuration

Key settings in `extension.toml`:
- Extension ID: `barbenheimer`
- Current version: `1.3.1`
- Repository: `https://github.com/jayvicsanantonio/barbenheimer-zed-theme`
- Schema version: 1 (current Zed extension format)

## Theme Customization

Users can customize themes by overriding specific attributes in their Zed `settings.json`. The theme provides comprehensive coverage of all Zed styling properties including editor, UI, terminal, and syntax highlighting colors.