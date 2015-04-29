# JsonCollectionParser
[![Build Status](https://api.travis-ci.org/MAXakaWIZARD/JsonCollectionParser.png?branch=master)](https://travis-ci.org/MAXakaWIZARD/JsonCollectionParser) 
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/MAXakaWIZARD/JsonCollectionParser/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/MAXakaWIZARD/JsonCollectionParser/?branch=master)
[![Code Climate](https://codeclimate.com/github/MAXakaWIZARD/JsonCollectionParser/badges/gpa.svg)](https://codeclimate.com/github/MAXakaWIZARD/JsonCollectionParser)
[![Coverage Status](https://coveralls.io/repos/MAXakaWIZARD/JsonCollectionParser/badge.svg?branch=master)](https://coveralls.io/r/MAXakaWIZARD/JsonCollectionParser?branch=master)
[![SensioLabsInsight](https://insight.sensiolabs.com/projects/801d5faf-e753-4b5c-8a14-5795a1a4d239/mini.png)](https://insight.sensiolabs.com/projects/801d5faf-e753-4b5c-8a14-5795a1a4d239)

[![GitHub tag](https://img.shields.io/github/tag/MAXakaWIZARD/JsonCollectionParser.svg?label=latest)](https://packagist.org/packages/maxakawizard/json-collection-parser) 
[![Packagist](https://img.shields.io/packagist/dt/maxakawizard/json-collection-parser.svg)](https://packagist.org/packages/maxakawizard/json-collection-parser)
[![Minimum PHP Version](http://img.shields.io/badge/php-%3E%3D%205.3-8892BF.svg)](https://php.net/)
[![License](https://img.shields.io/packagist/l/maxakawizard/json-collection-parser.svg)](https://packagist.org/packages/maxakawizard/json-collection-parser)

Event-based parser for large JSON collections (consumes small amount of memory).
Collection must be an array of objects.
Built on top of [JSON Streaming Parser](https://github.com/salsify/jsonstreamingparser)

This package is compliant with [PSR-4](http://www.php-fig.org/psr/4/), [PSR-1](http://www.php-fig.org/psr/1/), and [PSR-2](http://www.php-fig.org/psr/2/).
If you notice compliance oversights, please send a patch via pull request.

## Usage
Function as callback:
```php
function processItem(array $item)
{
    print_r($item);
}

$parser = new \JsonCollectionParser\Parser();
$parser->parse('/path/to/file.json', 'processItem');
```

Static method as callback:
```php
class ItemProcessor {
    public static function process(array $item)
    {
        print_r($item);
    }
}

$parser = new \JsonCollectionParser\Parser();
$parser->parse('/path/to/file.json', array('ItemProcessor', 'process'));
```


Instance method as callback:
```php
class ItemProcessor {
    public function process(array $item)
    {
        print_r($item);
    }
}

$parser = new \JsonCollectionParser\Parser();
$processor = new \ItemProcessor();
$parser->parse('/path/to/file.json', array($processor, 'process'));
```

## License
This library is released under [MIT](http://www.tldrlegal.com/license/mit-license) license.