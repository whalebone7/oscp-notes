# Checklist http

## Simple navigation
Try with a browser, what site is it?

## header discovery
Search os / server infos on response headers
What is the server vesion?
What is the server side language (java, php, perl, ...)

## https
Is there https domain? same content with no https?

## Interesting files
Is there a robots.txt? What pages are listed?
sitemap.xml?
feed/rss?

## other methods
POST/PUT/DELETE for webdav?
Bogus methods?

## known CMS

### If the CMS is a vendor-specific
What is the CMS and the version?
can we get the code? What are the interesting files (ie : files that give the CMS version)
what are all the default credentials?
any exploits? LFI, SQLI?
any file upload? What is the folder where files are uploads? Is it 777 ?
Is there any default dir or a renommed dir (ie : cuppa/alert -> administrator/alert)

### Unknow CMS
Explore the code, search for problems.

## gobuster
Search for the good dico on seclists. search RECURSIVELY with dirb.
Make a dico with cewl can be useful too.
Useful extensions to scan : txt,html,php,zip,tar

## nikto
Very noise, but can find some other problems. Take care of the bandwitch on production environments.

## online attack
For example with wordpress, try a wp-scan and a brute force dict attack.
With hydra, test with a little dictionnary to ensure that the login is correct (sometimes / is different than /index.php)

