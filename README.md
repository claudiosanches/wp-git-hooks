# WP GIT Hooks

My GIT hooks for WordPress plugins and themes development.

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
        "ClaudioSanches\\WpGitHooks\\Hooks::postHooks"
    ],
    "post-update-cmd": [
        "ClaudioSanches\\WpGitHooks\\Hooks::postHooks"
    ]
}
```

This will install all hooks and setup WPCS.

### Sample phpcs.xml for PHPCS/WPCS

A `phpcs.xml` file is required in order to correct run your project's coding standards.

```xml
<?xml version="1.0"?>
<ruleset name="WordPress Coding Standards">
    <description>PHP_CodeSniffer ruleset for WordPress plugins and themes development.</description>

    <rule ref="PHPCompatibility"></rule>
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

- 2018-07-31 - 1.3.2
 - Full support for `phpcs.xml.dist`.
- 2017-12-18 - 1.3.1
 - Fixed support for `phpcs.xml.dist`.
- 2017-12-18 - 1.3.0
 - Requires `phpcs.xml` or `phpcs.xml.dist` by default.
 - No longer accepts `phpcs.xml`.
- 2017-11-19 - 1.2.0
 - Included support for `PHPCompatibility`.
 - Automatically load all PHP_CodeSniffer plugins.
- 2017-11-09 - 1.1.0
 - Removed unnecessary configuration file.
- 2017-10-30 - 1.0.1
 - Fixed vendor path for `hooks/pre-commit` and `bin/read-wp-git-hooks-config`.
- 2017-10-27 - 1.0.0
 - Initial release.

## Sources

Inspired by:

- <https://github.com/juizmill/git-hooks>
- <https://github.com/smgladkovskiy/phpcs-git-pre-commit>
