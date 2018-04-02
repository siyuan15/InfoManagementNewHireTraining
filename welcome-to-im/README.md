# Welcome to IM! 
## DIRECTIONS
:see_no_evil: :hear_no_evil: :speak_no_evil:

I hope you like acronyms, because we use a lot of them :imp:

## Series 1 - Basics
Before we dive into any services let's do a quickly run over some basic 
computer stuff you'll need to know. If you miss some of it, don't worry 
you'll be able to refer back here later. Also, the whole of the internet is 
at your disposal. 

### Git :octocat: & Docs :blue_book:
Welcome to your first challange. This should be easy :smiley:
1. Take a look at the resources on
[extra-credit.md](extra-credit.md). 
1. Go find one of your own. It can be anyting cool (Good 
documentation [Coursera](https://www.coursera.org/), 
[Stack Overflow](https://stackoverflow.com), [Github](https://github.com/)).
1. Fork this repository, add your resource, and then make a 
pull request. 
    * If you need help ask anybody:raising_hand:, and if you finish quickly 
    get to know your neighbor (and maybe help them:exclamation:)

If you see more opportunities to contribute to these docs please 
feel free. Small improvements build over time and are excelent practice :+1:

### Ravello & VMs :computer:
Hopefully you've got your 
[ravello account](https://cloud.ravellosystems.com/) set up. 
If not, we'll just use a local VM. 

#### Directions
1. Find an [Oracle Linux](https://www.oracle.com/linux/index.html) image
1. Set up and log into your VM!


### OS Basics :shipit:
You're going to get to know linux :sparkles:
![](../common/what-are-clouds-made-of.jpg) [1]  
Some things we expect you to know: 
* How to navigate the filesystem :file_folder: (`cd`, `pwd`, `ls`)
* Users, Groups, and Permissions
* Software & Package Managers (`yum` for Oracle Linux)
* Environmental Variables (especielly the `$PATH`)

#### Directions
1. Open a terminal in your VM
1. Become `root` - `sudo su`
1. Navigate to your home directory - `cd ~`
1. 


### Linux & Bash
You'll often need to find your way around an unframiliar VM 
so understanding how to get the most out of the linux shell will 
really give you a head start! 
* Useful odds n ends 
    * `|` - pipe
    * `curl` / `wget` - download files from the interwebs :globe_with_meridians:
* Find files :page_with_curl:
    * `grep` - search for lines 
    * `mlocate` - index and search the filesystem
    * `find` - find files 
* Work with files - `vi` :pencil2:
    * `i` - insert mode
    * `:w<Return>` - write
    * `:q<Return>` - quit 
    * `/string` - search 

Bash will be your friend and so will python. 

#### Directions
Each of these steps should be done with one line of code :wink:
1. Download this file from the command line 
1. Get the number of lines
1. Find a folder named `advanced_analytics`
1. Use vim to add an alias to your `~/.bashrc`


### Networking - SSH, Public/Private key encryption, VNC
Hopefully you'll all already be framiliar with these techniques, 
and got to use VNC (maybe without knowing it) to log onto your Ravello
instance. 
![](../common/public-private-key-encryption.jpg) [2]  
* SSH clients (for Windows - on 'nix it's build in)
    * the standard is [putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/)
    * I prefer [mobaxterm](https://mobaxterm.mobatek.net/)
    * you can also use [cygwin](https://www.cygwin.com/) for ssh
    * or a terminal emulator like [cmder](http://cmder.net/) that comes with cygwin
* Port-Forwarding
* Proxies 
* VNC
* SFTP/SCP
#### Directions
1. Download an SSH client of your choice
1. SSH into your VM from above with said client
1. If you did this on clear-guest do this on VPN
1. Use SFTP or SCP to transfer over an `index.html` file
1. Host said file with `python -m SimpleHTTPServer`
1. Use port-forwarding to open up the webpage on `localhost`

### Tools :wrench:
IDE, text editors, DVD
#### Directions 
1. Everyone tell us your favorite IDE, text editor, and other devtools
1. Install a good text-editor (if you haven't already)
    * I recommend [vscode](https://code.visualstudio.com/) (I use it for almost everything)
1. Download [Data Visualization Desktop](http://www.oracle.com/technetwork/middleware/oracle-data-visualization/downloads/oracle-data-visualization-desktop-2938957.html)
:bar_chart: It's great for data-exploration and we'll be using this and it's cousin 
[Oracle Analytics Cloud](https://cloud.oracle.com/en_US/oac) frequently
1. Download [Oracle SQL Developer](http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html). 
If you're on IM or Analytics you'll be using SQLDeveloper often

### Data Management tools on Oracle Cloud
Have you used any of these? Let us know! (Remember 
you can check [cloud.oracle.com](https://cloud.oracle.com/home) 
to see the latest portfolio)
#### Directions
1. Pick a service
1. Tell us when & why to use it
1. Give a few of the selling points for this service


## Series 2 - Oracle Cloud Infrastructure (OCI) Storage - Object Store 
[Oracle's object storage](https://docs.us-phoenix-1.oraclecloud.com/Content/Object/Concepts/objectstorageoverview.htm)  
Object storage is pretty simple - think of it like a filesystem in the cloud. 
our object storage infrasctucture is build off of 
[OpenStack Swift](https://docs.openstack.org/swift/latest/)* (an
opensource, distributed object/blob store) and we even have our own 
[supported version](https://www.oracle.com/linux/openstack/index.html)

*this might only be true in OCI-Classic :grey_question:
#### Directions
TODO:(CY)

## Series 3 - DBCS
[Oracle Database](https://en.wikipedia.org/wiki/Oracle_Database) 
is unarguably one of the top databases in the world. It also happens to be 
Oracle's "bread and butter" so expect to get a lot of requests from customers 
to size or demo this. 
#### Directions
1. 

## Series 4 - ExaData 
More Oracle Database!

#### Directions
1. TODO:(danny)

## Series 5 - ADWCS
Once more over Oracle Database. 

#### Directions
1. 

## Series 6 - Advanced Analytics - ORAAH, ORE, ODM, Spatial & Graph

#### Directions
1. 


## Series 7 - Data Integration - Golden Gate, DIPC, EHCS
What is data integration? 

#### Directions
1. 


## Series 8 - BDC - Hadoop, Spark, Hive, Zeppelin
:dancer: Oracles Big Data Cloud :raised_hands:

#### Directions
1. 


## Series 9 - Data Science - data retrieval, exploration, cleaning, and model buildling 
#### Directions
1. 


## Final - Putting it all together - *challange* :grin:

#### Directions
1. 


# References 
[1] https://twitter.com/Linux/status/936877536780283905 

[2] https://en.wikipedia.org/wiki/Public-key_cryptography 