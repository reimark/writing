<a href="https://twitter.com/fisacourt"><img src="https://konklone.com/assets/images/blog/fisacourt/fisc-twitter-2.png" class="border" /></a>

**Short version**: The FISA Court has a [new website](http://www.fisc.uscourts.gov/), and [@FISACourt](https://twitter.com/fisacourt) is way smarter because I'm turning their [entire docket into data](https://github.com/konklone/fisacourt/tree/docket/filings). 

**Longer version:**

[One year ago](https://www.eff.org/deeplinks/2014/05/snowden-anniversary), a large population was told their entire network was being surveilled. A short time later, the [Foreign Intelligence Surveillance Court](https://en.wikipedia.org/wiki/United_States_Foreign_Intelligence_Surveillance_Court) (also known as the "FISA Court", or "FISC"), which oversees surveillance policy in the US, [began publishing a docket](http://arstechnica.com/tech-policy/2013/06/for-the-first-time-secret-court-wont-block-release-of-nsa-opinion/) after 35 years of silence. 

Ever since, I've been following the Court by running [@FISACourt](https://twitter.com/fisacourt) on Twitter, which does stuff like this:

<blockquote class="twitter-tweet" lang="en"><p>The FISC has ordered the gov't to file, in writing, why they failed to inform the FISC of existing relevant lawsuits: <a href="http://t.co/gB7LoJwuZL">http://t.co/gB7LoJwuZL</a></p>— FISA Court (@FISACourt) <a href="https://twitter.com/FISACourt/statuses/447079362995974144">March 21, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

@FISACourt is powered by an [open source tool](https://github.com/konklone/fisacourt) I wrote to watch the Court's public docket site. Within 5 minutes of any change to the docket, the tool automatically posts a tweet with a link to the HTML change, emails me, and texts my personal cell phone. When that happens, I quickly investigate and read anything that was posted, and follow up with a hand-written explanation.

### Do your reading

Because of @FISACourt, I've read basically every public filing the Court has made, and have very often been the First To Know and First To Tweet.

Reading all those filings feels amazing. If you want to know what's going on in this world, **you need to read primary sources**. The public docket [tells a story](https://gist.github.com/konklone/6314d7de4b1354e4a364), and few in the media are doing any more than reporting on the most exciting spikes.

The FISC's docket is a tiny piece of the action surrounding surveillance, but since the nation's only Court dedicated to surveillance first opened its ad hoc internet welcome mat in June of 2013, allowing the public a window into its work for the first time in 35 years, we've gotten to see:

* The Court declassifying and [publishing](https://twitter.com/FISACourt/status/459804652532686848) a [full justification](http://www.uscourts.gov/uscourts/courts/fisc/br14-01-opinion-order-140425.pdf) for allowing bulk collection of phone metadata under the Fourth Amendment.
* An [actual order](https://twitter.com/FISACourt/status/391250444049063936) by the Court authorizing bulk collection of telephone metadata under section 215 of the Patriot Act — for what I believe is the first time — along with a legal justification for granting it.
* The Department of Justice [scolded by the Court](https://twitter.com/FISACourt/status/447079362995974144) for failing to inform the Court of [relevant pending lawsuits](https://twitter.com/FISACourt/status/444186775100358656) in a dispute with the EFF over preserving bulk telephony metadata.
* The Department of Justice [put on the spot by the Court](https://twitter.com/FISACourt/status/403209352737062912) after refusing to declassify any part of an opinion interpreting section 215 of the Patriot Act. (The government had [previously been ordered](https://twitter.com/FISACourt/status/393737868675256322) by the Court to review it for declassification.)
* The sad end to a once-promising lawsuit by major technology companies [chafing](https://twitter.com/FISACourt/status/415273032563699712) at the government's restrictions from publishing exact numbers of request statistics: the companies [settled with the government](https://twitter.com/FISACourt/status/427942116845576192), and increased the granularity of reporting from 1000's to 250's, *if* some kinds of requests are jumbled together.
* The Court [responding](https://twitter.com/FISACourt/status/369824547010134018) to inquiries from prominent senators by [publicly describing](http://www.uscourts.gov/uscourts/courts/fisc/honorable-patrick-leahy.pdf) its operations, and [following up](http://www.uscourts.gov/uscourts/courts/fisc/ranking-member-grassley-letter-131011.pdf) with numbers on how often they make the government revise their requests before granting them (~25% of the time).

We also saw the FISA Court [publish](https://twitter.com/FISACourt/status/452174858705985536) a law student's brief arguing the Court's unconstitutionality (and [citing](https://twitter.com/konklone/status/452190149632610304) my [blog](https://konklone.com/post/the-door-to-the-fisa-court)!), and then [retract](https://twitter.com/FISACourt/status/453350951811022849) it without any notice (here's [the original](http://konklone.io/fisacourt/backup/2014-04-04-michael-walsh-motion-for-leave-to-file-amicus-brief.pdf)). I'm not judging the merits of the brief's arguments, but the Court's [decision to deny the request as "moot"](http://www.fisc.uscourts.gov/sites/default/files/Misc%2013-03%20Order-14.pdf), after **making** it moot by sitting on the request for 4 months, is obnoxious and beneath the Court.

Nonetheless, the Court is to be praised for making it possible to see all this. The Court, so secret that they [won't label their door](https://konklone.com/post/the-door-to-the-fisa-court), made a quick-and-dirty website last year while under the international spotlight, and just started uploading PDFs. Messy, but compared to the 35 years of silence before it, it was a huge step.

### A brand new website

<a href="http://www.fisc.uscourts.gov"><img src="https://konklone.com/assets/images/blog/fisacourt/fisc-header-2.png" class="border" style="padding-top: 15px" /></a>

In another step, the FISA Court recently relaunched their site, now at [fisc.uscourts.gov](http://www.fisc.uscourts.gov). It's a Real Website, built with the open source framework Drupal. It offers some new things, like their [judges](http://www.fisc.uscourts.gov/current-membership), [rules](http://www.fisc.uscourts.gov/rules-procedure), and even [an RSS feed](https://twitter.com/FISACourt/status/461587141265346560).

Of course, the filings are still scanned, un-searchable image PDFs, their utility hobbled by some combination of backwards processes and redaction paranoia, and the FISC's own search engine [suffers the consequences](http://www.fisc.uscourts.gov/search/node/surveillance). But the RSS feed is a big deal -- anyone can follow the docket, in more-or-less real time, without needing something like @FISACourt.

Most importantly, the Court is committing to a public presence in a way their last docket never did. The site is here to stay, at its own URL and subdomain, and there's a much more solid foundation from which to make technical improvements. They're acknowledging their visible role in our nation's democracy, and deliberately engaging the public to help them better understand the Court's work. That's courageous and an investment, and I appreciate it.

### Turning the FISA Court into data

Naturally, the new website immediately broke @FISACourt. I decided to see it as an opportunity, and [rewrote the whole tool](https://github.com/konklone/fisacourt/pull/15) to produce a comprehensive, up-to-date dataset of the Court's public docket.

I'm now doing a proper crawl of the entire FISC website, and saving [data for every filing](https://github.com/konklone/fisacourt/tree/docket/filings). For example, [this motion](http://www.fisc.uscourts.gov/public-filings/order-june-17-2013) becomes:

```yaml
 ---
 file_url: "http://www.fisc.uscourts.gov/sites/default/files/105B%28g%29%2007-01%20Order-1.pdf"
 title: "Order (June 17, 2013)"
 dockets:
 - name: "105B(g) 07-01"
   url: "http://www.fisc.uscourts.gov/docket/105bg-07-01"
 posted_on: '2014-04-15'
 landing_url: "http://www.fisc.uscourts.gov/public-filings/order-june-17-2013"
 id: "order-june-17-2013"
 last_sha: "ae16d4a74586762659efe28cb8611a796f42462380a3f140475f549a7b047cd8"
 last_etag: "240e18-5c510-4f71750b21840"

```

That data is in [YAML](https://en.wikipedia.org/wiki/YAML#Features), a humane data format that lends itself well to human readability, and [line-by-line diffs](https://github.com/konklone/fisacourt/commit/e15d2c6deca3456ccc0c453d23019187c00ac608#diff-79).

I'm also downloading [the actual PDFs](https://github.com/konklone/fisacourt/tree/docket/filings/pdfs), and watching them for any future changes. As the Court showed with its unexplained withdrawal detailed above (and as the [Supreme Court frequently demonstrates](http://www.nytimes.com/2014/05/25/us/final-word-on-us-law-isnt-supreme-court-keeps-editing.html?_r=0)), it's important to watch the public record for revisions of its history. (Update: my friend [David Zvenyach](https://twitter.com/vdavez) is now operating a similar bot to watch the Supreme Court, at [@SCOTUS_servo](https://twitter.com/scotus_servo).)

The data and PDFs are [versioned in their own branch](https://github.com/konklone/fisacourt/commits/docket), so you can use GitHub's [dedicated Atom feed](https://github.com/konklone/fisacourt/commits/docket.atom) watch every changes the system detects, or use the [GitHub Contents API](https://developer.github.com/v3/repos/contents/#get-contents) to [sync up](https://api.github.com/repos/konklone/fisacourt/contents/filings?ref=docket).

### Keep watching

<figure>
<a href="https://www.resetthenet.org"><img src="https://konklone.com/assets/images/blog/fisacourt/reset.png" class="border" style="padding-top: 15px" /></a>
<figcaption>Source: <a href="https://www.resetthenet.org" target="_blank">Reset the Net</a></figcaption>
</figure>

Nearly a year after Snowden revealed the extent of government surveillance, some of the spotlight and novelty has faded. People no longer drop everything to read a leak-driven Guardian or Intercept story. But the technical and legal mechanics of surveillance, now partly visible to the public eye, are going to be fought over for years to come. We need to keep watching.

If you want to use the FISA Court's data, or the scraper, or have any questions at all, please [open an issue](https://github.com/konklone/fisacourt/issues?state=open) over at the project. It's [all public domain](https://github.com/konklone/fisacourt/blob/master/LICENSE) and you don't need my or anyone's permission, but I love to help out and talk about this stuff.

And hey: if you're reading this and you actually **work** for the FISA Court, check out the [notes I wrote for the Court](https://github.com/konklone/fisacourt#a-note-to-the-fisc) on how to make your website better, and how to eliminate the need for a system like mine to scrape your HTML. (Also: maybe set up a public email address.)