# Back up WP sites

- [wordpressのバックアップ方法（mysqlとファイル一式)](http://viral-community.com/wordpress/wordpress-backup-5336/)
- [A Step By Step Guide to Migrating Your WordPress Website To A New Web Host](http://www.wpexplorer.com/migrating-wordpress-website/)
- 定期的に、Wordpressのバックアップをとっておくことは、必要不可欠。
    + うっかりWordPressのファイル・フォルダを削除
    + 外部からのハッキング攻撃
- Back up every aspect of your site.
- This step is good practice before any major change.
- It is also a requirement of migrating your WordPress installation.
- Many plugins out there that will completely backup your site for you.

## バックアップ対象データ(二つ)
- 1. WordPress・Webサイトのファイル一式
- 2. WordPressのデータベース（mysql）

==

## Manual method

### Step 1: Back Up Your Website’s Files
- Connect to your web host
- Copy (download) all files under your website's directory to your local computer
- IMPORTANT: This includes the hidden file `.htaccess`

![](http://mainwpex.wpengine.netdna-cdn.com/wp-content/uploads/FTP-Transfer1.png)

![](http://viral-community.com/wp-content/uploads/2013/11/hacking-protect-plan8-1.jpg)

![](http://viral-community.com/wp-content/uploads/2013/11/hacking-protect-plan8-2.jpg)

--

### Step 2: Export The WordPress Database
- Login to the cPanel account of your web server and open the phpMyAdmin. 
- Export the database that contains your WordPress installation.
- The default settings of a Quick export and the SQL format for the export are sufficient for what we need.

![](http://mainwpex.wpengine.netdna-cdn.com/wp-content/uploads/Database-Export.png)

==

## Backup using a plugin

TODO


