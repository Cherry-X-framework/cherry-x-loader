# Cherry X framework loader

## How to use:

1. Copy and include this class into your theme/plugin
2. Add unique prefix for the `CX_Loader` class name, e.g. - `Twentyseventeen_CX_Loader`
3. Initialize loader on `after_setup_theme` hook with priority `-20`, Example:

```php
add_action( 'after_setup_theme', 'twentyseventeen_framework_loader', -20 );

function twentyseventeen_framework_loader() {
    require get_theme_file_path( 'framework/loader.php' );
    new Twentyseventeen_CX_Loader(
        array(
            get_theme_file_path( 'framework/modules/module-1/module-1.php' ),
            get_theme_file_path( 'framework/modules/module-2/module-2.php' ),
            get_theme_file_path( 'framework/modules/module-3/module-3.php' ),
        )
    );
}
```
## Notes:

1. This class only select latest version of each module from all Cherry X framework instances loaded in current environment
2. You should manually initialize selected modules later, when them will be needed you, but not earlier than `after_setup_theme` hook with priority 0.
