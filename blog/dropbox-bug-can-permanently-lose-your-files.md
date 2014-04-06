127 of my files in <a href="https://www.dropbox.com/">Dropbox</a> are now <strong>gone forever</strong>, due to a bug where files were "updated" to be 0 bytes, and Dropbox lost its previous copy of the file.

2 other files (precious family photos) were also affected, but it happened recently enough to be recovered manually by Dropbox engineers. 23 other files were also turned to 0 byte dust, but Dropbox kept its version history of these and I could revert them to their original version. 

Check whether you've been affected (on Mac or Linux) by running this command in a Terminal, it'll spit out a list of 0-byte files to a text file on your desktop.

<code>
find /path/to/your/Dropbox -size 0 -type f > ~/Desktop/zero-byte-files.txt
</code>

<strong>Important</strong>: Make sure you sanity check the list. Some systems have hidden 0-byte files, such as Macs' <a href="http://superuser.com/questions/298785/icon-file-on-os-x-desktop">"Icon\r"</a>, that are expected and normal.

If you find any that look unexpected, <a href="https://www.dropbox.com/support">let Dropbox know</a>, and reference this blog post to them so they can connect it with the issue I reported.

I've included my correspondence with Dropbox on the issue below. They've been very nice about it, and are looking into it, but this is a very serious bug. Because they don't know what the bug is, potentially anyone could be affected. I'll update this post if they find a fix.

<strong>Update:</strong> Some folks on <a href="http://news.ycombinator.com/item?id=4703943">Hacker News</a>, and Matt Holden of Dropbox <a href="#comment-508b0becc68a6d1b2300000a">in the comments</a>, have raised the possibility of filesystem corruption, particularly because of a <a href="http://www.phoronix.com/scan.php?page=news_item&px=MTIxNDQ">recently reported ext4 bug</a>. I do use ext4, so this can plausibly explain why my files were 0-byte'd in the first place, and why <a href="https://twitter.com/dangillmor/status/261921738441515009">others</a> have <a href="http://news.ycombinator.com/item?id=4704236">reported</a> finding 0-byte'd files.  

I also do not use Packrat, a premium Dropbox feature that stores version history for longer than 30 days, so this could plausibly explain why my 127 files that had been 0-byte'd months ago no longer have a version history of before then. I wasn't aware of the 30-day window.

However, these do not plausibly explain why the 2 manually recovered files that had recently been 0-byte'd, well within the 30-day window, showed no pre-0-byte version history, and required the assistance of Dropbox engineers.

It could be that the bug here has nothing to do with their desktop client - it could be a version history bug in the web frontend that affects some recently edited files. If that's the case, then that still needs to be fixed, so that people in my position can recover files their disk corrupted before they pass out of the 30-day window. It's only by finding and fixing that website bug that Dropbox can say with confidence that there's no desktop client bug.

<strong>Update 2:</strong> A report by someone who is on OS X, uses Packrat, but has lost <a href="https://twitter.com/frr149/status/261957708746469378">70 files</a> they <a href="https://twitter.com/frr149/status/262091947903168513">can't recover</a>.

<strong>Original correspondence</strong>

<blockquote>
<pre>
<strong>Eric Mill, Oct 20 05:50 pm (PDT):</strong>

Hi,

I recently wiped my hard drive and reinstalled my OS (clean upgrade from Ubuntu 12.04 to 12.10). I had been running Dropbox on the old OS. When I installed Dropbox on the new OS, almost everything went very smoothly. However, for some unknown reason, 25 files were "edited" to become 0-byte files.

This took place over 3 "events", at 3:49 PM, 5:31 PM, and 5:45 PM that afternoon:
https://www.dropbox.com/events/[redacted]
https://www.dropbox.com/events/[redacted]
https://www.dropbox.com/events/[redacted]

As far as I know, nothing I did caused these to happen. I didn't interact with these files, and in fact, I took care not to make any destructive actions in my Dropbox folder during the long syncing process. I believe these are bugs in Dropbox's syncing logic, but I have no idea how to reproduce it, or what common thread ties these files and events together.

I am able to restore each file from Dropbox's version history, though the user experience for this process is pretty annoying - I have to navigate through the file system for each one. There's no way to jump from an "event" screen that lists the affected files to a file's version history screen.

In general, I'm pretty happy with Dropbox, but this was a pretty alarming bug. I hope there's something you can do to look into why it happened.

Thanks,
Eric


<strong>Ridwan - Dropbox Support, Oct 22 05:11 pm (PDT):</strong>

