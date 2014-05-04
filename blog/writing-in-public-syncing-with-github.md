<figure>
<a href="https://twitter.com/alykat/status/347719216499130369" target="_blank"><img src="/assets/images/blog/syncing/work-in-public.jpg" /></a>
<figcaption>unofficial motto of the NPR News Applications team, <a href="http://www.flickr.com/photos/alykat/9093785148/">by Alyson Hurt</a></figcaption>
</figure>

For a while now, I've admired my friend [Ben Balter](https://twitter.com/benbalter) for writing out in the open. His blog is built on [GitHub Pages](https://pages.github.com/), which means that for every [piece](http://ben.balter.com/2014/03/21/want-to-innovate-in-government-focus-on-culture/) on his blog, you can see [each draft](https://github.com/benbalter/benbalter.github.com/commits/master/_posts/2014-03-21-want-to-innovate-in-government-focus-on-culture.md) and [revision](https://github.com/benbalter/benbalter.github.com/commit/d39bfec676299afed1c1018cd83a15f31a81ad8e) along the way. 

As importantly, Ben takes advantage of GitHub to truly embrace collaboration — whether that's [detailed debate on a complex topic](https://github.com/benbalter/benbalter.github.com/pull/98) as he works through issues, or just graciously [fielding](https://github.com/benbalter/benbalter.github.com/pull/108) 
[my](https://github.com/benbalter/benbalter.github.com/pull/105) [constant](https://github.com/benbalter/benbalter.github.com/pull/91) [typo](https://github.com/benbalter/benbalter.github.com/pull/77) [fixes](https://github.com/benbalter/benbalter.github.com/pull/99). The end product is better for it, and everyone feels engaged and invested.

It's such a healthy, beautiful approach to public writing. Why doesn't every newspaper in the world work this way?

### Making this work for my blog

<img style="padding-top: 10px" class="border" src="/assets/images/blog/syncing/github-diff-2.png" />

And why not my blog? Well, Ben has the advantage of using GitHub Pages, which weaves his blog directly into [GitHub](https://github.com), one of the greatest systems for collaboration that mankind has yet crafted. And GitHub Pages, while [incredibly powerful](https://konklone.com/post/the-power-and-potential-of-github-pages), isn't for everyone. For me, I like having a database that can hold private content, and a comment system that belongs to me and not to Disqus. My blog is built on [Sinatra](http://www.sinatrarb.com/) and [MongoDB](https://www.mongodb.org/), which costs more time and money than GitHub Pages, but affords me more control.

Fortunately, GitHub is much more than a nice website and host -- it's also home to an [extraordinarily rich and well-documented API](https://developer.github.com/v3/), through which you can order GitHub to do just about anything you need. 

Using it, I've neatly integrated my published blog posts with a new GitHub repository, [konklone/writing](https://github.com/konklone/writing). There's now an "edit this post on GitHub" link on the sidebar, to make the connection obvious. You can [suggest an edit to this post itself](https://github.com/konklone/writing/edit/master/blog/syncing-a-handcrafted-blog-with-github.md) with the greatest of ease, and when I accept your edit, the post will automatically update.

I don't have to change my workflow or give up my database, but I still get a [public revision history](https://github.com/konklone/writing/commits/master/blog/switch-to-https-now-for-free.md) and the ability to accept pull requests that automatically update my blog as soon as I press the `Merge` button.

If you're curious about the technical mechanics, I created two pull requests that explain the gritty details:

* [Syncing TO GitHub](https://github.com/konklone/konklone/pull/125): Any published post with an assigned URL to a file on GitHub will, upon save, use the GitHub [Repo Contents API](https://developer.github.com/v3/repos/contents/) to update that file with the post's contents. A GitHub URL is assigned to a post upon first publish, which then automatically creates a file in [konklone/writing](https://github.com/konklone/writing).
* [Syncing FROM GitHub](https://github.com/konklone/konklone/pull/126): The `writing` repo has a [webhook](https://github.com/blog/1778-webhooks-level-up) enabled that sends a POST to a special endpoint in my blog upon any content changes. My blog accepts those changes from GitHub, while using a log of previously synced commits to avoid infinite sync loops.

Though my code is customized for my blog, you could take this approach with just about anything -- it's just APIs over HTTP, the *lingua franca* of the Internet, along with a couple extra fields on posts to keep everything straight. It's not that bad.

### News In Public

I'd like this blog to be known for high quality, accurate pieces that people share and return to. I also just want to write good stuff that reads clearly. It's a lot easier to make all that happen with an obvious path for readers to contribute, and an annotated history of changes.

I don't see any reason why a major newspaper can't do the same thing. The New York Times cares deeply about precision, enough to run <a href="http://www.nytimes.com/2011/12/26/us/navigating-love-and-autism.html">corrections like this</a>:

<a href="http://www.nytimes.com/2011/12/26/us/navigating-love-and-autism.html"><img src="/assets/images/blog/syncing/correction.png" class="border" /></a>

Yet when the Times make changes due to less funny mistakes, like opening a [woman rocket scientist's obituary](http://www.thedailybeast.com/articles/2013/03/31/new-york-times-changes-sexist-obit.html) with a description of her cooking, you won't see a correction notice at the bottom of [the current article](http://www.nytimes.com/2013/03/31/science/space/yvonne-brill-rocket-scientist-dies-at-88.html?pagewanted=all&_r=0). You'll have to hope someone else caught it and rescued it from Google's cache or something.

Don't even try to keep track of the constant headline tweaking. In one recent example, the Times was being [criticized](https://twitter.com/dangillmor/status/455130457223725057) for essentially running the headline the Obama administration wanted them to. The web's complex mechanics clearly demonstrates the Times responding in fits and starts:

<blockquote class="twitter-tweet" lang="en"><p>Between the URL slug, the Twitter card, and the final headline, a NYT editor and reporter are twisting in the wind <a href="http://t.co/w3q1LFsevz">pic.twitter.com/w3q1LFsevz</a></p>— Eric Mill (@konklone) <a href="https://twitter.com/konklone/statuses/455134683940925441">April 13, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

I'm picking on the New York Times here, as my favorite newspaper and the United States' paper of record, but all of this applies to any major newspaper. Can you think of a single one with a transparent changelog?

### Authority Through Obscurity

I've heard people tell me that adding malleability and collaboration to their public work would reduce its credibility and authority. That's not much different than believing that you're [more secure by hiding your security choices](http://lists.w3.org/Archives/Public/site-comments/2014May/0002.html). Truth withstands public scrutiny, and is stronger for it. It's not like it has to be Wikipedia: on GitHub, you're in total control over what changes you accept.

And it doesn't have to be through GitHub! Any system that lets readers suggest concrete fixes and improvements, lets writers and editors easily accept them into the published version, and offers the public a record of a story's evolution would do just fine.

Working in public this way is a set of principles shaped by the collaborative world of open source code. Practiced often, it becomes like breathing. 

The world of online journalism in 2014 is increasingly technology-driven, and staffed with excited people who were raised by the Internet -- it can and should embody these principles just as vigorously.