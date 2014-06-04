Python Email Crawler
====================

This python script search/google certain keywords, crawls the webpages from the results, and return all emails found.

Requirements
------------

- sqlalchemy
- urllib2

If you don't have, simply `sudo pip install sqlalchemy`. 


Usage
-------

Start the search with a keyword. We use "iphone developers" as an example.

	python email_crawler.py "iphone developers"

After the process finished, run this command to get the list of emails

	python email_crawler.py --emails

The emails will be saved in ./data/emails.csv


Additional Info
---------

The search and crawling process can take up to 24 hours, as it retrieve up to 500 search results (from Google), and crawl up to 2 level deep. It should crawl around 10,000 webpages. You can modify the number: 500 to retreive more, but make sure that you don't ask to retreive more than 640 searches.

If you run 2 instances of this script or try to get more than 640 queries, you will end up with this:

	python email_crawler.py "iphone developers"
	[17:47:15] INFO::email_crawler - ----------------------------------------
	[17:47:15] INFO::email_crawler - Keywords to Google for: iphone developers
	[17:47:15] INFO::email_crawler - ----------------------------------------
	[17:47:15] INFO::email_crawler - Crawling http://www.google.com/search?q=iphone+developers&start=0
	[17:47:19] ERROR::email_crawler - Exception at url: http://www.google.com/search?q=iphone+developers&start=0
	HTTP Error 503: Service Unavailable
	[17:47:19] ERROR::email_crawler - EXCEPTION: expected string or buffer 
	Traceback (most recent call last):
	  File "email_crawler.py", line 212, in <module>
	    crawl(arg)
	  File "email_crawler.py", line 65, in crawl
	    for url in google_url_regex.findall(data):
	TypeError: expected string or buffer

You will be able to start a new query in about 1 hour of the first time you got this error.

Change the Google
--------------------

For those who are not tech savy or don't know python, you can simply change the default google.com to whatever google you want just by changing the google url in line 62 of email_crawler.py from (example):

	url = 'http://www.google.com/search?
	
to

	url = 'http://www.google.com.au/search?

ORIGINAL AUTHOR AND REPO
---------------------------
samwize from Github: https://github.com/samwize/python-email-crawler