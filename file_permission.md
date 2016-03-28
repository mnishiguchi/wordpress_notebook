# [File Permissions](https://codex.wordpress.org/Changing_File_Permissions)

- All files should be owned by the actual user's account, not the user account used for the httpd process.
- Group ownership is irrelevant, unless there's specific group requirements for the web-server process permissions checking. This is not usually the case.
- All directories should be 755 or 750.
- All files should be 644 or 640. Exception: wp-config.php should be 440 or 400 to prevent other users on the server from reading it.
- IMPORTANT: No directories should ever be given 777, even upload directories. Since the php process is running as the owner of the files, it gets the owners permissions and can write to even a 755 directory.
