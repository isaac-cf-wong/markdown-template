# A markdown repository template

[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/isaac-cf-wong/markdown-template/main.svg)](https://results.pre-commit.ci/latest/github/isaac-cf-wong/markdown-template/main)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

This is a template repository for markdown-based projects. It includes configurations for linting, spell checking, and formatting markdown files.

## Features

- **Markdown linting** with `markdownlint` - Enforces consistent markdown style
- **Spell checking** with `cspell` - Catches typos and spelling errors
- **Pre-commit hooks** with `pre-commit` - Automated checks before commits
- **Formatting** with `prettier` - Consistent code and markdown formatting
- **YAML linting** with `yamllint` - Validates YAML configuration files
- **Secret detection** with `detect-secrets` - Prevents accidental secret
  commits
- **Automated releases** with GitHub Actions - Tag-based release workflow

## Quick Start

### Using this template

1. Click "Use this template" button on GitHub
2. Clone your new repository
3. Install dependencies and set up pre-commit hooks:

```bash
# Install pre-commit (if not already installed)
pip install pre-commit

# Install the git hook scripts
pre-commit install

# Install commit-msg hook for spell checking commit messages
pre-commit install --hook-type=commit-msg

# (Optional) Run against all files
pre-commit run --all-files
```

### Manual setup for existing projects

```bash
# Copy configuration files to your project
curl -O https://raw.githubusercontent.com/isaac-cf-wong/markdown-template/main/.pre-commit-config.yaml
curl -O https://raw.githubusercontent.com/isaac-cf-wong/markdown-template/main/.markdownlint.yaml
curl -O https://raw.githubusercontent.com/isaac-cf-wong/markdown-template/main/.yamllint.yaml
curl -O https://raw.githubusercontent.com/isaac-cf-wong/markdown-template/main/cspell.json
curl -O https://raw.githubusercontent.com/isaac-cf-wong/markdown-template/main/.prettierrc

# Install and setup pre-commit
pip install pre-commit
pre-commit install
pre-commit install --hook-type=commit-msg
```

## Configuration Files

| File                      | Purpose                       | Customization                            |
| ------------------------- | ----------------------------- | ---------------------------------------- |
| `.pre-commit-config.yaml` | Pre-commit hook configuration | Add/remove hooks, update versions        |
| `.markdownlint.yaml`      | Markdown linting rules        | Modify rules to match your style         |
| `cspell.json`             | Spell check configuration     | Add project-specific words to dictionary |
| `.prettierrc`             | Code formatting rules         | Adjust formatting preferences            |
| `.yamllint.yaml`          | YAML linting configuration    | Customize YAML style rules               |
| `.ignore_words.txt`       | Custom spell check dictionary | Add technical terms, names, etc.         |

## Customization

### Adding custom words to spell checker

Edit `.ignore_words.txt` to add project-specific terms:

```txt
kubernetes
dockerfile
```

### Modifying markdown rules

Edit `.markdownlint.yaml` to customize markdown linting:

```yaml
# Disable specific rules
MD013: false # Line length
MD033: false # Allow inline HTML

# Configure rule options
MD024:
  siblings_only: true # Allow duplicate headers in different sections
```

### Adding more pre-commit hooks

Edit `.pre-commit-config.yaml` to add additional hooks:

```yaml
- repo: https://github.com/psf/black
  rev: 22.3.0
  hooks:
    - id: black
      language_version: python3
```

## GitHub Actions

This template includes a release workflow that:

- Triggers on version tags (e.g., `v1.0.0`)
- Creates GitHub releases automatically
- Uses `gh` CLI for GitHub-specific features

To create a release:

```bash
git tag v1.0.0
git push origin v1.0.0
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file
for details.
