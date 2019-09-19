# Dev

# symlink

goals.yml
```yml
siteApp:
  path: .
  public:
    site:
      media:
        gnt:
          symlink: '../../../vendor/codexten/gnt-core/media'
```
hidev.php

```php
<?php
return [
    'components' => [
        'include' => [
            __DIR__ . '/goals.yml',
        ],
    ],
];
```

command
```cmd
 ./vendor/bin/hidev deploy
```

