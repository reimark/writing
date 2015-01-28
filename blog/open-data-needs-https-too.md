<blockquote class="twitter-tweet" lang="en"><p>I’m increasingly convinced that SSL is an inherent requirement to publish open data. It’s the easiest way to ensure that data is authentic.</p>— Waldo Jaquith (@waldojaquith) <a href="https://twitter.com/waldojaquith/status/551089956870193152">January 2, 2015</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Recently, [Tim Berners-Lee](https://en.wikipedia.org/wiki/Tim_Berners-Lee) (inventor of the web  and [President of the Open Data Institute](http://theodi.org/team/timbl)) informally [asked a W3C working group]((http://lists.w3.org/Archives/Public/public-webappsec/2015Jan/0002.html)) to consider relaxing "mixed-content" restrictions on fetching insecure data in web browsers, apparently [in order to support "open data mashups"](https://github.com/w3ctag/web-https/issues/12). 

Berners-Lee [supports a secure web](http://www.theguardian.com/technology/2013/dec/03/tim-berners-lee-spies-cracking-encryption-web-snowden), and he argued that loosening the rules would ease the web's transition to HTTPS. However, loosening mixed-content restrictions for open data is technically unworkable<sup><a href="#fn1" id="ref1">1</a></sup>, and the proposal is unlikely to go far.

But his proposal has a clear and (sadly) correct implication: a whole lot of open data is only available over an insecure connection.

Which is too bad, because **open data especially needs HTTPS**. From a [response I posted](https://github.com/w3ctag/web-https/issues/12#issuecomment-68627767) on GitHub:

> Any data that's important enough to call "open data", that we think there's value in people, businesses, and civil society depending on -- is important enough that we should demand that it's provided over a secure and private connection.
> 
> This is why Gov.UK [requires HTTPS for government services](https://www.gov.uk/service-manual/domain-names/https.html), and why 18F [will only build .gov sites that use HTTPS](https://18f.gsa.gov/2014/11/13/why-we-use-https-in-every-gov-website-we-make/). It's why Sunlight ensures [its legislative APIs are encrypted](https://sunlightfoundation.com/blog/2014/01/28/encrypting-our-congress-api-and-protecting-your-location/), and why HTTPS is [increasingly](https://twitter.com/waldojaquith/status/551089956870193152) the [priority](https://twitter.com/JoshData/status/378616437020971008) of the open data [community](https://twitter.com/courtlistener/status/354388742569598977).
>
> "Open data" is a broad term, covering services and information that touch every part of our lives. No ISP, cafe, or government should be able to use HTTP requests for open data to [identify someone's location](https://www.propublica.org/article/spy-agencies-probe-angry-birds-and-other-apps-for-personal-data), [profile their health](http://www.washingtonpost.com/blogs/the-switch/wp/2014/11/07/federal-sites-leaked-the-locations-of-people-seeking-aids-services-for-years/), or [track their browsing activity](https://www.eff.org/deeplinks/2014/11/verizon-x-uidh) -- or to sell the metadata to someone who will. Open data on the web has to serve the public's interest, and HTTPS is the most basic way to achieve that.

So why are so many of the leaders of the open data community so far behind?

* **[Code for America](http://www.codeforamerica.org)** sets a bad example for its fellows and brigades by not using HTTPS on its website or its [API](http://codeforamerica.org/api/).
* **[OpenCongress](http://www.opencongress.org)** <s>sets a terrible example by literally transmitting passwords in the clear during account creation (and, until I [badgered them for months](https://github.com/sunlightlabs/opencongress/issues/64#issuecomment-54002366), during every login). What's mystifying is that OpenCongress already supports HTTPS, and chooses not to simply force it.</s> **Update:** [OpenCongress now forces HTTPS](https://twitter.com/konklone/status/560541372084944896) across the board.
* Similarly, the homepages for the **[Sunlight Foundation](http://sunlightfoundation.com)**, the **[Open Data Institute](http://theodi.org)**, and **[Data.gov](http://www.data.gov)** are all HTTPS-ready, but don't force it -- and so Google leads all of their visitors to the HTTP version. You'd only know they supported it by typing in the 's' yourself.
* Anyone who scans the [complete list of .gov domains](https://18f.gsa.gov/2014/12/18/a-complete-list-of-gov-domains/) will find that the overwhelming majority of `.gov` domains are served over insecure connections.

<blockquote class="twitter-tweet" data-conversation="none" lang="en"><p><a href="https://twitter.com/EdFelten">@EdFelten</a> Government sites which distribute the law or other critical information should also use always-on https. Matter of trust.</p>— Carl Malamud (@carlmalamud) <a href="https://twitter.com/carlmalamud/status/30561890337820672">January 27, 2011</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

To be clear, I understand that transitions can be work, especially for APIs. When I [moved Sunlight's Congress API to HTTPS](https://sunlightfoundation.com/blog/2014/01/28/encrypting-our-congress-api-and-protecting-your-location/), we held off on forcing a redirect while I [set up analytics](https://github.com/sunlightlabs/congress/commit/bb862216d59db7872ecbc39755f94bf5288680fa) to track use of encryption, scrambled around GitHub [updating](https://github.com/mcwhittemore/sunlight-congress-api/pull/9) [popular](https://github.com/sunlightlabs/python-sunlight/pull/9) [clients](https://github.com/steveklabnik/sunlight-congress/pull/30), and eventually [emailing users directly](https://github.com/18F/api.data.gov/issues/34#issuecomment-38859164) warning them to switch. It cost me time and energy, and owners of popular services are understandably risk averse.

But plenty of other open data services have found the time to do it. [GovTrack](https://twitter.com/JoshData/status/378616437020971008) and [CourtListener](https://twitter.com/courtlistener/status/354388742569598977) moved in 2013, and Carl Malamud has been going [out of his way](https://twitter.com/carlmalamud/status/533068374457069568) to obtain only the most top-notch certificates for many years.

And frankly, it's just the way the internet is moving.

* The W3C's Technical Architecture Group is working on [Securing The Web](https://w3ctag.github.io/web-https/), whose draft findings say that the web should actively prefer secure connections and transition entirely to HTTPS. 
* The Internet Engineering Task Force (the internet's standards body) said in May 2014 that [pervasive monitoring is an attack](https://datatracker.ietf.org/doc/rfc7258/).
* The IETF's parent, the Internet Architecture Board, said [encryption should be the norm](http://www.internetsociety.org/news/internet-society-commends-internet-architecture-board-recommendation-encryption-default) in November 2014.
* The Chrome security team is working on [marking every plain HTTP request as non-secure](https://www.chromium.org/Home/chromium-security/marking-http-as-non-secure).

In 2013, we got leaks about the NSA and GCHQ exploiting their access to internet backbones to [correlate](https://www.propublica.org/article/spy-agencies-probe-angry-birds-and-other-apps-for-personal-data) and [copy](https://www.eff.org/files/2014/07/24/backbone-3c-color.jpg) [wholesale](http://www.theatlantic.com/international/archive/2013/07/the-creepy-long-standing-practice-of-undersea-cable-tapping/277855/) as much internet traffic as they possibly can. In 2014, we got Comcast and Verizon [injecting ads](http://arstechnica.com/tech-policy/2014/09/why-comcasts-javascript-ad-injections-threaten-security-net-neutrality/) and [tracking beacons](https://www.eff.org/deeplinks/2014/11/verizon-x-uidh) into their customers' internet use.

Those who love and care for the internet agree: **those are all attacks**, and they affect all of us. Strong HTTPS makes those attacks impossible to pull off at global scale. So in 2015, I hope we see the open data community tighten up its wires with the rest of us.

<blockquote class="twitter-tweet" lang="en"><p>All of CourtListener is now only available over https. Here's to making your research as private as possible.</p>— CourtListener (@courtlistener) <a href="https://twitter.com/courtlistener/status/354388742569598977">July 8, 2013</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
<hr/>

<sup id="fn1">1. <strong>Mixed content</strong> is when you visit a website over `https://`, and it tries to load images or fonts over insecure `http://`. Browsers today will let images by with a warning, but will block fonts, scripts, and other forms of "active" data. Without this protection, the promise of a website's `https://` doesn't mean very much, because pulling in insecure assets could completely compromise the security of the website. <a href="#ref1" title="Jump back">↩</a></sup>