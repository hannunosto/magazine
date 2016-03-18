# Magazine — Sane Magento Packaging

Magazine helps you automatically package extensions for Magento 1.x in a sane manner. Magazine uses the cannibalised Magento core classes to build you a fully-compliant Magento package in seconds.

Requirements
------------

Magazine requires PHP version 5.1.2 or greater.

Installation
------------

The easiest way to get started with Magazine is use [Composer](http://getcomposer.org/). You can easily install Magazine system-wide with the following command:

    composer global require "mridang/magazine=*"

Make sure you have `~/.composer/vendor/bin/` in your PATH.

Or alternatively, include a dependency for `mridang/magazine` in your `composer.json` file. For example:

```json
{
    "require-dev": {
        "mridang/magazine": "0.*"
    }
}
```

You will then be able to run Magazine from the vendor bin directory:

    ./vendor/bin/magazine -h

You can also download the Magazine source and run the `magazine` command directly from the Git checkout:

    git clone git://github.com/mridang/magazine.git
    cd magazine
    php bin/magazine -h

Usage
-----

In order to move towards automated packaging, you'll need to create a `package.json` file in your extension's directory. The foarmat of this JSON file closely matches that of the XML file generated by Magento's packager and bundles in the extension package.

Most the fields are self-explanatory but the `include` paths must be carefully configured. 

| Alias          | Description                                     | Path                  | 
|----------------|-------------------------------------------------|-----------------------|
| magelocal      |  Magento Local module file                      |  ./app/code/local     |
| magecommunity  |  Magento Community module file                  |  ./app/code/community |
| magecore       |  Magento Core team module file                  |  ./app/code/core      |
| magedesign     |  Magento User Interface (layouts, templates)    |  ./app/design         |
| mageetc        |  Magento Global Configuration                   |  ./app/etc            |
| magelib        |  Magento PHP Library file                       |  ./lib                |
| magelocale     |  Magento Locale language file                   |  ./app/locale         |
| magemedia      |  Magento Media library                          |  ./media              |
| mageskin       |  Magento Theme Skin (Images, CSS, JS)           |  ./skin               |
| mageweb        |  Magento Other web accessible file              |  .                    |
| magetest       |  Magento PHPUnit test                           |  ./tests              |
| mage           |  Magento other                                  |  .                    |

```json
{
  "name": "Foobar",
  "version": {
    "release": "1.0.4"
  },
  "stability": {
    "release": "beta"
  },
  "license": {
    "_content": "OSL",
    "attribs": {
      "uri": "http://opensource.org/licenses/osl-3.0.php"
    }
  },
  "channel": "community",
  "summary": "Foobar for Magento",
  "description": "Foobar for Magento",
  "notes": "Foobar for Magento",
  "authors": {
    "author": {
      "name": "John Doe",
      "user": "j.doe",
      "email": "john.doe@example.com"
    }
  },
  "date": "2015-01-22",
  "time": "21:13:05",
  "dependencies": {
    "required": {
      "php": {
        "min": "5.2.0",
        "max": "7.0.0"
      }
    }
  },
  "include": {
    "magelocal": [] ,
    "magecommunity": [
      "app/code/community/Foo/Bar/*"
    ],
    "magecore": [],
    "magedesign": [],
    "mageetc": [],
    "magelib": [],
    "magelocale": [],
    "magemedia": [],
    "mageskin": [],
    "mageweb": [],
    "magetest": [],
    "mage": []
  },
  "exclude": [
    "vendor",
    "*.json",
    "*.lock",
    "*.tar"
  ]
}
```

Authors
-------

Mridang Agarwalla

License
-------

Magazine is licensed under the MIT License - see the LICENSE file for details
