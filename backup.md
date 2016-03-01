# Back up WP sites

- A good practice before any major change.
- A requirement of migrating your WordPress installation.
- Keep these backups in a unique folder on your computer called something like `website backups`.

## Things to be backed up
- 1. WordPress website files
- 2. WordPress database（mysql）

## A few different ways
- Manual
- On the web host's cPanel
- Using a plugin

==

## Manual method
- IMPORTANT: Manual backups need to be manually restored.

### Step 1: Back Up the Website’s Files
- Connect to the web host.
- Copy (download) all files under the website's directory to the local computer.
- IMPORTANT: This includes the hidden file `.htaccess`

![](http://mainwpex.wpengine.netdna-cdn.com/wp-content/uploads/FTP-Transfer1.png)

![](http://viral-community.com/wp-content/uploads/2013/11/hacking-protect-plan8-1.jpg)

![](http://viral-community.com/wp-content/uploads/2013/11/hacking-protect-plan8-2.jpg)

--

### Step 2: Export The WordPress Database
- Login to the cPanel and open the phpMyAdmin. 
- Export the database that contains your WordPress installation.
- The default settings of a Quick export and the SQL format for the export are sufficient for what we need.

![](http://mainwpex.wpengine.netdna-cdn.com/wp-content/uploads/Database-Export.png)

==

## Backup using a plugin
- Can be restored by using the same plugin
- [7 Best WordPress Backup Plugins Compared (Pros and Cons)](http://www.wpbeginner.com/plugins/7-best-wordpress-backup-plugins-compared-pros-and-cons/)
- [11 Best Free Quality Backup Plugins for Protecting Your WordPress Site - WPMU DEV](https://premium.wpmudev.org/blog/free-quality-backup-plugins/#)

==

## Resources
- [wordpressのバックアップ方法（mysqlとファイル一式)](http://viral-community.com/wordpress/wordpress-backup-5336/)
- [A Step By Step Guide to Migrating Your WordPress Website To A New Web Host](http://www.wpexplorer.com/migrating-wordpress-website/)

