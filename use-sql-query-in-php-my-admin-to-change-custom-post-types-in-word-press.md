# Use SQL Query In phpMyAdmin To Change Custom Post Types in WordPress

This tutorial shows you how to run a sql query on a specific database in phpMyAdmin.

This SQL Query changes the name of a custom post type from portfolio to photos which i tested in phpMyAdmin.

Once you login to phpMyAdmin:

1. Select the database from the left hand sidebar you want to run the query in.
2. Click SQL from the top menu
3. Copy the following line of code from the view raw link in the Gist and paste it into the RUN query box.
4. Make sure you change the names for each post type type to your own.

Note: Please take a full database export (backup) before running any SQL Queries.

```sql
UPDATE  `wp_posts` SET  `post_type` =  'photos' WHERE  `post_type` = 'members';
```

And here’s an example of using the above query to change the name of CPT’s from portfolio to photos. ( Click Image To Enlarge ).