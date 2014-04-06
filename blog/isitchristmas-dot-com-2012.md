<a href="http://isitchristmas.com">isitchristmas.com</a> continues to get an irrational amount of traffic, [right 2013-03-04 In all of 2012: 3M visits, 2.3M uniques.] so I put an irrational amount of work into it this year.

If you <a href="http://isitchristmas.com">visit</a> in Chrome, Firefox, IE10, or Safari and wait a second or few for it to connect, you should see a bunch of <a href="http://superturtle513.tumblr.com/post/38296087305/isitchristmas-com-added-a-feature-where-everyone-on-the">crazy flags</a> appear and start moving around and making ripples. Each flag is another person, from that flag's country, moving their mouse around, and the ripples are clicks. Your own cursor should be your own flag, and you can participate too.

Participate in what? I have no idea. But people seem to be <a href="http://woodsgotwood.tumblr.com/post/38439453526">figuring out</a> some <a href="http://superturtle513.tumblr.com/post/38296646132/so-on-isitchristmas-com-i-found-my-friend-whos">awesome</a> <a href="http://cynchi-yuu.tumblr.com/image/38392610532">ways</a>.

<a href="http://www.flickr.com/photos/konklone/8326547743/in/set-72157632388653620/" target="_blank"><img src="/assets/iic/brazilians-thumb2.png" style="text-align: center; border: 1px solid #888;" /></a>

**Update:** I've created a [set of screenshots](http://www.flickr.com/photos/konklone/sets/72157632388653620/) on Flickr.

**How it works, short version**:

* User visits isitchristmas.com, a Node.js app (**web**) running on Nodejitsu.
* **web** determines the user's country by checking their IP against a MongoDB full of mappings of IP blocks to ISO country codes obtained from MaxMind.
* **web** renders the page, which contains a bunch of JavaScript...
* ...that connects to a *separate* Node.js app (**sockets**) via SockJS.
* **sockets** keeps track of all connected users, and broadcasts mouse activity and other messages as appropriate between users.
* There can be as many instances of **web** and **sockets** as there need to be to handle load. Each instance of **sockets** makes a virtual room that a visitor is randomly assigned to through Nodejitsu's load balancers.
* Each **sockets** server uses a central Redis instance to say what users are connected, store analytics, and send certain commands and messages.

Read on if you're interested in more technical details.

## WebSockets Have Arrived or at Least Are Arriving or Almost Arrived

<a href="http://www.html5rocks.com/en/tutorials/websockets/basics/">WebSockets</a> are super-low-latency held-open TCP connections that allow for lightning-fast data transfer. They stay open even as the Internet shifts under their feet. While completely magical, open TCP sockets are not new -- but for them to be available inside the browser in a standard way is extremely new. And while you can do a lot of things with rapid polling, even chat rooms, for mouse cursor movement you need actual open sockets.

Back in 2010, Jeff Kreeftmeijer did an <a href="https://vimeo.com/13805413">experimental blog post</a> that showed you other readers' cursors in real time. Since then, WebSockets support has grown to include the most current version of every major browser - even Internet Explorer 10.

I use <a href="http://sockjs.org/">SockJS</a> to handle WebSockets or to fall back to <a href="http://en.wikipedia.org/wiki/Comet_(programming)">"Comet"</a> (a held-open AJAX connection). I expected lots of people to resort to Comet, but was pretty amazed to find that **over 80%** of successful connections are through WebSockets. WebSockets support has moved very fast!

In fact, many people who connect to isitchristmas.com through Comet are actually visiting in browsers that support WebSockets! Many routers, switches, and firewalls have a hard time allowing WebSockets connections through.

