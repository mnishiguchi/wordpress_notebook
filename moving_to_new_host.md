# Moving a WP site to a new web host

- [A Step By Step Guide to Migrating Your WordPress Website To A New Web Host](http://www.wpexplorer.com/migrating-wordpress-website/)
- [Migrating WordPress Across Hosts, Servers and URLs](http://code.tutsplus.com/tutorials/migrating-wordpress-across-hosts-servers-and-urls--wp-20104)
- [Migrating A WordPress Site – Step By Step](http://wordpress.mcdspot.com/2012/08/22/migrating-a-wordpress-site-step-by-step/)
- [HOW TO MIGRATE WORDPRESS TO A NEW HOST](https://www.godaddy.com/garage/webpro/wordpress/how-to-migrate-wordpress-to-a-new-host/)

## Manual method

### Step 1: Back Up Your Website’s Files
- Back up every aspect of your site.
- This step is good practice before any major change.
- It is also a requirement of migrating your WordPress installation.
- Many plugins out there that will completely backup your site for you.

![](http://mainwpex.wpengine.netdna-cdn.com/wp-content/uploads/FTP-Transfer1.png)

### Step 2: Export The WordPress Database
- Login to the cPanel account of your web server and open the phpMyAdmin. 
- Export the database that contains your WordPress installation.
![](http://mainwpex.wpengine.netdna-cdn.com/wp-content/uploads/Database-Export.png)
- The default settings of a Quick export and the SQL format for the export are sufficient for what we need.

### Step 3: Create The WordPress Database On Your New Host Server
- Login to your new web host with the user credentials they have supplied you and connect to the cPanel software.
- Create a new database table
    + Open MySQL Database and create a new database with an appropriate name for your website.
    + Create a new MySQL user (with a secure password).
    + Add this user account to the new database and grant it All Privileges.
- Write down the database name, the new MySQL username and its password. You will need them soon.

### Step 4: Edit the `wp-config.php` File

1. Within the local copy of the project file, find `wp-config.php` that controls the access between WordPress and your database.

2. Make a copy of `wp-config.php` and store it in another folder on your local computer. This is necessary for restoring the changes we are about to make should something go wrong later.

3. Open the original `wp-config.php` with a text editor and make the following three changes:
    + **Change The Database Name**
        * Find `define('DB_NAME', 'db_name');`
        * The db_name portion of this line will currently be set to the MySQL database name of your old web host. This must be changed to the name of the new database you have just created.
    + **Change the Database Username**
        * Find `define('DB_USER', 'db_user');`
        * In this line you need to change the db_user portion from the username of your old host to match the new username you have just created.
    + **Change The Database User Password**
        * Find `define('DB_PASSWORD', 'db_pass');`
        * As with the others the db_pass section of this line must be changed to the new secure password you created for your MySQL user.

4. Save `wp-config.php` and close the file.

### Step 5: Import Your Database

![](http://mainwpex.wpengine.netdna-cdn.com/wp-content/uploads/Database-Import1.png)

- Launch `phpMyAdmin` from the cPanel on your new server.
- Select the new database from the list on the left hands sidebar.
- Select the Import tab from the navigation menu.
- **File to Import**
    - Click the Choose File button and select the SQL file you exported previously.
- **Format**
    - Un-tick the Partial Import check box.
    - Format: SQL.
- Click the Go button.

### Step 6: Upload The WordPress Files To Your New Host

- Connect to your new web host using your FTP program.
- Select the folder that your website is going to be held.
    - (If this is the primary, or only site being installed on this web server then uploading the files to the `public_html` folder is the usual directory.)
- Upload your website files that contains the updated version of `wp-config.php`.
- IMPORTANT: Don’t delete these files from your local computer once the upload finishes. They are still needed until the final steps have been completed.

### Step 7: Linking to New URL & Defining New Domain

- Update the Site URL and assets URLs.
- the [Search Replace DB script on github](https://github.com/interconnectit/Search-Replace-DB)
    - Allow you to do this with great ease. 
    - IMPORTANT: Run the search and replace on the new domain (not the old one).
    - IMPORTANT: DELETE it when your are done (for security reasons). 

### Step 8: Reconfigure your domain’s DNS settings
- DNS changes can take **up to 48 hours** to fully propagate.
- It’s best to do this at a period when you expect **lower levels of traffic**. 
- During this 48 hour window, **avoid making any changes to your website**.

### Step 9: Connect to your old web host to delete the files and database
- **After the 48-hour period has expired**, connect to your old web host to delete the files and database.
- IMPORTANT: Keep a local backup copy of these files and the database export, along with the original `wp-config.php` file in case you need to roll back the migration. It can be a good idea to hold onto these files for a an extended period just to be on the safe side.

==

## the `public_html` folder

- Only need to upload what’s inside the public_html folder.
- Everything outside is "generally" just server related files.
- But backup everything just in case.

==

## Troubleshooting
[Why is my database import losing text widget data?](http://wordpress.stackexchange.com/questions/9076/why-is-my-database-import-losing-text-widget-data)

[The requested URL /index.php was not found on this server](https://wordpress.org/support/topic/the-requested-url-indexphp-was-not-found-on-this-server-3)

[Changing The Site URL](http://codex.wordpress.org/Changing_The_Site_URL)

