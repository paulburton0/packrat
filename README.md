packrat
=======

Archives images from your Reddit.com saved links, del.icio.us bookmarks, and tumblr favorites.

## Features

* Archive your favorite images from the web
* Add multiple reddit, delicious, and tumblr accounts
* Download albums from imgur.com

## Installation and Setup

### Prerequisites

Packrat is a perl script, so you must have perl installed on your system. Packrat has been tested with Perl 5 in cygwin, windows (ActiveState), and linux (Ubuntu and Slackware) environments.

Once you have perl installed, there are a few perl modules that you'll need prior to running packrat:

* [JSON::XS](http://search.cpan.org/~mlehmann/JSON-XS-3.01/XS.pm)
* [XML::Simple](http://search.cpan.org/~grantm/XML-Simple-2.20/lib/XML/Simple.pm)
* [LWP::UserAgent](http://search.cpan.org/~gaas/libwww-perl-6.05/lib/LWP/UserAgent.pm)
* [OAuth::Consumer](http://search.cpan.org/~mathias/OAuth-Consumer-0.03/lib/OAuth/Consumer.pm)
* [File::Slurp](http://search.cpan.org/~uri/File-Slurp-9999.19/lib/File/Slurp.pm)
* [File::Basename](http://search.cpan.org/~rjbs/perl-5.18.1/lib/File/Basename.pm)
* [DateTime](http://search.cpan.org/~drolsky/DateTime-1.03/lib/DateTime.pm)

File::Basename is included with the standard Perl 5 installation. The others are available from [CPAN](http://search.cpan.org).


### Installation

Once your environment is all set up, you're ready to run packrat. No installation is necessary. The first time you run packrat, you will be guided through the process of configuring it and granting access to your online accounts. All the necessary configuration files will be created where you tell packrat to create them.

## Usage

`packrat [-qrc: /path/to/config]`   
`packrat [-s]`

There are four command line options that you can use with packrat:

* q - Supresses the normal "Checking" and "Downloading" messages that normally print when packrat is running. Errors (such as local file access errors or download failures) are still printed.
* s - Packrat runs completely silently. No errors or status messages are displayed at all.
* r - Forces the first-run configuration assistant to run.
* c - Specifies the configuration file to use. This option takes an argument in the form of a path to a configuration file.

## Bugs

Many, I'm sure. If you run across something, or if you have a suggestion, please open a bug or enhacement request at the [github page](https://github.com/paulburton0/packrat/issues), or email me at <paulburton0+packrat@gmail.com>.

