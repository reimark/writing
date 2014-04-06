I don't pretend to understand why [isitchristmas.com](https://isitchristmas.com) gets such an indefensible amount of traffic. But for as long as I have this gift, I will continue to exploit and misuse it. 

<a href="https://konklone.com/assets/images/blog/iic-2013/sine-2.png">
<img src="https://konklone.com/assets/images/blog/iic-2013/sine-2.png" class="border block" width="650" />
</a>

For 2013, I took the [real-time flag thing I built for 2012](https://konklone.com/post/isitchristmas-dot-com-2012), and focused on making it more interactive, fun, and reliable.

When you show up, it will change your mouse cursor into the flag of the country you're visiting from, and start showing you other people's cursor-flags moving and clicking around in real time. For those who know (or can figure out) how to open their browser's developer console, there's a hidden chat room.

## Little Touches

The thing I loved the most about 2012 were the [formations](https://www.flickr.com/photos/konklone/8326547005/in/set-72157632388653620) people would [often](https://www.flickr.com/photos/konklone/8327607092/in/set-72157632388653620) [make](https://www.flickr.com/photos/konklone/8326547743/in/set-72157632388653620), so the only visible flag features I added were meant to make more formations possible. I made right-clicking leave a translucent "ghost" that would disappear after a few seconds -- and scrolling would rotate your flag (and any clicks and ghosts). 

While there were certainly formations this year, the ghosts and rotation also allowed people to [automate more creative things](https://twitter.com/konklone/status/416399871231275008) too.

<a href="https://twitter.com/konklone/status/416399871231275008">
<img src="https://konklone.com/assets/images/blog/iic-2013/hearttttt.png" class="border block" width="650" />
</a>

The chat room worked functionally enough in 2012, but I was able to figure out some ways to add color and interactivity — detailed in a [separate post](https://konklone.com/post/how-to-hack-the-developer-console-to-be-needlessly-interactive) — to seriously liven it up this year. The result was **much** better than 2012; the room had notably less spam and ugliness, people stuck around longer, and there were actually memorable conversations.

<img src="https://konklone.com/assets/images/blog/iic-2013/chat4.png" class="border block" />

## Open Data

I opened up an [isitchristmas/data](https://github.com/isitchristmas/data#isitchristmas-data) repository on GitHub, where you can see traffic reports from past years, and some stats on browsers and countries from 2012. This is also where you can find the [2012 chat logs](https://github.com/isitchristmas/data/blob/gh-pages/2012/chat.csv).

2013's chat logs will get published there eventually too, after I put in some effort to clean it up and make a presentation that captures the visual additions.

I'll also be publishing a new piece of data: "snapshots" of flags and their positions. Every 5 seconds, each streaming server "pings" every connected user for their flag's country, X/Y coords, and rotation angle, then saves them all to a central Redis database set up solely for this purpose. I was hoping to use this to make a near-live birds' eye view of all activity on the site, but ran out of time to do more than just collect it.

But still, even just 4 days of snapshots turned out to be a lot of data: my Redis dump is **3.3GB**. Because of this, I had to host this myself, on EC2, rather than a Redis cloud provider. (It wasn't that hard!) I need to examine and clean up this data, which will mean making a little "viewer" for it, that I'll also publish. It won't be perfect — it clearly dropped some snapshots during heavy load — but I think it will be very cool to see when it's ready.

<a href="https://konklone.com/assets/images/blog/iic-2013/flags.png">
<img src="https://konklone.com/assets/images/blog/iic-2013/flags.png" class="border block" width="650" />
</a>

## Making It Work

The basic architecture of the site is still the same:

* The main isitchristmas.com website is served by a Node application called [**web**](https://github.com/isitchristmas/web). It looks up your country from your IP and renders a page.
* That page then connects, via WebSockets, to a separate Node application called [**sockets**](https://github.com/isitchristmas/sockets), that manages the real-time passing around of flag events. Every server running this app is a "room".
* Behind the scenes, every room server connects to a single Redis instance called "manager", which shows me who's connected and how, and lets me send commands through every room and down to every connected user. I also transmit chat messages via the manager, which lets chat travel across every room.

<a href="https://konklone.com/assets/images/blog/iic-2013/chat5.png">
<img src="https://konklone.com/assets/images/blog/iic-2013/chat5.png" class="border block" />
</a>

This year, the app ended up being spread across **5** different hosts: [Amazon EC2](http://aws.amazon.com/) for the main nginx/Node website, [Redis Labs](http://redislabs.com/) for the Redis manager, and a combination of [Nodejitsu](https://www.nodejitsu.com/), [Heroku](https://dashboard.heroku.com/apps), and [dotCloud](https://www.dotcloud.com/) for the flag streaming servers (more on that below).

After suffering some embarrassing crashes last year at midnight EST and CST, I made some significant architectural changes.

* In 2012, I [used MaxMind](https://konklone.com/post/isitchristmas-dot-com-2012#getting-users-countries-with-money) for geolocation, by loading their excellent [IP->country database](http://www.maxmind.com/en/country) into a MongoDB instance on MongoLab, and every visit meant a MongoDB lookup. For 2013, I cut out MongoDB entirely by using kuno's excellent Node [geoip](https://github.com/kuno/GeoIP) library to do the country lookup purely in-memory.
* In 2012, I hosted both apps (the main web app, and the flag servers) on Nodejitsu. For 2013, I ran the main web app at isitchristmas.com on a large Amazon EC2 instance, proxied through nginx to 2 Node processes managed by [forever](https://github.com/nodejitsu/forever) (itself a Nodejitsu open source project).
* In 2012, when I crashed, my backup was my old PHP/MySQL app on [Webfaction](https://www.webfaction.com). For 2013, I prepared a static file for my EC2 instance to serve via nginx, just in case.

This year, everything held up just fine. According to Google Analytics, I peaked at around 4,500 simultaneous users. I did get some intermittent 500's that resulted from an occasional "too many open files" error, so I [raised the open files limit](http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/) and all was well.

<img src="https://konklone.com/assets/images/blog/iic-2013/analytics.png" class="border block" />

## Moving Beyond Nodejitsu

[In 2012](https://konklone.com/post/isitchristmas-dot-com-2012#hosting-nodejs-and-websockets-is-fun-but-not-without-emotions), I used only [Nodejitsu](https://www.nodejitsu.com/) for my WebSockets servers, and I really pushed their limits. At my peak, I had 60 parallel servers, and I needed one of their main support people to hand-hold the deploy process to get me there, which was draining for both sides. But overall, I left satisfied with my experience there.

They've since [revamped their deploy process](https://blog.nodejitsu.com/infrastructure-at-nodejitsu-1), but I still had lots of failed deploys, restarts, and scaling commands this year, even with as few as 8 servers. I also suffered a plague of "zombie" servers, where old servers would stubbornly refuse to die, making it extremely difficult for me to condense servers or manage room sizes effectively.

Making matters worse, Nodejitsu has also clearly [reconfigured its public cloud business](http://blog.nodejitsu.com/changes-in-nodejitsu-public-cloud) over the last year to become more sustainable, and it's come at a price. Now, Nodejitsu's [pricing model](https://www.nodejitsu.com/pricing/) requires an upfront payment of $240 (the price of 10 servers running all month) for you to go above 10 servers for even a day. For a brief, un-budgeted line item like isitchristmas, this is steep.

I wrote Nodejitsu asking for an exception to this policy, but was denied on the basis that people who use more than 10 servers usually end up costing them on support. After thinking about it for a few weeks, I swallowed hard and decided to shell out the $240 anyway, figuring that their new business plans, deploy process, and (seeming) recommitment to their public cloud meant it'd be the most stable option out there. That did not turn out to be the case, and I when I asked about said support, I was told not to expect much over the holidays.

So for 2013, I reduced my dependency by splitting my app across Nodejitsu, [Heroku](https://dashboard.heroku.com/apps), and [dotCloud](https://www.dotcloud.com/). Heroku didn't support WebSockets in 2012, but they [added beta support for it](https://blog.heroku.com/archives/2013/10/8/websockets-public-beta) this year that worked just fine for me. dotCloud has long supported WebSockets, and it was very easy to set up and go. Pricing for [Heroku](https://www.heroku.com/pricing) and [dotCloud](https://www.dotcloud.com/pricing.html) are both entirely pay-as-you-go, making them much cheaper for a spiky project like mine than Nodejitsu's model. And splitting the app across hosts is actually pretty manageable, when you [make your own dashboard](https://konklone.com/assets/images/blog/iic-2013/dashboard.png).

I took a glance at [AppFog](https://www.appfog.com/), but they don't support WebSockets and [can't muster](http://feedback.appfog.com/forums/171983-appfog/suggestions/3543100-add-websocket-support-to-node-js) any public statement about their plans to, despite [once announcing](http://blog.appfog.com/appfog-acquires-nodester-shares-love-for-node-devs/) they would over a year ago. I took a long look at Red Hat's [OpenShift](https://www.openshift.com/), which I really want to use for something, but their [WebSockets support](https://www.openshift.com/blogs/paas-websockets) is still experimental, requires you to custom-build an image, and hasn't seen any improvements in a year.

All three companies' servers functioned adequately, and anecdotally it felt like Nodejitsu's could handle a bit more load. But fundamentally, I expect my deploys to work, and to get what I pay for. While their servers are nice, and they really do deserve a lot of credit for open sourcing [so much](https://github.com/nodejitsu/forever) [valuable](https://github.com/nodejitsu/node-http-proxy) [software](https://github.com/flatiron/winston), Nodejitsu's pricing and policies have become far less competitive. If I were doing it again, I'd either omit Nodejitsu or make it a much smaller part of my cloud.

The larger lesson for me was to not depend on any one company — moving more resources to another host was much easier than writing and updating drawn-out support tickets. If I do this next year, I'll be evaluating self-hosting my own elastic cloud.


## Things and observations

<a href="https://konklone.com/assets/images/blog/iic-2013/strange.png">
<img src="https://konklone.com/assets/images/blog/iic-2013/strange.png" class="border block" />
</a>

[Brandon Jones](https://twitter.com/btj) went nuts on this year's update to the [Is It Christmas? app for iOS](https://itunes.apple.com/us/app/is-it-christmas/id344978638?ls=1&mt=8), taking advantage of iOS 7's built-in physics engine to do some ridiculous word interactions.

I made isitchristmas an HTTPS-only website, because it's [a good, free habit](https://konklone.com/post/switch-to-https-now-for-free) to be in. Then I went overboard and bought a "Class 2" certificate, just for the experience of being physically mailed a verification code to type into a web form. Like last year, all WebSockets interaction was already encrypted.

And speaking of, **WebSockets is so here that it's crazy**: In 2012, about 80% of my visitors managed to connect via native WebSockets -- in 2013, **97%** did. I don't even need to support fallback options anymore. I'll have formal 2013 stats in [my data repo](https://github.com/isitchristmas/data#isitchristmas-data).

[SockJS](https://github.com/sockjs/sockjs-client#sockjs-client) once again held up like a champ, and I strongly recommend it for anyone needing to send packets around the web via an open socket.

Finally, I actually built (and then barely used) a whole [tapping system](https://github.com/isitchristmas/sockets/blob/master/calea.js) that let me dodge my host's load balancer and join the room of my choice, if provided a secret room ID. It works by making a [Redis](http://redis.io/) pub/sub channel pretend to be a WebSockets connection, that funnels traffic out the backdoor. It was very neat, but I didn't get a chance to build the visual [HQ](http://www.businessinsider.com/pictures-of-the-nsas-utah-data-center-2013-6) that really would have taken advantage of it. Maybe next year!

## Hooray

All in all, isitchristmas.com was great fun this year, and I'm glad I committed the time and resources to make it better and do it again. [Traffic](http://isitchristmas.io/data/google-analytics/2013.pdf) turned out to be about the same as [last year](http://isitchristmas.io/data/google-analytics/2012.pdf), but the quality and energy of the visitors, the attention my [console hacks](https://konklone.com/post/how-to-hack-the-developer-console-to-be-needlessly-interactive) got, and the overall stability and technical experience I got make it feel like a bigger success to me. Hooray for Christmas!

<a href="https://konklone.com/assets/images/blog/iic-2013/yes.png">
<img src="https://konklone.com/assets/images/blog/iic-2013/yes.png" class="border block" width="650" />
</a>