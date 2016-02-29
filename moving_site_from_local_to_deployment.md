# [How to Move WordPress From Local Server to Live Site](http://www.wpbeginner.com/wp-tutorials/how-to-move-wordpress-from-local-server-to-live-site/)

-  Plugins: BackupBuddy, Duplicator, etc

## Manual method

### Step 1: Export Local WordPress Database

![](http://www.wpbeginner.com/wp-content/uploads/2013/02/export-tab-phpmyadmin.jpeg)


### Step 2: Uploading WordPress Files to Live Site

![](http://cdn.wpbeginner.com/wp-content/uploads/2013/06/uploadingwordpress.png)

### Step 3: Creating MySQL Database on Live Site

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/createdatabasecpanel.png)

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/createnewdb3.png)

![](http://cdn3.wpbeginner.com/wp-content/uploads/2013/06/newdbuser1.png)

### Step 4: Importing WordPress Database on Live Site

![](http://cdn4.wpbeginner.com/wp-content/uploads/2013/06/importingdb2.png)

### Step 5: Changing the Site URL

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/wpoptionsbrowse.jpg)

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/editsiteurlphpmyadmin.jpg)

### Step 6: Setting Up your Live Site


### Step 7: Fixing Images and Broken Links by updating Paths

```sql
UPDATE wp_posts SET post_content = REPLACE(post_content, 'localhost/test/', 'www.yourlivesite.com/');
```

![](http://www.wpbeginner.com/wp-content/uploads/2013/06/wpfiximageurls.png)
