# [How to Move WordPress From Local Server to Live Site](http://www.wpbeginner.com/wp-tutorials/how-to-move-wordpress-from-local-server-to-live-site/)

-  Plugins: 
    +  BackupBuddy, 
    +  Duplicator, etc

==

## Manual method 1

### Step 1: Export Local WordPress Database
1. Open phpMyAdmin.
2. Click on Export tab.
3. In the Export Method option choose custom.
4. Select all tables to export and `gzipped` for compression.
5. Press the Go button to export database.

![](http://www.wpbeginner.com/wp-content/uploads/2013/02/export-tab-phpmyadmin.jpeg)

### Step 2: Uploading WordPress Files to Live Site
1. Open an FTP client and connect to your live site.
2. Upload the files in the `public_html` directory.

![](http://cdn.wpbeginner.com/wp-content/uploads/2013/06/uploadingwordpress.png)

### Step 3: Creating MySQL Database on Live Site
1. Create a database by entering a name for your database.
2. Scroll down to MySQL users section and create or add an existing user to the database.
3. Set MySQL privileges for that user. Simply grant all privileges to the user.

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/createdatabasecpanel.png)

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/createnewdb3.png)

![](http://cdn3.wpbeginner.com/wp-content/uploads/2013/06/newdbuser1.png)

### Step 4: Importing WordPress Database on Live Site
1. Go to the cPanel dashboard.
2. Open phpMyAdmin. (==>phpMyAdmin will show your new database with no tables)
3. Click on the Import tab.
4. Click on choose file button and then select the gzipped database file from Step 1.
5. Press Go button. (==>phpMyadmin will now import your WordPress database)

![](http://cdn4.wpbeginner.com/wp-content/uploads/2013/06/importingdb2.png)

### Step 5: Changing the Site URL
1. Look for the `wp_options` table in the database that was just imported in step 4.
2. Browse the `wp_options` table.
3. Under the field `options_name`, look for `siteurl`.
    1. Click the `Edit Field` icon which can be found at the far left at the beginning of the row.
    2. Find the input box for `option_value` with the URL of your local install something like `http://localhost/***`.
    3. Insert the new site URL in that field, like `http://www.example.com`.
    4. Save the field by clicking the Go button.
4. Under the field `options_name`, look for `home`.
    1. Update the `home` url to be the same as the `siteurl`.
5. ==>Now, all of our content should be uploaded.

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/wpoptionsbrowse.jpg)

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/editsiteurlphpmyadmin.jpg)

### Step 6: Setting Up WordPress on your Live Site
- Your site should be showing an Error Establishing Database Connection error. 

1. Connect to your website using an FTP client.
2. Edit the `wp-config.php` file:
    - Provide the **Database name**, **User** and **Password** that are created in Step 3.
3. Save the `wp-config.php` file and upload it back to the server. 
    - ==>Visit your website, and it should be live now.
4. Login to the WordPress admin panel.
5. Go to `Settings > General`.
6. Click save.
    - ==>This will ensure that the site url is corrected anywhere else that needs to be.
7. Go to `Settings > Permalink`.
8. Click save.
    - ==>This will ensure that all post links are working fine.

### Step 7: Fixing Images and Broken Links by updating Paths
IMPORTANT: Whenever you are moving a WordPress site from one domain to another, or from local server to a live site, you would face broken links and missing images issue. You can either use the SQL query or use the [Velvet Blues](https://wordpress.org/plugins/velvet-blues-update-urls/) WordPress plugin.

1. Go to phpMyAdmin.
2. Click on the database.
3. Click on the SQL tab.
4. Write this query with your own local site and live site URLs.

```sql
UPDATE wp_posts SET post_content = REPLACE(post_content, 'localhost/test/', 'www.mylivesite.com/');
```

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/wpfiximageurls.png)

==

## Manual method 2
- I tried this to duplicate a site to the local environment.

### Step 1: Export the WordPress content on the old dashboard
- [How to Export and Import a Wordpress Blog](http://www.wikihow.com/Export-and-Import-a-Wordpress-Blog)

### Step 2: Create a new database in the destination

### Step 3: Create a new WordPress project directory in the destination
- Do the five minute install process.

### Step 4: Copy paste and override the files with the old ones
- Except: `.htaccess` and `wp-config.php`

### Step 5: Import the WordPress content on the new dashboard

==
