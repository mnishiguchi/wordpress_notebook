# Set up WordPress locally (with MAMP + WordPress)
- https://codex.wordpress.org/Installing_WordPress_Locally_on_Your_Mac_With_MAMP
- https://premium.wpmudev.org/blog/develop-wordpress-locally-mamp/
- [MAMP](https://en.wikipedia.org/wiki/MAMP): Macintosh, Apache, MySQL, and PHP
- The default MAMP ports are:
    + 8888 for Apache
    + 8889 for MySQL

==

## Setup

### Install MAMP (first-time only)
- http://www.mamp.info/en/downloads/index.html

### Set MAMP document root (on an as-needed basis)
- Can be configured on the MAMP window.
- e.g., `/Users/masa/WordPressProjects/`

![](https://premium.wpmudev.org/blog/wp-content/uploads/2015/09/mamp-servers-working1.png)

### Download WordPress and rename it to a project directory
- Use the downloaded `wordpress` directory as a scaffold.
- Just copy it and rename it to make it a project directory.

### Create a database for the project
1. Start the MAMP Apache and MySQL servers.
2. Open phpMyAdmin on the MAMP web interface.
3. Under "Create new database", enter a database name and press "Create".

![](http://coolestguidesontheplanet.com/wp-content/uploads/2011/07/create-database-wordpress-phpmyadmin1.png)

### Run the WordPress 5-minute install
1. Visit the local WP project site (`http://localhost:8888/<project_dir>/`)
2. Enter the following information into the database setup form:

```
Database Name: <project_db_name>
User Name (database): root
Password (database): root
Database Host/server: localhost
Table Prefix: wp_
```

==

## The file structure of my local MAMP/WP environment

- MAMP document root: `/Users/masa/WordPressProjects/`
- WP project root: `/Users/masa/WordPressProjects/<project_dir>/`
- To access the WP project: `http://localhost:8888/<project_dir>/`
- To access the WP dashboard: `http://localhost:8888/<project_dir>/wp-admin/`
