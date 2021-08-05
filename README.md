# htaccess
Simple commands to insert in .htaccess

#301 Redirects for .htaccess
#Redirect a single page:
Redirect 301 /pagename.php http://www.domain.com/pagename.html

#Redirect an entire site:
Redirect 301 / http://www.domain.com/

#Redirect an entire site to a sub folder
Redirect 301 / http://www.domain.com/subfolder/

#Redirect a sub folder to another site
Redirect 301 /subfolder http://www.domain.com/
