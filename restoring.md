# Restoring a WP site

## Manual method
### A: The WP site
1. Using Cyberduck, connect to the site's server.
2. Upload and overwrite the directory `homedir/public_html/` with a backup.

### B: The WP database
1. On the server's cPanel, open phpMyAdmin.
2. Import a backup `.sql` file.

==

## Resources

- [How to Restore WordPress from Backup](http://www.wpbeginner.com/beginners-guide/beginners-guide-how-to-restore-wordpress-from-backup/)
