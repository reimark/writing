<figure>
<a href="http://www.flickr.com/photos/posthistoria/414100964/"><img class="block" src="https://konklone.com/assets/images/blog/internet-homeownership.png" /></a>
<figcaption>
<a href="http://www.flickr.com/photos/posthistoria/414100964/">joaquín (jko) contreras, CC-BY-NC</a>
</figcaption>
</figure>

Every so often, the Knight Foundation holds a [News Challenge](https://www.newschallenge.org), where they put a few million dollars up for grabs, and invite people to openly submit grant proposals for various sizes and shapes. Last summer, Knight's focus was on "open government", and I knew several of [the 8 winners](http://www.knightfoundation.org/press-room/press-release/open-government-projects-receive-more-32-million-w/). In fact, one of them, GitMachines, credits [2013's Open Data Day DC](https://konklone.com/post/open-data-day-dc-2013) with its start. 

This year's was, maybe unsurprisingly, about [a stronger Internet](https://www.newschallenge.org/challenge/2014), and it attracted over 650 entries. Among them are some excellent projects:

* **[TextSecure](https://www.newschallenge.org/challenge/2014/submissions/textsecure-simple-private-communication-for-everyone)** - My favorite privacy project at the moment, an [open source](https://github.com/whispersystems/textsecure) top-class [Android app](https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms) by [Moxie Marlinspike](https://twitter.com/moxie) for secure text messaging. So good that it recently became CyanogenMod's [default SMS app](https://whispersystems.org/blog/cyanogen-integration/).
* **[Mail-in-a-box](https://www.newschallenge.org/challenge/2014/submissions/mail-in-a-box)** - My friend [Josh Tauberer](https://twitter.com/JoshData)'s [open source](https://github.com/JoshData/mailinabox) personal mail server, that he's been using for umpteen years. The proposal asks for funding to make it easier for people less Josh than Josh to install for themselves.
* **[SLAPP Boomerang](https://www.newschallenge.org/challenge/2014/submissions/slappboomerang-a-simple-weapon-to-slay-the-enemies-of-free-expression-on-the-internet)** - A refreshingly non-technical proposal for making frivolous oppressive lawsuits easier to slap back against without going bankrupt, by my friends [Alan deLevie](https://twitter.com/adelevie) and [David Zvenyach](https://twitter.com/vdavez).

And a proposal by me!

* **[Superuser, Internet homeownership for everyone](https://www.newschallenge.org/challenge/2014/submissions/superuser-control-for-everyone)** - A central control panel for deploying other people's open source code to computers you own (or otherwise control), for people without much technical experience. I gave it the hastily chosen name of Superuser, since that's what it aims to turn everyone into.

I included in my proposal an anecdote from last August, that first inspired the idea:

> I operate a Twitter account called [@FISACourt](https://twitter.com/FISACourt), whose core is a very small program that checks the public docket of the Foreign Intelligence Surveillance Court every few minutes and announces when changes occur. It also immediately emails and texts me, so that I can quickly review the changes and provide a human editorial voice. Though simple and cheap, the near-real-time aspect of the tracking makes free central services like [IFTTT](https://ifttt.com) or [ChangeDetection](https://www.changedetection.com/) not an option - it has to be hosted oneself. 
> 
> A journalist from one of the world's biggest news outlets contacted me and asked me to configure my program to notify them as well, but they weren't able to meet my requirement for attribution. I encouraged the journalist to take my [very simple, open-source program](https://github.com/konklone/fisacourt) and have their newsroom IT department set it up somewhere, but wasn't able to communicate this in a way the journalist understood. 
> 
> I left that interaction convinced that everyone should be able to make use of the same power to automate and control the world around them that technically experienced users have.

After that happened in August, I sent some long-winded emails to friends to bounce self-hosting ideas off of them, and spent some plane rides drawing up design documents for such a system. But, I ended up daunted by how much code I'd have to write to get even a simple working prototype working, and never broke ground.

I don't know what my chances are like, here -- I have no working code, I'm just an individual with no team, and the idea will seem quite abstract to reviewers without a technical background. But I'm quite glad I took the time to write it up, as it was difficult and forced me to articulate the concepts in the most accessible way I could muster. In particular, I like "Internet homeownership" as an analogy for what I'm passionate about.

Two days after I submitted my proposal, [Sandstorm.io](http://sandstorm.io/) announced their public (invite-only) alpha, after a few months of development. It's very similar to my proposal, except that its author had the temerity to actually write code! So while it was a little jarring at first glance, it's actually very encouraging to see someone else believe in the same idea, and enough to build it. I still want to build Superuser, and I can imagine a number of things I'd do differently than Sandstorm, but I'll dig into Sandstorm and see if I can be of help.

In the meantime, I encourage you to leave "applause" and comments on each of the [other](https://www.newschallenge.org/challenge/2014/submissions/textsecure-simple-private-communication-for-everyone) [great](https://www.newschallenge.org/challenge/2014/submissions/mail-in-a-box) [proposals](https://www.newschallenge.org/challenge/2014/submissions/slappboomerang-a-simple-weapon-to-slay-the-enemies-of-free-expression-on-the-internet) I listed above (and [mine](https://www.newschallenge.org/challenge/2014/submissions/superuser-control-for-everyone), if you so feel moved).