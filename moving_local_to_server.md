# [Moving WordPress From Local Server to Live Site](http://www.wpbeginner.com/wp-tutorials/how-to-move-wordpress-from-local-server-to-live-site/)

## Plugins: 
- BackupBuddy, 
- Duplicator, etc

==

## Manual method

--

### Step 1: Export Local WordPress Database
#### 1. Open phpMyAdmin.
#### 2. Click on Export tab.
    + Export Method: custom.
    + Tables: Select all the tables to export
    + Output:
        * Compression: `gzipped`

#### 3. Press the **Go** button to export database.

![](http://www.wpbeginner.com/wp-content/uploads/2013/02/export-tab-phpmyadmin.jpeg)

--

### Step 2: Upload WordPress project files to live server
#### 1. Open an FTP client and connect to the live server.
#### 2. Upload the project files to the live server's `public_html` directory.

![](http://cdn.wpbeginner.com/wp-content/uploads/2013/06/uploadingwordpress.png)

--

### Step 3: Create MySQL Database on live server
#### 1. Go to the cPanel dashboard
#### 2. Open MySQL Databases

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/createdatabasecpanel.png)

#### 3. Create a database
- Entering a database name

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/createnewdb3.png)

#### 4. Create or add an existing user to the database.
#### 5. Set MySQL privileges for that user
- Simply grant all privileges to the user.

![](http://cdn3.wpbeginner.com/wp-content/uploads/2013/06/newdbuser1.png)

--

### Step 4: Import WordPress Database to live server
#### 1. Go to the cPanel dashboard.
#### 2. Open phpMyAdmin, which will show the new database with no tables.
#### 3. Click on Import tab.
- File to Import:
    + Choose the gzipped database file from Step 1.

#### 4. Press Go button to import

![](http://cdn4.wpbeginner.com/wp-content/uploads/2013/06/importingdb2.png)

--

### Step 5: Change the site URL in the database
#### 1. Look for the `wp_options` table in the database.
![](http://www.wpbeginner.com/wp-content/uploads/2013/06/wpoptionsbrowse.jpg)

#### 2. Under the field `options_name`, look for `siteurl` and `home`.
* Update `siteurl`'s option_value to the new site URL, like `http://www.example.com`.
* Update `home`'s option_value to the same URL.

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/editsiteurlphpmyadmin.jpg)

- NOTE:
    + Now, all of our content should be uploaded.
    + But our site should be showing an Error Establishing Database Connection error. 

--

### Step 6: Set Up WordPress on live server

#### 1. Edit the `wp-config.php` file on the live website
```php
define('DB_NAME', 'database-name');
define('DB_USER', 'database-username');
define('DB_PASSWORD', 'database-password');
define('DB_HOST', 'localhost');
```

- NOTE: 
    + Provide info that are created in Step 3.
    + `DB_HOST` must be `localost` for some online web hosting services.
    + Visit the website, and it should be live now.

--

### Step 7: Initialize the URL and permalink on the WordPress admin panel
#### 1. Login to the WordPress admin panel
#### 2. Go to `Settings > General`.
#### 3. Click save
- NOTE: This will ensure that the site url is corrected anywhere else that needs to be.

#### 4. Go to `Settings > Permalink`.
#### 5. Click save.
- NOTE: This will ensure that all post links are working fine.

--

### Step 8: Fix Images and groken Links by updating Paths
IMPORTANT: Whenever you are moving a WordPress site from one domain to another, or from local server to a live site, you would face broken links and missing images issue. You can either use the SQL query or use the [Velvet Blues](https://wordpress.org/plugins/velvet-blues-update-urls/) WordPress plugin.

#### 1. Go to phpMyAdmin.
#### 2. Click on the database.
#### 3. Click on the SQL tab.
#### 4. Write this query with your own local site and live site URLs.

```sql
UPDATE wp_posts SET post_content = REPLACE(post_content, 'localhost', 'www.mylivesite.com/');
```

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/wpfiximageurls.png)

==

## Troubleshooting

### Cannnot access /wp-admin/
- Check the `WP-config.php` file
    + `WP-Config.php` is probably the single most important file in your entire WordPress installation.
    + This is where you specify the details for WordPress to connect your database.
    + If you changed your root password, or the database user password, then you will need to change this file as well. First thing you should always check is if everything in your wp-config.php file is the same. 
- [How to Fix the Error Establishing a Database Connection in WordPress](http://www.wpbeginner.com/wp-tutorials/how-to-fix-the-error-establishing-a-database-connection-in-wordpress/)

```php
define('DB_NAME', 'database-name');
define('DB_USER', 'database-username');
define('DB_PASSWORD', 'database-password');
define('DB_HOST', 'localhost');
```
