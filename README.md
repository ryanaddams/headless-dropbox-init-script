# headless-dropbox-init-script
Headless dropbox bash init script, adapted from [https://gist.github.com/benhedrington/](this gist) which I discovered through [http://rkulla.blogspot.com](Ryan Kulla's) [http://rkulla.blogspot.com/2014/03/headless-dropbox.html](handy guide) on setting everything up.

The Dropbox script (as it was in the gist at the time) needed to be updated to account for recentish changes to the Dropbox Linux version; namely, the renaming of the dropbox daemon to "drobpoxd" and, apparently, it becoming a symlink to the actual versioned daemon binary.

I made a few minor modifications to have it use the Dropbox pidfile to kill the daemon (to account for the binary having a different name in the process list than the initial daemon command), as well as adding "nice" and "iosched" settings to the start-stop-daemon call so that Dropbox doesn't eat up all of the CPU and disk io on my Ubuntu server (which it was, initially, as it was syncing a ton of files then, but I'd like to avoid this likely happening again in the future when I add new files).