Hi Eric,

Terribly sorry about the delayed response on this support request. In reviewing your account you appear to have restored most of these files via the web interface (I restored one extra).

Is there anything further I can assist you with?

I'm not aware of any bugs in the client syncing process at this moment, but I'll pass your case along to our engineering team. Hope this helps! Please let me know if I can be of any other assistance.

Best,
Ridwan


<strong>Eric Mill, Oct 23 07:37 am (PDT):</strong>

Yeah, there is one other piece of assistance I need - in restoring the files one by one, I noticed there were two that seem to have lost their history entirely:

https://www.dropbox.com/revisions/[redacted]
https://www.dropbox.com/revisions/[redacted]

These two files were the first two marked as "Edited" in the third Dropbox event along with a bunch of other files, the rest of whom have an earlier version I could restore. These two do not, yet they definitely had an earlier version that was not 0 bytes. Dropbox describes the event as "Edited", which clearly implies there was an earlier version.

Again, I have no idea why these 25 files, among my entire Dropbox, were affected, or why these 2 were affected differently from the other 23. These 2 files are now lost to me.

I would ask that you take this as a serious bug report. Even if your engineering team were to write off my original report of 25 files being 0-byte'd as my own human error (which it wasn't), the state of these two files indicate an undeniable bug in Dropbox's software (which in turn strongly suggests that all 25 were affected by a Dropbox bug).

If you can restore my files somehow, that would be greatly appreciated. Thankfully, these are just a couple of random photos - but I have other, more irreplaceable files contained in Dropbox, and if I were to lose them I would be very upset.

-- Eric


<strong>David M. - Dropbox Support, Oct 23 05:30 pm (PDT):</strong>

Hi Eric,

I've reported this to our engineers and they are taking a further look into the issue. To help troubleshoot the issue can you run the following in Terminal:

find /home/eric/.dropbox_actual/Dropbox -size 0 > ~/Desktop/zerodump

This should generate a text file on your Desktop. Can you attach that file to your reply so we can see if there are any additional files that are 0 bytes in your Dropbox folder. Please also note there may be some false positives as some applications will create 0 byte log/temp files.

Additionally, can you let us know of any system events that may have occurred during the time frames for those changesets?

Thanks!

Best,
David


<strong>Eric Mill, Oct 24 07:07 am (PDT):</strong>

Hi David,

Thank you for the prompt response. That's a good suggestion, I ran the command and have attached the file. I should have thought of that myself.

There are more files than I expected listed as 0 bytes. The one that's marked as deleted and is in the dropbox cache folder is one that I deleted myself on the same day as the events in question, before I realized what was going on. Many of the rest are apparently from earlier in the year - for example, one is this, from May 20th:
https://www.dropbox.com/revisions/[redacted]

May 20th is somewhat near when I last upgraded Ubuntu, but I'm pretty sure I did that much earlier in May, soon after Ubuntu's release. This one also lacks a previous version to restore, which is alarming.

I don't know what specific system events would have transpired during the events in question, either in May or October. In October, the 3 events I originally referenced occurred throughout the late afternoon, during the hours after installation of Dropbox in which it was syncing ~11GB of data down to my laptop. During this time, I was re/installing other drivers and software, occasionally rebooting, and configuring things like my /etc/fstab and my /etc/X11/xorg.conf files.

The only thing I can think of that might have been related is that, somewhere in the middle of that, I added the user_xattr flag to the partition on which my Dropbox lives, and rebooted (which caused a remount). My understanding is that the user_xattr flag is a pretty harmless option, that allows applications that care about such things to add arbitrary filesystem attributes.

Unfortunately, I don't have system logs from that time - because I have an SSD, I mount my logs directory into RAM (to minimize disk writes) and it gets wiped on every reboot. Still, if you have any other questions I'm happy to try to answer them.

-- Eric


<strong>David M. - Dropbox Support, Oct 25 02:48 pm (PDT):</strong>

Hi Eric,

I was able to have our web team recover the two files:

https://www.dropbox.com/revisions/[redacted]
https://www.dropbox.com/revisions/[redacted]

Unfortunately, it looks like the files that were previously 0 byted can no longer be recovered as their previous versions were removed from our servers as the events occurred in June. I sincerely apologize for this file loss.

Thank you for the additional information you were able to provide about the events, I'll be continuing to follow up with our engineering team to try and find the root cause of this issue. I'll let you know as soon as we have any news.

If you have any additional questions or concerns please let me know.

Best,
David
</pre>
</blockquote>