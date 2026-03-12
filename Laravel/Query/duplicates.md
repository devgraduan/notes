# Duplicates

## Find duplicates

```php

$duplicates = \DB::table('articles')
    ->select('id', 'title')
    ->groupBy('title') // duplicate column
    ->havingRaw('COUNT(*) > 1')
    ->get();

```

```php

use Illuminate\Support\Facades\DB;

$duplicates = DB::table('products')
    ->select('title', DB::raw('COUNT(*) as count')) // Select the column(s) to check and count them
    ->groupBy('title') // Group by the selected column(s)
    ->havingRaw('COUNT(*) > 1') // Filter for groups where the count is more than 1
    ->get();


```