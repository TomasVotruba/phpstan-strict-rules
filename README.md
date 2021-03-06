[![Latest Stable Version](https://poser.pugx.org/thecodingmachine/phpstan-strict-rules/v/stable)](https://packagist.org/packages/thecodingmachine/phpstan-strict-rules)
[![Total Downloads](https://poser.pugx.org/thecodingmachine/phpstan-strict-rules/downloads)](https://packagist.org/packages/thecodingmachine/phpstan-strict-rules)
[![Latest Unstable Version](https://poser.pugx.org/thecodingmachine/phpstan-strict-rules/v/unstable)](https://packagist.org/packages/thecodingmachine/phpstan-strict-rules)
[![License](https://poser.pugx.org/thecodingmachine/phpstan-strict-rules/license)](https://packagist.org/packages/thecodingmachine/phpstan-strict-rules)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/thecodingmachine/phpstan-strict-rules/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/thecodingmachine/phpstan-strict-rules/?branch=master)
[![Build Status](https://travis-ci.org/thecodingmachine/phpstan-strict-rules.svg?branch=master)](https://travis-ci.org/thecodingmachine/phpstan-strict-rules)
[![Coverage Status](https://coveralls.io/repos/thecodingmachine/phpstan-strict-rules/badge.svg?branch=master&service=github)](https://coveralls.io/github/thecodingmachine/phpstan-strict-rules?branch=master)


TheCodingMachine's additional rules for PHPStan
===============================================

This package contains a set of rules to be added to the [wonderful PHPStan static analyzer](https://github.com/phpstan/phpstan).

Those rules come from [TheCodingMachine best practices](http://bestpractices.thecodingmachine.com/).
They are more "strict" than the default PHPStan rules and some may be controversial. We use those at TheCodingMachine, have found them to help us in our daily work, and ask anyone working with us to follow them.

## Rules list

### Exception related rules

- You should not throw the "Exception" base class directly [but throw a sub-class instead](http://bestpractices.thecodingmachine.com/php/error_handling.html#subtyping-exceptions).
- You should not have empty catch statements
- When throwing an exception inside a catch block, [you should pass the catched exception as the "previous" exception](http://bestpractices.thecodingmachine.com/php/error_handling.html#wrapping-an-exception-do-not-lose-the-previous-exception)

### Type-hinting related rules

This is a PHP 7.1+ rule:

- You should use type-hinting when possible
- If not possible, you should use a Docblock to specify the type
- If type-hinting against an array, you should use a Docblock to further explain the content of the array

[More about type-hinting related rules...](doc/typehinting_rules.md)

### Work-in-progress

    // Don't use superglobals (__GET __POST)...
    // Always provide a "default" in a switch statement (and throw an exception if unexpected)
    // Never use public properties
    // Force type hinting on all methods, starting with PHP 7.1 (or mixed must be passed in @param docblock to explain that we expect absolutely anything)

## Installation

We assume that [PHPStan](https://github.com/phpstan/phpstan) is already installed in your project.

Let's add this package:

```bash
composer require --dev thecodingmachine/phpstan-strict-rules
```

Now, edit your `phpstan.neon` file and add these rules:

```yml
includes:
    - vendor/thecodingmachine/phpstan-strict-rules/phpstan-strict-rules.neon
```