I drastically improved WebSockets connection rates, believe it or not, by <a href="https://gist.github.com/4247942">using SSL</a>. [right Check <a href="https://groups.google.com/d/topic/sockjs/wAgVZoN5iC4/discussion">this discussion</a> for more, including some better research from theyak.] By <a href="https://github.com/sockjs/sockjs-client/issues/94#issuecomment-9901564">moving it off port 80</a>, and by signaling that your packets require security, some networks that would otherwise examine and drop your packets choose to leave you alone.

**SockJS vs socket.io**: I started out using <a href="http://socket.io/">socket.io</a>, but my servers were <a href="https://gist.github.com/4146668">crashing every 30 minutes</a> from exhausted memory. After switching to SockJS, they don't. I don't know for certain that socket.io was leaking memory (though there are <a href="https://github.com/LearnBoost/socket.io/issues/438#issuecomment-11745557">enough reports</a> that I suspect it was), because when I switched to SockJS, I also stopped brokering all mouse motion through Redis. That was hugely intensive and negated a lot of the benefit of adding more application servers. 

So it's ambiguous. What I can say for sure is: SockJS is lighter and affords you more control, it's easy to add niceties like broadcasting and named events yourself, and <a href="https://groups.google.com/forum/?fromgroups#!forum/sockjs">Marek's support</a> is far more responsive than <a href="https://github.com/LearnBoost/socket.io/issues">socket.io's</a>. socket.io is easier to start with if you've never done streaming before, but to really get things done, I recommend <a href="http://sockjs.org/">SockJS</a>.

## Getting Users' Countries With Money

From 2007-2011, I've used the free database at <a href="http://www.hostip.info/">hostip.info</a> to match IP addresses to locations, using their <a href="http://www.hostip.info/dl/index.html">SQL dump</a>. It's done a great job, but I chose to pay a bit of money this year for <a href="http://www.maxmind.com/en/home">MaxMind's</a> commercial dataset. They offer varying levels of granularity, including just what I'm looking for - <a href="http://www.maxmind.com/en/country">country codes</a> - for only $50, with updates for $12 apiece. There's also a <a href="http://dev.maxmind.com/geoip/geolite">free version</a> with the same schema; it's less accurate but actually seems pretty good.

MaxMind gives you a spreadsheet, so you can <a href="https://github.com/isitchristmas/web/blob/master/scripts/load.js">load it</a> into whatever you want. I leased a MongoDB instance from <a href="https://www.mongolab.com/">MongoLab</a> ($10/month) for this. Visits to isitchristmas.com check the visitor's IP address <a href="https://github.com/isitchristmas/web/blob/master/app.js">against each IP block</a> and get the page rendered. Unfortunately, doing this process server-side limits my options for caching. If it becomes a bottleneck, I'll have to add more application servers and potentially more MongoDB instances.

## Flag Hutch

I collected country names and flags by mixing <a href="http://www.maxmind.com/en/home">MaxMind</a>, <a href="http://flagpedia.net/">Flagpedia</a>, <a href="http://en.wikipedia.org/wiki/File:Flag_of_the_Isle_of_Man.svg">Wikipedia</a>, and <a href="http://geonames.de/">geonames.de</a>.

First, I took all the ISO country codes and names that appear in MaxMind's country spreadsheet. Flagpedia's flag image URLs are blessedly predictable by country code, so I "borrowed" all of their flags. Thanks, Flagpedia! 

This only covered sovereign states, so for the remaining ~50 territories that have their own flag, I researched each one on Wikipedia and downloaded them by hand as SVG. I resized them down to a 20px height and converted to PNG to match Flagpedia.

Because the click effects (and other things) in isitchristmas depend on the exact width and height of the flag image, I wrote a script that used imagemagick to extract the width and height of each flag and create a <a href="https://github.com/isitchristmas/web/blob/master/public/christmas.js#L193">canonical bit of JSON</a> with country codes, names, and flag sizes.

The localized country names, visible at the top-right when you mouse over someone else's flag, come from <a href="http://www.geonames.de/indcou.html">geonames.de's index of country names</a>.

