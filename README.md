# WP GIT Hooks

GIT hooks for WordPress plugins and themes development.

## Hooks

* `pre-commit` - Lint and check coding standards using [WPCS](https://packagist.org/packages/wp-coding-standards/wpcs).

## Installation

```bash
composer require claudiosanches/wp-git-hooks
```

## Setup

Include the follow lines into the project's `composer.json`:

```
"scripts": {
    "pre-update-cmd": [
        "ClaudioSanches\\WpGitHooks\\Hooks::preHooks"
    ],
    "pre-install-cmd": [
        "ClaudioSanches\\WpGitHooks\\Hooks::preHooks"
    ],
    "post-install-cmd": [
        "\"vendor/bin/phpcs\" --config-set installed_paths vendor/wp-coding-standards/wpcs",
        "ClaudioSanches\\WpGitHooks\\Hooks::postHooks"
    ],
    "post-update-cmd": [
        "\"vendor/bin/phpcs\" --config-set installed_paths vendor/wp-coding-standards/wpcs",
        "ClaudioSanches\\WpGitHooks\\Hooks::postHooks"
    ]
}
```

This will install all hooks and setup WPCS.

### Configuration file

Supports a configured file named `.wp-git-hooks.yml`.

See an example of configuration file to make PHPCS/WPCS ignore files and paths:

```yml
pre_commit:
  ignore:
    - foo.php
    - includes/bar.php
    - test/
```

### Sample phpcs.ruleset.xml for PHPCS/WPCS

A `phpcs.ruleset.xml` file is required in order to correct run your project's coding standards.

```xml
<?xml version="1.0"?>
<ruleset name="WordPress Coding Standards">
    <description>PHP_CodeSniffer ruleset for WordPress plugins and themes development.</description>

    <rule ref="WordPress"></rule>
</ruleset>
```

### Manual setup (optional)

By default should already run all commands from composer `scripts` when installed, but if necessary run it manually is possible with the follow commands:

```bash
composer run-script pre-update-cmd
composer run-script post-update-cmd
```

## Release history

- 2017-10-27 - 1.0.0 - Initial release.

## Sources

Inspired by:

- <https://github.com/juizmill/git-hooks>
- <https://github.com/smgladkovskiy/phpcs-git-pre-commit>
