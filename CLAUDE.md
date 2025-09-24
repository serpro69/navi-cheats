# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains personal cheatsheets for [navi](https://github.com/denisidoro/navi), a command-line cheatsheet tool. The primary focus is creating `.cheat` files that provide interactive command templates with auto-completion for various tools and services.

## Repository Structure

- `*.cheat` files: Navi cheatsheet files with command templates (e.g., `gcloud.cheat`)
- `docs/`: Documentation for specific cheatsheets (e.g., `gcloud.md`)
- `navi/`: Git submodule containing the upstream navi repository for documentation reference

## Navi Cheatsheet Format

Cheatsheets follow the navi syntax format:

```
% tag1, tag2, tag3
# Description of the command
command <placeholder>

$ placeholder: command-to-generate-options
$ another_placeholder: echo "option1 option2" | tr ' ' '\n'
```

Key syntax elements:
- `%` - Defines tags for categorizing commands
- `@` - References helper variables from other sections (e.g., `@ gcloud, common`)
- `#` - Command description
- `$` - Variable definitions that provide auto-completion options
- `;` - Comments (not displayed in navi interface)
- `<placeholder>` - Variables that will be populated via auto-completion

Full syntax and other relevant documentation can be found in the [navi docs](./navi/docs/)

## Development Workflow

### Adding New Cheatsheets

1. Create a new `.cheat` file in the root directory
2. Use the existing `gcloud.cheat` as a reference for format and structure
3. Organize commands into logical sections with clear comments
4. Define helper variables at the top of the file for reuse across commands
5. Create corresponding documentation in `docs/<name>.md` explaining features and usage
6. Update `README.md` in the root directory with the link to the new cheat doc file

### Modifying Existing Cheatsheets

1. Follow the existing naming conventions and organization patterns
2. Use helper variables from the `common` section when applicable (defined at file top)
3. Maintain consistent tagging structure for easy navigation
4. Test commands locally before committing

### Testing Cheatsheets

To test cheatsheets locally with navi:

```bash
navi
```

## Code Style Guidelines

- Use descriptive tags that follow the format: `tool, category, subcategory`
- Include the `@ tool, common` reference when using shared helper variables
- Group related commands into sections with clear comment dividers
- Provide meaningful command descriptions that explain the purpose
- Use consistent indentation (spaces, not tabs) in multi-line commands
- For complex commands, use code blocks with proper escaping

## Helper Variables

The `gcloud.cheat` file demonstrates the pattern of defining reusable helper variables:

```
$ project: gcloud projects list --format='value(projectId)'
$ compute_region: gcloud compute regions list --format='value(name)'
```

These can be referenced in multiple commands throughout the file, reducing duplication and ensuring consistency.

The same `gcloud.cheat` also contains good examples of "interactive variables", where a variable itself runs a command that, i.e. returns a list of values, which `navi` tool can then present to the user for interactive selection. This greatly improves the workflow and experience of using the `navi` tooling:

```
$ project: gcloud projects list --format='value(projectId)'
```
