Finder won't relaunch after being manually killed, aka "The Finder Hydra"
=================================================

Issue
-----

I noticed this one when trying to `open .` from the terminal and nothing happened. For some reason, Finder had forked itself... no worries, I thought, I could just `pkill -KILL finder`, right? Wrong... The OS realised Finder had died and launched a new copy which forked itself again. I had three copies of Finder running, and killing each one just spawned more.

I rebooted, and then something weird happened; Finder wouldn't launch at all. `open .` still wasn't working, and neither was `open -a Finder` or `open
/System/Library/CoreServices/Finder.app`.

Solution
--------

`rm ~/Library/Preferences/com.apple.finder.plist`

This resets Finder's preferences to the default, and seems to solve any Finder launch issues.

_Note: This **will not** reset the Finder sidebar, since this is stored in_ `~/Library/Preferences/com.apple.sidebarlists.plist` _and not the Finder settings._
