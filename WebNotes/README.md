# WordPress Site Rollout Guide  
## How To Move a Redesigned WordPress Site - Ready to Go live  

This is a *general* outline to help guide through the process of moving a production [WordPress](https://wordpress.com/) (WP) website to a *live-state*, when ready. This outline works for most sites, i.e. hosted in-house (standard) by [VistaGraphics Inc.](http://www.vistagraphicsinc.com/)  

This README is divided into two separate outlines: [Standard](#standard-wordpress-site-rollout) (hosted by VistaGraphics Inc., or *in-house*) and [Client-Hosted](#client-hosted-wordpress-rollout).  

For a WP site ready to go live, to be hosted by a client's means, skip the first section to see the [next section](#client-hosted-wordpress-rollout).  

***  

# **Standard** WordPress Site Rollout  

#### *10,000 ft.* Overview of *Standard* Steps:  
* Backup the Site Files & Database  
* Update permalinks  

# Backup the Website & Database  

It is always a good idea to make a copy of your website, before undergoing major changes. Below are steps for taking a *snapshot* of your website, Site Files and the Database.  

## Backup Site Files  

1. Open cPanel > File Manager  
2. Compress `public_html`  
3. Rename Zip folder (e.g. `sitename_oldsite_backup.zip`)  

## Backup Database  

1. From cPanel > phpMyAdmin  
2. Select Current Database Name (e.g. `lynchburg_wp1_db`)  
3. Select Export: export as `.sql`  

Download the site files and database backups, then upload to a safe place, i.e. `SYN_NAS0`, or `Grandma's House`.  

# The Going-Live Bit  

In order to make the website "live", all links must point to the correct Domain.  

## Update Site Links  

1. With current database selected, select `wp_options`  
2. Remove `/wp` from all links (*Show All Rows*)  

***  

<center>  

## **Alternatively**  
 In contrast to the steps above, open the `.sql` file in your favorite text editor and perform a search/replace and save. Then, import the database. However,  
 **ENSURE YOU DOWNLOAD A SEPARATE DATABASE BACKUP FILE** (an *unedited* database file)  
 If anything goes awry, you can restore the database from the backup (snapshot)  
</center>  

***  

3. Back in cPanel, open `public_html`, make note of the files below:  
    * `cgi-bin`  
    * `htaccess` (if there is one)  
    * `google code`  
    * `sitemapxml`  
4. Delete all files **except the above** in the `public_html` directory   
5. Open `wp` directory,  
    Select All > Move To `public_html`  

6. Navigate through live site, check where links need to be updated (i.e. remove any `/wp`, URLS pointing to vg server)  

#### Common Areas to Check for Step #6:  
* Widgets  
* Media  
* Pages  
* Custom Templates  

***  

# **Client-Hosted** WordPress Rollout  

## GoDaddy  
*Note: the following guide is for a client already hosting through GoDaddy.*  

#### *10,000 ft.* Overview of *Client-Hosted* Steps:  

* Backup the Site Files & Database  
* Backup the client's current site files (and database, if there is one)  
* Update permalinks  
* Update the programming language of the environment (PHP) to match closest to that of the production site, and Apache (if need be)  

***  

## HostGator  

### Scenario: *redesigned* WordPress project housed in `/wp` directory  

#### *10,000 ft.* Overview:  

* Download the *live* database, place the `.sql` file into the *live* `public_html` directory  
* Compress `public_html` **--> omitting** `cg-bgin` **from the compression**  
* Use Search & Replace plugin on the `/wp` project; in order to remove any url instance of `/wp` and `/wp/`  
* Compress `/wp` folder  
* Delete uncompressed "live" site files (`public_html` contents **--> omitting** `cg-bin`)  
* Extract `/wp` folder contents to `public_html`  
* Have a beer  
