# IsDayOf

[![Latest Version](https://img.shields.io/badge/release-1.0.1-blue)](https://img.shields.io/badge/release-1.0.1-blue)
[![Downloads](https://img.shields.io/badge/downloads-3%E2%80%89443-blue)](https://img.shields.io/badge/downloads-3%E2%80%89443-blue)
[![Documentation](https://img.shields.io/badge/docs-yes-blue)](https://img.shields.io/badge/docs-yes-blue)

PHP SDK for [isdayof.ru](https://isdayoff.ru)

#### Instalation
```bash
composer require phptcloud/isdayoff-sdk
```


#### After install
You can check the work of the scripts in the "Examples" folder. ;)

#### Simple example

```php
require_once __DIR__ . '/../vendor/autoload.php';

use isDayOff\Client\IsDayOff;

$client = new IsDayOff();

$date = new DateTime('now');
$result = $client->date()->isDayOff($date);

if($result) {
    echo 'is day off.';
} else {
    echo 'working day.';
}
```

#### Filters


```php
// Countries
isDayOff\Filters\UkraineFilter
isDayOff\Filters\RussianFilter
isDayOff\Filters\KazakhstanFilter
isDayOff\Filters\BelorusFilter
isDayOff\Filters\UnitedStatesFilter
isDayOff\Filters\UzbekistanFilter
isDayOff\Filters\TurkeyFilter

// Additional
isDayOff\Filters\CovidFilter
isDayOff\Filters\PreHolidayFilter
```

#### Filters examples

```php
/**
 * New filter collection
 */
$filters = new FiltersCollection();
$filters->addOne(new UkraineFilter());

$client->date()->setFilters($filters);
$date = new DateTime('2019/01/01');

$result = $client->date()->getDataPerMonth($date);

print_r($result);
```