Finally, I downloaded the <a href="http://en.wikipedia.org/wiki/File:Flag_of_Esperanto.svg">flag for Esperanto</a> and made it the default for people the site can't identify or has no flag for.

I believe I have flags for every country and non-sovereign territory that has one - please let me know if I've missed one. Grab them <a href="https://github.com/isitchristmas/web/tree/master/public/countries">from my public repository</a> if you want.

## Hosting Node.js and WebSockets is Fun But Not Without Emotions

Both the main app and the streaming app run on <a href="http://nodejs.org/">Node.js</a>, hosted on <a href="http://nodejitsu.com/">Nodejitsu</a>, a Node app host. I signed up because of how Node-dedicated they are - <a href="http://nodejitsu.com/company/team.html">their team</a> is made up almost entirely of extremely active Node.js community members. There are competitors to Nodejitsu out there, but they don't all support native WebSockets. Notably, Heroku <a href="https://devcenter.heroku.com/articles/using-socket-io-with-node-js-on-heroku">does not</a>. (*Update*: Heroku has since added [WebSockets support](https://devcenter.heroku.com/articles/heroku-labs-websockets).)

I can definitely recommend Nodejitsu for its ease of deployment and app management, and especially its quality of real-time support. I've visited their IRC channel at every hour of the day and have always gotten an answer to a question or problem right away. All the people who've helped me there are professional, smart, and nice. They've taken isitchristmas.com indefensibly seriously and gone out of their way to make sure things go smoothly for it - I really appreciate that.

The actual servers you get with Nodejitsu are less powerful than I would like for a project like this. Their site <a href="http://nodejitsu.com/paas/pricing.html">advertises business plans</a>, with dedicated servers and better controls over performance. Unfortunately, their December launch for these plans didn't happen on time, and so I'm using their shared VMs, which they recommend for "non-critical applications or experiments". I can't call isitchristmas.com critical, but I'd have liked the option to pretend it is.

The silver lining of being stuck on shared VMs is that the servers start choking before clients' browsers do. Servers only syndicate user activity to other users on that server, so this means I can handle "room" management and load balancing purely by adding more servers. Each server handles something like 50-60 users (including idle ones) before showing the strain, and this turns out to be an appropriate room limit. No load balancing application logic required!

Both Nodejitsu and I were surprised that the strain showed at 50-60 users. While my code could have some performance flaws, I think it's just that real-time mouse streaming is an unusually intense amount of work. I'm sure for most uses, a Nodejitsu shared VM could handle a lot more users than that.

Nodejitsu makes it really easy to add as many servers as you want behind a domain, and their load balancers Just Work, even for WebSockets. I pay $3/server/month, or about 10 cents a day for each server. I could run 50 servers from December 24-26 and pay $15 for the trouble. That's a good deal.

A downside of Nodejitsu's approach to scaling is that there's no way to add a new server behind the balancer without disconnecting and reshuffling all currently connected users. Since isitchristmas' whole point is longform user interaction, this is really disruptive and unpleasant. In an ideal world, adds would be seamless, removes would only disturb the users on the removed server, and Nodejitsu would provide a mechanism to automatically adjust server levels. Nodejitsu's upcoming business plan will provide an auto-scaling option, but it won't be much good for a project like this unless server scaling is non-disruptive.

Overall, Nodejitsu is a fine company with a great team, and you get a good deal with them. I definitely recommend them as a host. It's really amazing the kind of power you can lease on the Internet now for just a few bucks, and Nodejitsu gives you that power.

Of course, this is still partly just theory: I'm writing this as the traffic is just ramping up towards midnight, so it's possible it could all fall to hell! I'm excited to find out.

<strong>Update:</strong> As it turned out, Nodejitsu held up well - but I forgot to scale out my Mongo database. I never bumped it above one instance, which was a bottleneck that yielded me some stressful midnight crashes. I panicked and just moved the HTML/JS delivery part back to my old host, and used Nodejitsu only for streaming, which solved it.

