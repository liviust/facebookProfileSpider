# facebookProfileSpider

A Python spider using **[Selenium](http://www.seleniumhq.org/)** to crawl [Facebook](http://www.facebook.com) user profile information such as first name,last name,work information,education information and etc,and output the information into a csv file.

## About
As we know,the page contents of [Facebook](http://www.facebook.com) are created by many [Javascript](http://www.w3schools.com/js/) plugins, thus we can not simply crawl the data using [Regex](http://www.regexr.com/) or [Scrapy](http://scrapy.org/) framework.We need to use **[Selenium](http://www.seleniumhq.org/)** to simulate a web browser action and then get data from it. Using **[Selenium](http://www.seleniumhq.org/)** may cost time but it will be the most effective way to crawl from these sites such as [Facebook](http://www.facebook.com) or [Taobao](http://www.taobao.com).

This project had batter to be run at Eclipse on Win7,but will add support to Ubuntu and let it can run on the Linux terminal later.

## Require
1. Python2.7
2. Selenium 2.42.1
3. [BeautifulSoup 4.3.2](http://www.crummy.com/software/BeautifulSoup) 
4. urllib2
5. A stable **VPN** account if you are in the mainland China.
6. Jdk1.6+
7. Eclipse

## Usage
First,ensure you can access to [Facebook](http://www.facebook.com) freely and quickly,then run the ***facebookSpider.py*** to make this project run,then it will login to [Facebook](http://www.facebook.com) automatically and crawl data from the specified URLs one by one.

All the urls are written in the *urls.py* file.All the configuration items are written in the *settings.py* file.

## Note

Some guys told me that they have a problem when run this application,this is because you have not set the `User-Agent` correctly when running.

In the [facebookLogin.py](https://github.com/lucumt/facebookProfileSpider/blob/master/fpspider/src/facebookLogin.py),change the `User-Agent`data depends on which browser you are using.Only if you have set the correctly value for it,your Selenium can run normaly.

    def __init__(self):
        '''
        Constructor
        '''
        cookie=cookielib.CookieJar()
        opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookie))
        # change to User-Agent depends on your own account and browser data,and do not use it directly!
        opener.addheaders = [('Referer', 'http://login.facebook.com/login.php'),
                            ('Content-Type', 'application/x-www-form-urlencoded'),
                            ('User-Agent', 'Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7 (.NET CLR 3.5.30729)')]
        self.opener=opener

The `User-Agent` is used to avoid login to Facebook each time when fetch data from Facebook,if you do not know how to set it, **just Google!**