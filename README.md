# WordPress notebook

- WordPress is a free and open-source content management system (CMS)
- based on PHP and MySQL
- installed on a web server
- Can have a local computer configured to act as its own web server hosting Wordpress for single-user testing or learning purposes
- Features include a plugin architecture and a template system
- The most popular blogging system in use on the Web, at more than 60 million websites

==

## Themes

- Check out the available free and paid themes
    - https://wordpress.org/themes/ 
    - http://themeforest.net/category/wordpress
    - https://thethemefoundry.com/wordpress-themes/
    - https://colorlib.com/wp/

    + e.g., a $60 theme [story-creative-responsive-multipurpose-theme/7824993](http://themeforest.net/item/story-creative-responsive-multipurpose-theme/7824993) 
        * ==> [http://lits.us/](http://lits.us/)

- Themes can be installed through the admin panel in a click, or they may need to be manually moved into the wp-content directory on the server.

### Some themes

#### simple
- [olsen-light](https://wordpress.org/themes/olsen-light/)
- [twentysixteen](https://wordpress.org/themes/twentysixteen/)
- [pblog](https://wordpress.org/themes/pblog/)

#### nice typography
- http://themeforest.net/item/elliot-clean-blogmagazine-wordpress-theme/full_screen_preview/12122349

#### with carousel / hero image
- [influence](https://wordpress.org/themes/influence/)
- [refur](https://wordpress.org/themes/refur/)
- [ving](http://divjot.co/ving/)
- [leadsurf-lite](https://wordpress.org/themes/leadsurf-lite/)
- [silk-lite](https://pixelgrade.com/demos/silk-lite/)
- [square](http://demo.hashthemes.com/square/)

==

## Migrating WP sites (2 main parts)

- 1- **Move the wp-content dir** content from initial destination to target destination
- 2- **Export the DB** from the old server and import it on the new server.

==

## Tutorials

There are plenty of good tuts online for installing, creating, and migrating with Wordpress.

- [http://www.wpbeginner.com/category/beginners-guide/](http://www.wpbeginner.com/category/beginners-guide/)
- [https://codex.wordpress.org/New_To_WordPress_-_Where_to_Start](https://codex.wordpress.org/New_To_WordPress_-_Where_to_Start)
- [https://thethemefoundry.com/blog/edit-wordpress-theme-html/](https://thethemefoundry.com/blog/edit-wordpress-theme-html/)

==

## [Moving WordPress](http://codex.wordpress.org/Moving_WordPress)
## [Moving a Root install to its own directory](http://codex.wordpress.org/Giving_WordPress_Its_Own_Directory#Using_a_pre-existing_subdirectory_install)

==

## Featured image
https://en.support.wordpress.com/featured-images/

==

## get the current URL
- https://wordpress.org/support/topic/how-to-get-the-url-of-the-page-you-are-on-with-php

```php
echo "http://" . $_SERVER['HTTP_HOST']  . $_SERVER['REQUEST_URI'];
```

==

## category title

### Displaying with the "Category:<category>" format
```
the_archive_title( '<h2 class="page-title">', '</h2>' );
```

### Displaying only the title
```
<h2 class="page-title"><?php single_cat_title(); ?></h2>
```

==

## [Function to check, if older/newer posts exist](https://wordpress.org/support/topic/function-to-check-if-oldernewer-posts-exist)

```php
if( get_next_posts_link() ) { do it }
if( get_previous_posts_link() ) { do it }
```

==

## Troubleshooting
- [images link broken](https://wordpress.org/support/topic/images-broken-on-all-but-home-page)

```
Reference images with an absolute path instead of a relative path:

I.e. in the widget on the top left:

<img src="/wp-content/uploads/orvis_166x95.gif"

or

<img src="http://www.yoursite.com/wp-content/uploads/orvis_166x95.gif"

instead of

<img src="wp-content/uploads/orvis_166x95.gif"
```

== 

## [Display most recent posts on static homepage](https://wordpress.org/support/topic/display-most-recent-posts-on-static-homepage-how)

```
<?php

global $post;

$myposts = get_posts('numberposts=5&category=1');

foreach($myposts as $post) :

?>

<?php the_title(); ?>

<?php the_content(); ?>

<?php endforeach; ?>
```

==

## [Get `<?php the_content(); ?>` as a string or turn it into a string](http://stackoverflow.com/questions/4405395/php-how-do-i-get-php-the-content-as-a-string-or-turn-it-into-a-strin)

