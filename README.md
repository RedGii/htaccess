# htaccess
Simple commands to insert in .htaccess

## 301 Redirects for .htaccess
### Redirect a single page
Redirect 301 /pagename.php http://www.domain.com/pagename.html

### Redirect an entire site
Redirect 301 / http://www.domain.com/

### Redirect an entire site to a sub folder
Redirect 301 / http://www.domain.com/subfolder/

### Redirect a sub folder to another site
Redirect 301 /subfolder http://www.domain.com/

## Security
### Prevent Access to .htaccess
<Files .htaccess>
        Order allow,deny
        Deny from all
</Files>

### Redirect to HTTPS
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI} [R,L]

### Disable directory browsing
Options All -Indexes

### Enable directory browsing
Options All +Indexes

### Block IP range by address
<Limit GET POST PUT>
        Order allow,deny
        Allow from all
        Deny from 99.88.77.66
        Deny from 99.88.77.*
        Deny from 99.88.*.*
        Deny from 99.*.*.*
</Limit>

### Block two unique IP addresses
Deny from 99.88.77.66 11.22.33.44

### Stop hotlinking and serve alternate content
<IfModule mod_rewrite.c>
        RewriteEngine on
        RewriteCond %{HTTP_REFERER} !^$
        RewriteCond %{HTTP_REFERER} !^http://(www\.)?domain\.co
        RewriteRule .*\.(gif|jpg)$ http://www.domain.com/eatme.
</ifModule>

### Protect against denial-of-service (DOS) attacks (limiting file upload size)
LimitRequestBody 10240000

### Secure directory by disabling script execution
AddHandler cgi-script .php .pl .py .jsp .asp .htm .shtml .sh .c
Options -ExecCGI

## Performance
### Disable the Server Signature
ServerSignature Off

### Set the server timezone
SetEnv TZ America/Washington

### Set the default language
DefaultLanguage it-IT

### Enabling File Caching for one week
<FilesMatch ".(js|css|pdf|txt)$">
        Header set Cache-Control "max-age=604800"
</FilesMatch>

### Disable caching for scripts and dynamic files
<FilesMatch "\.(pl|php|cgi|spl|scgi|fcgi)$">
        ExpiresActive Off
</FilesMatch>
