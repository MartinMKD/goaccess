GoAccess [![Build Status](https://secure.travis-ci.org/allinurl/goaccess.png?branch=master)](http://travis-ci.org/allinurl/goaccess)
========

## What is it? ##
GoAccess is an open source **real-time web log analyzer** and interactive viewer that **runs in a terminal in *nix systems**. It provides fast and valuable HTTP statistics for system administrators that require a visual server report on the fly.
More info at: http://goaccess.prosoftcorp.com/ 

![GoAccess Main Dashboard](http://goaccess.prosoftcorp.com/images/goaccess_screenshot1M-03L.png?1387168716)

## Features ##
GoAccess parses the specified web log file and outputs the data to the X terminal. Features include:

* General Statistics, bandwidth etc.
* Time taken to serve the request _(useful to track pages that are slowing down your site)_
* Top Visitors
* Requested files
* Requested static files, images, swf, js, etc.
* Referrers URLs
* 404 or Not Found
* Operating Systems
* Browsers and Spiders
* Hosts, Reverse DNS, IP Location
* Geo Location - Continents/Countries
* HTTP Status Codes
* Referring Sites
* Keyphrases
* Ability to output JSON and CSV
* Support for IPv6
* Different Color Schemes
* Unlimited log file size
* Custom log format
* Output statistics to a file.

### Nearly all web log formats... ###
GoAccess allows any custom log format string. Predefined options include, but not limited to:

* Common Log Format (CLF) Apache
* Combined Log Format (XLF/ELF) Apache | Nginx
* W3C format (IIS).
* Amazon CloudFront (Download Distribution).
* Apache virtual hosts

## Why GoAccess? ##
The main idea behind GoAccess is being able to quickly analyze and view web server statistics in real time without having to generate an HTML report. Although it is possible to generate an (HTML|JSON|CSV) report, by default it outputs to a terminal.

You can see it more as a monitor command tool than anything else.

## Installation ##
GoAccess can be compiled and used on Linux, OSX, OpenBSD, NetBSD, FreeBSD.

Download, extract and compile GoAccess with:

    $ wget http://downloads.sourceforge.net/project/goaccess/0.7/goaccess-0.7.tar.gz
    $ tar -xzvf goaccess-0.7.tar.gz
    $ cd goaccess-0.7/
    $ ./configure --enable-geoip --enable-utf8 
    $ make
    # make install
    
### Build from GitHub (Development) ###

    $ git clone https://github.com/allinurl/goaccess.git 
    $ cd goaccess 
    $ autoreconf -fi 
    $ ./configure --enable-geoip --enable-utf8 
    $ make
    # make install

## Usage ##
The simplest and fastest usage would be:

    # goaccess -f access.log
    
That will generate an interactive text-only output.

To generate an HTML report:

    # goaccess -f access.log -a > report.html
    
To generate full statistics we can run GoAccess as:

    # goaccess -f access.log -a

The `-a` flag indicates that we want to process an agent-list for every host parsed. The `-c` flag will prompt the date and log format configuration window. Only when curses is initialized.

Now if we want to add more flexibility to GoAccess, we can do a series of pipes. For instance:

If we would like to process all `access.log.*.gz` we can do:

    # zcat access.log.*.gz | goaccess 
    OR
    # zcat -f access.log* | goaccess
    
Another useful pipe would be filtering dates out of the web log

The following will get all HTTP requests starting on 05/Dec/2010 until the end of the file.

    # sed -n '/05\/Dec\/2010/,$ p' access.log | goaccess -a

For more examples, please check GoAccess' man page: 
http://goaccess.prosoftcorp.com/man

## Contributing ##

Any help on GoAccess is welcome. Feel free to use the Github issue tracker and pull requests to discuss and submit code changes.


Enjoy!
