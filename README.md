php-cli-helpers
===============

Utility classes to write PHP command-line scripts

[![Build Status](https://travis-ci.org/amercier/php-cli-helpers.png?branch=master)](https://travis-ci.org/amercier/php-cli-helpers)
[![Coverage Status](https://coveralls.io/repos/amercier/php-cli-helpers/badge.png?branch=master)](https://coveralls.io/r/amercier/php-cli-helpers?branch=master)
[![Dependency Status](https://www.versioneye.com/user/projects/51ed3f51632bac3b8900366c/badge.png)](https://www.versioneye.com/user/projects/51ed3f51632bac3b8900366c)

[![Latest Stable Version](https://poser.pugx.org/amercier/cli-helpers/v/stable.png)](https://packagist.org/packages/amercier/cli-helpers)


Installation
------------

_php-cli-helpers_ is available through [Composer](http://getcomposer.org/).
```json
  "require": {
    "amercier/php-cli-helpers": "1.*"
  }
```
```bash
php composer.phar install
```

If you are not familiar with _Composer_, please read the
[full installation intructions](docs/install.md).


Usage
-----


### Parameter

Utility class to handle command-line parameters.

```php
$options = \Cli\Helpers\Parameter::getFromCommandLine(array(
    'host'     => new Parameter('h', 'host'    , '127.0.0.1'),
    'username' => new Parameter('u', 'username', Parameter::VALUE_REQUIRED),
    'password' => new Parameter('p', 'password', Parameter::VALUE_REQUIRED),
    'verbose'  => new Parameter('v', 'verbose' , Parameter::VALUE_NO_VALUE),
));

$options['host'];     // given -h/--host, or 127.0.0.1 otherwise
$options['username']; // given -u/--username
$options['password']; // given -p/--password
$options['verbose'];  // true if -v/--verbose is given, false otherwise
```

See [API Documentation for Parameter](docs/api-parameter.md)


### Parameter

Utility class to run a job and catch exceptions.

On successful jobs:
```
\Cli\Helpers\Job::run('Doing awesome stuff', function() {
    ... // awesome stuff
});
```
```
Doing awesome stuff... OK
```

On unsuccessful jobs:
```
\Cli\Helpers\Job::run('Fighting Chuck Norris', function() {
    ... // throws a RoundHouseKickException('You've received a round-house kick', 'face')
});
```
```
Fighting Chuck Norris... NOK - You've received a round-house kick in the face
```

See [API Documentation for Job](docs/api-job.md)


Contributing
------------

Contributions (issues ♥, pull requests ♥♥♥) are more than welcome! Feel free to
clone, fork, modify, extend, etc, as long as you respect the
[license terms](../LICENSE).

See [contributing intructions](docs/contributing.md) for details.


Licensing
---------

This project is released under [MIT License](LICENSE) license. If this license
does not fit your requirement for whatever reason, but you would be interested
in using the work (as defined below) under another license, please contact
[authors](docs/authors.md).
