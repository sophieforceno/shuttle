README.md

**SHuttle v0.9.7 (build 062016) - First public release!**

# Introduction:
SHuttle is a Pushbullet client written in Bash shell script. It allows the sending of push notifications from the Linux CLI and from within Bash scripts. SHuttle itself cannot receive pushes, in that regard, it is not a full client. I wrote SHuttle primarily as a means to receive real-time notifications for system administration purposes. You can find many of the scripts I wrote for sys admin use in the shuttle-utils repository: https://github.com/andyforceno/shuttle-utils

SHuttle has been tested on Ubuntu Linux 14.04 running Bash 4.3.11(1), and Debian 8 running Bash 4.3.30(1). SHuttle contains numerous Bash-isms making it unsuitable for other shells. SHuttle has few dependencies, most of which are included by default in most distros. Curl is likely the only program you will have to install.


# Installation:
    git clone https://github.com/andyforceno/shuttle/
    cd to shuttle/
    chmod +x shuttle
    ./shuttle

On first run, SHuttle will walk you through the setup. This requires a web browser for OAuth.
You can run setup at any time by executing `./shuttle setup`

Note: Since authentication with Pushbullet is via OAuth, pushes from SHuttle will appear under Following > Shuttle on the Pushbullet website/app.


# Usage:
```
Commands take the following form: 
shuttle <action> <type> <recipient> <data> where:

<actions>   		    <types>						
* push 		        	file, link, note, sms, weather			
* list		        	channels, chats, devices, pushes, user		
* chats			        add, delete, update
* devices		        delete, update
* help		        	Shorter usage text
* usage		    	    List full usage text 		
* setup 	    	    Oauth and setup
* Except for "usage" and "setup", all <actions> require additional parameters. 


Command-line arguments:
<action>:
chats | -c		        Add, delete, or update chats
devices | -d            Add, delete, or update devices
help | usage	        Show the long usage text
list | -l 		        List channels, chats, devices, pushes, or user info
push | -p		        Send push to <device> or <chats>
setup 		    	    Setup OAuth for SHuttle 

<type>:
For "push" <action>
file | -f		        Push a file to <device> or <chats>
link | -l		        Push a link to <device> or <chats>
note | -n		        Push a note to <device> or <chats>
sms  | -s	            Send an SMS to <phone number>
weather | -w	        Send weather forecast to <device> or <chats>

For "chats" or "devices" <action>:
add | -a		        Add <chat> email address or <device> name
delete | del	        Delete <chat> email address or <device> name
update | -u		        Update <chat> email address or <device> name

For "list" <action>:
channels		        List channel subscriptions
chats | -c		        List available chats recipients
devices | dev | -d      List available devices 	 
pushes			        List pushes from the last t intervals (h hours, d days - default is 24h)
user 		        	List user info


Notes & Examples (not exhaustive):
To push notes or files:   <action> <type> <recipient> <title> <body> (<file name>)
To push links: 	          <action> <type> <recipient> <title> <URL>
       Note: If no URL title is given, SHuttle will parse the website for a title
To push clips: 		  <action> <type> <device> <clip> 
To send SMS: 		  <action> <type> <phone number> <SMS>

SHuttle can do partial matches of device names and chat addresses:
To push a note to your friend "Jane Doe":
shuttle -p -n jane "Hi Jane!" "How are you today?"

Push a weather forecast to your mobile phone:
shuttle -p -w "galaxy s4"

Push a note to the Chrome web browser:
shuttle -p -n chrome "This is a note title" "This is a note body"

Push a URL to your friend at "a_friend@somewhere.com":
shuttle -p -l a_friend "https://www.github.com"
Note: If you omit title as in above example, SHuttle will parse the website for a title and push it along with the URL

Push an SMS:
shuttle -p -s "+1 9995551234" "Remember to buy milk"
Note: Your phone must be connected to the internet and set as "sms_device" in .shuttlerc

List your devices:
shuttle -l -d

Rename a device:
shuttle -d -u "Phone" "Mi5"

List chats (contacts):
shuttle -l -c

Add a chat (contact):
shuttle -c -a a_friend@somewhere.com 

Update a chat (contact) address:
shuttle -c -u a_friend@somewhere.com my_friend@gmail.com

Delete a chat recipient:
Delete accepts partial matches of e-mail, if they are unique:
shuttle chats del "moogie@"

List pushes (from last 7 days):
shuttle -l -p 7d
Accepts hours or days (default is 24h)
```


# License:

This program is distributed under the MIT license:

The MIT License (MIT)

Copyright (c) 2016 Andy Forceno <andy@aurorabox.tech>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