## Broadcasting, Analytics, and Monitoring in Redis

I use <a href="http://redis.io/">Redis</a> to keep track of connected users, and to store analytics on every visitor - their country, browser, OS, and whether they connected with WebSockets or Comet. Every visit increments a bunch of different counters, based on different combinations of values. It's anonymous and extremely helpful.

By having each server report connected users to the same Redis server, and snapshot its own system vitals to Redis every 5s, I can have any one of them produce a dashboard of all users and all servers.  This is crucial for me in knowing when to add and remove servers to handle load.

Redis' pub/sub messaging system is a dream. By having each server subscribe to a few different channels, I was able to build tiny systems to send down live config changes (like adjusting mouse framerate) and arbitrary commands (like forcing reconnects) to clients from the Redis CLI, and to run a little chat room across every server entirely via the developer console. Redis' architecture made the code to do all this very small.

I'm using a micro instance on <a href="https://openredis.com/">OpenRedis</a>. They respond quickly to email, their site reads and works well, and they have reasonable prices (50MB for $8/month goes a long way). They also just opened up some servers inside <a href="http://joyent.com/">Joyent's</a> data center, which is where my <a href="http://nodejitsu.com/">Nodejitsu</a> servers are hosted: bonus.

## A Better Broadcast?

Something still feels inefficient. While I do need an application layer to register users, create a dashboard, and keep analytics, all I want to do with mouse events is multicast them as quickly as possible to everyone else. The best way for me to do this right now is in Node, with <a href="https://github.com/isitchristmas/sockets/blob/master/app.js#L53">a for loop</a>. <a href="http://en.wikipedia.org/wiki/V8_(JavaScript_engine)">V8</a> is shockingly fast and all, but Redis is faster and its pub/sub system is optimized for multicasting.

I could have Node publish mouse events into a Redis channel, instead of doing a for loop, but the faster Redis multicast processing would probably be outweighed by the extra Redis round trip. Plus, the same Node process would ultimately need to deliver all the messages to users, so it's hard to see the gain.

Ideally, all users' browsers would connect directly to a messaging server whose sole purpose is to blindly multicast. If Redis supported WebSockets, that would fit the bill, though exposing a whole Redis server to the outside world could be a big problem.

Is there anything out there that does this? <a href="http://www.rabbitmq.com/blog/2012/05/14/introducing-rabbitmq-web-stomp/">RabbitMQ-Web-STOMP</a> seems closer, <s>but still uses a SockJS/Node server as an intermediary</s>. [ed: Actually, it's a RabbitMQ plugin that exposes a SockJS endpoint directly.] <a href="https://github.com/progrium/nullmq">NullMQ</a> also <a href="http://avalanche123.com/blog/2012/02/25/interacting-with-zeromq-from-the-browser/">looks promising</a>, though perhaps no longer maintained. Figuring out a tighter multicast loop is the main thing I'll work on if I do this again. Also intriguing is <a href="http://webd.is/">Webdis</a>, a tiny C-based HTTP server whose sole job is to add an HTTP layer on top of Redis. Its main downside is that its WebSocket support is relatively new, and appears to have <a href="https://github.com/nicolasff/webdis/issues/search?q=websockets">issues</a>.

## The Code

Both Node.js applications are open source under permissive licenses:

<a href="https://github.com/isitchristmas/web">github.com/isitchristmas/web</a> - Looks up user's country code, renders page. Node + MongoDB.<br/>
<a href="https://github.com/isitchristmas/sockets">github.com/isitchristmas/sockets</a> - Manages all socket interaction. Node + SockJS + Redis.

Pull requests welcome. Or, if you want to correct a mis-translation, <a href="https://github.com/isitchristmas/web">file a ticket here</a>.

Thanks for reading this, for not DOSing me, and for not calling out how obviously pretentious this whole enterprise is! Hooray for Christmas.