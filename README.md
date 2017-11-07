# typo3_cgl_helpers
Configuration files for PHPStrom providing TYPO3 CGL related settings

File `PHPStorm_TYPO3_code_sheme.xml` contains PHPStorm code scheme definition for PHP (PSR2)
and JS (based on AirBnB).
Not all rules are possible to set in PHPStrom, but the basics are there. Thanks to that you can use *Code* => *Reformat Code*
option for JS files too.

## How to import the configuration to PHPStorm

1) Go to *Settings* => *Editor* => *Code Style*
2) Click on the gear icon by 'Scheme'
3) Select *Import Scheme* => *Intellij IDEA code style XML*
4) Select File `PHPStorm_TYPO3_code_sheme.xml`

## How to setup AirBnB JS Code Style inspections using JSCS
1) Install JSCS (-g means globally)
`npm install jscs -g`
2) Go to *Settings* => *Languages & Frameworks* => *JavaScript* => *Code Quality Tools* > *JSCS*
3) Check *Enable*
4) Configure node interpreter (e.g. `/usr/bin/node`)
5) Set JSCS package (e.g. `/usr/local/lib/node_modules/jscs`)
6) Select *Airbnb* from the *Code style preset* list 
7) Enjoy

## Disable Default PHPStorm inspections which are in conflict with Airbnb style
1) Go to *Settings* => *Editor* => *Inspections*
2) Look for *Unneeded last comma in object literal* and *Unneeded last comma in array literal*
3) Uncheck them

## Some random notes on Airbnb styles
We should have consistent indentation of the requirejs modules content (body of the function), independently from whether we have many (multiline) dependencies, or just a few. 
This way if we add one additional dependency and would need to wrap them in few lines, we dont need to reformat the whole file.

eg.
```
define(['jquery', 'd3', 'TYPO3/CMS/Backend/Icons'],
  function ($, d3, Icons) {
    'use strict';

    var dd = 3;
  });
```
```
define(
  [
    'jquery',
    'd3',
    'TYPO3/CMS/Backend/ContextMenu',
    'TYPO3/CMS/Backend/Modal',
    'TYPO3/CMS/Backend/Severity',
    'TYPO3/CMS/Backend/Notification',
    'TYPO3/CMS/Backend/Icons',
    'TYPO3/CMS/Lang/Lang',
  ],
  function ($, d3, ContextMenu, Modal, Severity, Notification, Icons) {
    'use strict';

    var dd = 3;
  });
```
