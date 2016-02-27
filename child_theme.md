# Child theme
- A child theme consists of at least:
    + The child theme directory
    + style.css
    + functions.php
- IMPORTANT: The only required child theme file is `style.css`, but `functions.php` is necessary to enqueue styles correctly.

## Creating a Child theme

### 1- create the child theme directory
- `wp-content/themes/<parent-theme-name>-child/`

### 2- create the child theme's stylesheet (`style.css`)
- The stylesheet must begin with [the stylesheet header](https://codex.wordpress.org/Theme_Development#Theme_Stylesheet)
- The `Template` line corresponds to **the directory name of the parent theme**

### 3- enqueue the parent and child theme stylesheets
- Add a `wp_enqueue_scripts` action and use `wp_enqueue_style()` in the child theme's `functions.php`
