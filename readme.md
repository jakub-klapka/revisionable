# Revisionable with custom Revision class

This repo is fork of [VentureCrafts Revisionable](https://github.com/VentureCraft/revisionable) with added ability, to define your own Revision class to Revisionable Trait.

This can be usefull, if you need to use different tables for different parts of your application.

For Revisionable documentation, refer to https://github.com/VentureCraft/revisionable

## Usage
First, creare your new model, which would extend Revision:
```php
<?php

namespace App\Models;

class Revision extends \Venturecraft\Revisionable\Revision {

	/**
	 * Use custom table for revisions
	 *
	 * @var string
	 */
	public $table = 'el_revisions';

}
```

Then, you can create new Revisionable Trait, which could define custom Revision class:

```php
<?php

namespace App\Providers;

trait RevisionableTrait {
	use \Venturecraft\Revisionable\RevisionableTrait;

	/**
	 * Overwrite Revision class
	 *
	 * @return string
	 */
	protected static function getRevisionModelPath() {
		return App\Models\Revision::class;
	}

}
```

In your models, just use your Trait, instead of! Revisionable.