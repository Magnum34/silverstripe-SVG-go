# SilverStripe SVG GO

Basic SVG support for SilverStripe

## Requirements
SilverStripe 4 or higher

## Installation
```composer require magnum34/silverstripe-svg-go```

## License
MIT license. See the LICENSE file for more details.

#### Examples


```php

use Magnum34\SilverStripeSVGGO\Models\IconSVG

class CustomPage extends Page {
    
    
    private static $many_many = [
        'Icon' => IconSVG::class
    ];
    
    public function getCMSFields()
    {
        $fields =  parent::getCMSFields();
        $select = AjaxSelect2Field::create('IconID','Icon');
        $select->setConfig('multiple',false);
        $select->setConfig('resultsFormat', '<strong>$Title</strong><br />$Thumbnail');
        $select->setConfig('classToSearch', IconSVG::class);
        $select->setConfig('minimumInputLength', 0);
        $select->setConfig('placeholder', 'Search for a Icon...');
        $select->setConfig('selectionFormat', '<strong>$Title </strong>');
        $fields->addFieldToTab('Root.Icon',$select);
        $fields->addFieldToTab('Root.Icon',
                    HasOneButtonField::create($this, 'Icon',"Icon",'Icon (only .svg, .png, .jpg, .jpeg)'),
                    'Content');
        
        
        
        return $fields;
        
    }

}

``` 
