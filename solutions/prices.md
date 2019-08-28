## Intro
There are multiple aspects to designing how prices are handled on the platorm. Of course, no need to reinvent the wheel and we can combine existing solutions from multiple aspects that reach our design goals:
- database design
- custom precition decimal math
- handling multiple currencies

## Solutions
#### PHP (API v1)
BCMath module in PHP. Needs to be enabled in `php.ini`, and installed via the `pecl` php extension manager. Caution, some docker containers use a version of archlinux that does not support this extension.
#### Javascript (API v2)
http://mikemcl.github.io/decimal.js/