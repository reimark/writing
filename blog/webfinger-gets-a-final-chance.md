[WebFinger](http://webfinger.net/) is **finally final**, with a real RFC and everything! It's [RFC 7033](http://tools.ietf.org/html/rfc7033). And unlike a lot of RFCs you might have glanced at, shuddered, and immediately closed, WebFinger's is **actually simple**. 

WebFinger is a standard way to attach information to an email address, or other account. Mine is at [https://konklone.com/.well-known/webfinger?resource=acct:eric@konklone.com](https://konklone.com/.well-known/webfinger?resource=acct:eric@konklone.com):

```json
{
  "subject": "acct:eric@konklone.com",
  "properties": {
    "http://schema.org/name":"Eric Mill"
  },
  "links": [
    {
      "rel": "http://webfinger.net/rel/profile-page",
      "href": "https://konklone.com"
    },
    {
      "rel": "http://webfinger.net/rel/avatar",
      "href": "https://secure.gravatar.com/avatar/ac3399caecce27cb19d381f61124539e.jpg?s=400"
    }
  ]
}
```

Go ahead and peek at the data if you want to - it's a tiny piece of JSON, a link to my blog and my [avatar](https://secure.gravatar.com/avatar/ac3399caecce27cb19d381f61124539e.jpg?s=400). (WebFinger is HTTPS only, so you've got to [take care of that first](https://konklone.com/post/switch-to-https-now-for-free).)

To understand why this strange thing called WebFinger exists, you have to go back to a more innocent time — those heady days before Google+ — when people once believed that maybe regular people one day wouldn't have to keep using passwords.

## A Sorry History

It's been a long time since [WebFinger was announced](http://hueniverse.com/2009/08/introducing-webfinger/) by Eran Hammer in 2009, and thrust into the spotlight in 2010 by what seemed at the time like a blaze of Open Web Glory: the [launch of Google Buzz](http://googleblog.blogspot.com/2010/02/introducing-google-buzz.html).

Along with Google Buzz came a decision by Google to invest in [a raft](https://web.archive.org/web/20100212031303/http://code.google.com/apis/buzz/documentation/) of decentralized, open-web protocols: [Salmon](http://www.salmon-protocol.org/) for comments, [Pubsubhubb](http://code.google.com/p/pubsubhubbub/) for subscriptions, and WebFinger for identity.

Of course, Buzz was a huge failure, and looking back at the design, and the way Google talked about it, it's clear that the Open Web crowd was the **only** constituency Buzz was serving. That the Buzz team didn't blink at [automatically publicly surfacing your most-emailed contacts](http://www.businessinsider.com/warning-google-buzz-has-a-huge-privacy-flaw-2010-2) is just more evidence that Buzz was an all-engineering-driven effort.

But at the time, [I was very excited](/post/makes-mouths-happy):

> With every open standard we adopt, with every decentralized protocol we weave into our communication, the Internet becomes more resilient, more intelligent, and harder to oppress. Even if Google Buzz becomes a flop like Wave seems to be, if it gives WebFinger and Pubsubhubbub the boost they need to see mainstream adoption, then all of our futures will be brighter for it.

A few months later, I was still very excited, and I gave an [Ignite talk on WebFinger](http://www.youtube.com/watch?v=Y26c9MNQLyc) at RailsConf. 

<p style="text-align: center"><iframe class="youtube" src="//www.youtube.com/embed/Y26c9MNQLyc" frameborder="0" allowfullscreen></iframe></p>

Then, Google Buzz collapsed, and the energy got sucked out of the room. None of the standards on the sidebar of the [original Buzz APIs page](https://web.archive.org/web/20100212031303/http://code.google.com/apis/buzz/documentation/) are alive and well now, except for [OAuth](http://oauth.net/) (whose v2 is in [a different kind of hell](http://hueniverse.com/2012/07/oauth-2-0-and-the-road-to-hell/)).  

And yet: the [WebFinger mailing list](http://www.ietf.org/mail-archive/web/webfinger/current/maillist.html) kept creeping along, refusing to die. And now, 3 years later, seemingly out of nowhere, WebFinger is ready for anyone to implement.

## Will Anyone Bother?

Now the obvious question is: is this worth anyone's time? And honestly, I don't know.

I spent a whole free [hackathon](http://fedscoop.com/code-dc-calls-furloughed-feds/) day working on WebFinger, and at the end of it all, a reporter came by and asked us all about our projects. The best I could think of to say was "Er....remember OpenID?"

[OpenID](http://en.wikipedia.org/wiki/OpenID) was and is a way to turn the tables on how people relate to web sites. Instead of logging into them, **get the website to log in to you**. That's the idea behind decentralized identity. But OpenID's major problem was that to log in, you typed in your OpenID URL, and **no one thinks of themselves as a URL**. Logging in with a URL feels weird, and is hard to teach people. OpenID had [other problems](http://developer.yahoo.com/blogs/ydn/yahoo-releases-openid-research-7479.html) too, but it boils down to basic usability. 

A founding goal of WebFinger was to address this. Since WebFinger lets you go simply and automatically from email address to any other data, if OpenID URLs were attached to emails, then your users could log in to your website using only their emails. Like regular login, but without a password. People can dig that.

But OpenID has [faded](http://productblogarchive.37signals.com/products/2011/01/well-be-retiring-our-support-of-openid-on-may-1.html) [away](https://www.myopenid.com/), replaced across the web by Log In With Facebook, or Twitter. It's been years since Chris Messina [proposed](http://factoryjoe.com/blog/2010/01/04/openid-connect/) a successor, [OpenID Connect](http://openid.net/connect/), as a simpler form of OpenID that used email addresses instead of URLs — using WebFinger! Of course, the standards process wore on and blew up into complexity again, and it appears to be going nowhere. Maybe the closest thing alive is Mozilla's [Persona](http://www.mozilla.org/en-US/persona/), but: seen a Log In With Persona button anywhere lately?

When I got home from the hackathon, I posed the question [to the WebFinger mailing list](http://www.ietf.org/mail-archive/web/webfinger/current/msg00860.html):

> So, now that OpenID is dead, what's the one line explanation for why WebFinger is important? What's the path forward to making WebFinger something people are incentivized to support?
> 
> Should we be pushing really hard to resuscitate OpenID via OpenID Connect? Do we just need to wait for internal lobbying inside of Google/Microsoft/Twitter/etc to pay off in some announcement? I know WebFinger supports more than email lookup -- is there some particular killer app people were envisioning when they lobbied for that feature?

It [got](http://www.ietf.org/mail-archive/web/webfinger/current/msg00863.html) a [handful](http://www.ietf.org/mail-archive/web/webfinger/current/msg00866.html) of [responses](http://www.ietf.org/mail-archive/web/webfinger/current/msg00861.html), but nothing that filled me with hope. Making Bitcoin wallet IDs more human readable just isn't going to be the lever we need to get the web to jump on board. We need to find some more ideas.

One of the few things that genuinely excites me is seeing Google have [Tim Bray work on identity](http://www.tbray.org/ongoing/When/201x/2012/06/29/Becoming-an-Identity-guy). I'm not exactly sure what that work *is* yet, but Tim is extremely smart, committed to simplicity, and one of the people responsible for getting WebFinger out the door. It's not impossible that Google could yet surprise us, even as it leaves other [important standards](https://www.eff.org/deeplinks/2013/05/google-abandons-open-standards-instant-messaging) behind.

## Forward: With Code

Nonetheless, **this is WebFinger's one real chance**. It stayed alive because a group of people — including people from Google and Microsoft — believed there's a meaningful, achievable idea here that, under the right circumstances, could see web-wide use. We should make the most of the chance we have. 

Will Norris and Matthias Pfefferle have created [webfinger.net](http://webfinger.net/), where you can test out [WebFinger lookups](http://client.webfinger.net/lookup?resource=eric%40konklone.com) and find out what the hell it is. On my day of WebFinger work, I contributed some improvements to webfinger.net, and worked on two projects to make it easier to add WebFinger data to an [email address whose domain you own](https://konklone.com/post/take-control-of-your-email-address):

* **[sinatra-webfinger](https://github.com/konklone/sinatra-webfinger)**: An extension for [Sinatra](http://sinatrarb.com/) that makes it pretty dirt easy. I'm [using it](https://github.com/konklone/konklone/blob/master/konklone.rb#L157) for this blog.
* **[jekyll-webfinger](https://github.com/konklone/jekyll-webfinger)**: A plugin for Jekyll sites to generate WebFinger data for a domain. Jekyll's a static site generator, so it has some limitations (the biggest is that it'll return the same data for any email address, which isn't technically in-spec but should work in practice), and plugins aren't allowed on GitHub Pages. But, if you're using Jekyll outside of GitHub, here you go.

Also, if you're using Apache, Aaron Parecki has a nice [example Apache .htaccess](https://gist.github.com/aaronpk/5846789) that uses a static file.

If you're still rocking a `@gmail.com` address or something, and don't control their WebFinger support, you can still participate! **[WebFist](http://webfist.org/)** is a sort of community fallback service. Set up a WebFinger endpoint anywhere you want, then email `fist@webfist.org` with `webfinger = https://your-actual.com/webfinger/endpoint`, and they'll list an entry for you that directs participating clients to your endpoint.

I don't know whether this turns out to be the the beginning of WebFinger's next chapter, or just a coda to a shared, flawed dream. But right now, WebFinger is a working piece of what a better Web could be, and I want to see it get the best shot it can.