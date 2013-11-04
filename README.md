packrat
=======

Archives images from your Reddit.com saved links, del.icio.us bookmarks, and tumblr favorites.

## Features

* Archive your favorite images from the web
* Add multiple reddit, delicious, and tumblr accounts
* Download albums from imgur.com
* Run quietly or silently (for use in cron jobs)

## Installation and Setup

### Prerequisites

Packrat is a perl script, so you must have perl installed on your system. Packrat has been tested with Perl 5 in Cygwin, Windows (ActiveState), and Linux (Ubuntu and Slackware) environments.

Once you have perl installed, there are a few perl modules that you'll need prior to running packrat:

* [JSON::XS](http://search.cpan.org/~mlehmann/JSON-XS-3.01/XS.pm)
* [XML::Simple](http://search.cpan.org/~grantm/XML-Simple-2.20/lib/XML/Simple.pm)
* [LWP::UserAgent](http://search.cpan.org/~gaas/libwww-perl-6.05/lib/LWP/UserAgent.pm)
* [OAuth::Consumer](http://search.cpan.org/~mathias/OAuth-Consumer-0.03/lib/OAuth/Consumer.pm)
* [File::Slurp](http://search.cpan.org/~uri/File-Slurp-9999.19/lib/File/Slurp.pm)
* [File::Basename](http://search.cpan.org/~rjbs/perl-5.18.1/lib/File/Basename.pm)
* [DateTime](http://search.cpan.org/~drolsky/DateTime-1.03/lib/DateTime.pm)
* Getopt::Std

File::Basename and Getopt::Std are included with the standard Perl 5 distribution. The others are available from [CPAN](http://search.cpan.org).

### Installation

Once your environment is all set up, you're ready to run packrat. No installation is necessary. The first time you run packrat, you will be guided through the process of configuring it and granting access to your online accounts. All the necessary configuration files will be created where you tell packrat to create them.

## Usage

`packrat [-qrc /path/to/config]`   
`packrat [-s]`

There are four command line options that you can use with packrat:

* q - Supresses the normal "Checking" and "Downloading" messages that normally print when packrat is running. Errors (such as local file access errors or download failures) are still printed.
* s - Packrat runs completely silently. No errors or status messages are displayed at all.
* r - Forces the first-run configuration assistant to run.
* c - Specifies the configuration file to use. This option takes an argument in the form of a path to a configuration file.

## The .packraft.conf file

packrat's configuration file uses [JSON](http://www.json.org/) syntax because it's easy for Perl to interact with JSON, especially since it already uses the JSON::XS module to parse data from web APIs.  

You shouldn't need to manually update .packrat.conf, since packrat helps you set up the parameters, but if you do, here's an overview of those parameters:

**destination** - the path to the directory where downloaded images are stored  

**nonimage_file** - the path to the text file where URLs that are not direct links to images are written  

**failed\_urls\_file** - the path to the text tile where URLs that cannot be downloaded are written.  

**track_file** - the path to the text file where packrat keeps track of what likes/saved/bookmarks have been downloaded.  

**imgur\_auth\_id** - the ID string that permits packrat to access the imgur.com API  

**services** - object that contains up to three elements: tumblr, reddit, and delicious  

&nbsp;&nbsp;&nbsp;&nbsp;**tumblr** - array that contains un unlimited number of elements (one for each tumblr account added)  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**username** - the tumblr username for an account  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**consumer_key** - the OAuth consumer key for a tumble account  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**consumer_secret** - the OAuth consumer secret string for a tumbr account  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**token_key** - the OAuth token key for a tumblr account  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**token_secret** - the secret OAuth token for a tumblr account   

&nbsp;&nbsp;&nbsp;&nbsp;**reddit** - array that contains an unlimited number of elements (one for each reddit account added)  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**username** - the reddit username for an account  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**rss_url** - the private RSS URL for the saved links for a reddit account

&nbsp;&nbsp;&nbsp;&nbsp;**delicious** - array that contains an unlimited number of elements (one for each delicious account added)  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**username** - the delicious username for an account  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**password** - the delicious password for an account

### Sample .packrat.conf file

<pre>
{
    "destination": "/home/foo/packrat/new",
    "nonimage_file": "/home/foo/.packrat/nonimages",
    "failed_urls_file": "/home/foo/.packrat/failedurls",
    "track_file": "/home/foo/.packrat/packrat.track",
    "imgur_auth_id": "0000000000000000",
    "services": {
        "tumblr": [
            {
                "username": "tumblr_user_1",
                "consumer_key": "this_isn't_real",
                "consumer_secret": "this_isn't_real",
                "token_key": "this_isn't_real",
                "token_secret": "this_isn't_real"
            },
            {
                "username": "tumblr_user_2",
                "consumer_key": "this_isn't_real",
                "consumer_secret": "this_isn't_real",
                "token_key": "this_isn't_real",
                "token_secret": "this_isn't_real"
            }
        ],
        "reddit": [
            {
                "username": "reddit_user_1",
                "rss_url": "http://www.reddit.com/saved.json?feed=some_random_alpha_characters&user=reddit_user_1"
            },
            {
                "username": "reddit_user_2",
                "rss_url": "http://www.reddit.com/saved.json?feed=more_random_alpha_characters&user=reddit_user_2"
            }
        ],
        "delicious": [
            {
                "username": "delicious_user",
                "password": "delicious_password"
            }
        ]
    }
}
</pre>

## Bugs

Many, I'm sure. If you run across something, or if you have a suggestion, please open a bug or enhacement request at the [github page](https://github.com/paulburton0/packrat/issues), or email me at <paulburton0+packrat@gmail.com>.
