## mysite.farm

www.mysite.farm is the only reservered name

mysite.farm points to 127.0.0.1

*.mysite.farm points to 127.0.0.1

# Mamp Setup

## Include the Custom Virtual Hosts File

/Applications/MAMP/conf/apache/httpd.conf

Remove the comment on line 575

```
# Virtual hosts
Include /Applications/MAMP/conf/apache/extra/httpd-vhosts.conf
```

## Add virtual host

This will allow subdomains to work by simply adding a directory to /Applications/MAMP/htdocs

For instance test.mysite.farm will point to /Applications/MAMP/htdocs/test/ and mysite.farm will point to /Applications/MAMP/htdocs/

/Applications/MAMP/conf/apache/extra/httpd-vhosts.conf

```
<VirtualHost *:80>
    ServerName mysite.farm
    UseCanonicalName Off
    ServerAlias *.mysite.farm
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /Applications/MAMP/htdocs/*>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    VirtualDocumentRoot /Applications/MAMP/htdocs/%1
</VirtualHost>
```
