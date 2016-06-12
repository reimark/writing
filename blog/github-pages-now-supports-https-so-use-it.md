<div class="callout">
<strong>Update, June 2016:</strong> 
GitHub recently announced <a href="https://github.com/blog/2186-https-for-github-pages">official HTTPS support for github.io domains</a> on GitHub Pages!
<br/><br/>
This is <em>excellent</em> progress, especially because <strong>for new github.io sites, HTTPS is mandatory</strong>. Existing github.io sites can <a href="https://help.github.com/articles/securing-your-github-pages-site-with-https/">opt-in to server-side HTTPS enforcement</a>.
<br/><br/>
Of course, the work's not done until GitHub Pages supports HTTPS for custom domains. GitHub hosts a huge number of project, personal, and conference sites that use custom domains -- including <a href="http://codeconf.com">GitHub's own CodeConf site</a> -- which all continue to put their users at risk.
<br/><br/>
But this is clearly involved a ton of CDN and infrastructure work by GitHub that will make custom domain HTTPS support easier, and it means that the GitHub Pages team made HTTPS support a priority for its finite engineering time. That deserves plenty of kudos, and bodes well for future work.
<br/><br/>
I've updated some instructions below to reflect GitHub's new options. You can also <a href="https://github.com/isaacs/github/issues/156">follow this long-running GitHub Issues thread</a> for community updates on further developments.
</div>

Recently, GitHub Pages [began supporting HTTPS](https://twitter.com/benbalter/status/444555263195217920) for `*.github.io` domains, like [this one](https://cfpb.github.io/) and [this one](https://sunlightlabs.github.io/congress/). 

In my opinion, this is a huge deal - GitHub Pages is the only major, free, general-purpose web host which also offers a secure channel. Given [how many simple and powerful uses](https://konklone.com/post/the-power-and-potential-of-github-pages) GitHub Pages has, and how vital secure and confidential connections are to the future of the web, I see this as a big step forward for developers, GitHub, and everyday people.

There are two major catches:

* <s>You **can't force HTTPS** for your `*.github.io` site.</s> **Update June 2016:** You can now [enforce HTTPS server-side for `*.github.io` sites](https://help.github.com/articles/securing-your-github-pages-site-with-https/).
* You **can't use a custom domain name** with a fully secured HTTPS connection.

### Enforcing HTTPS for github.io sites

_(This section updated in June 2016 to integrate GitHub's [new HTTPS support for github.io](https://help.github.com/articles/securing-your-github-pages-site-with-https/).)_

First, begin [enforcing HTTPS server-side](https://help.github.com/articles/securing-your-github-pages-site-with-https/).

Second, add or update **[canonical URLs](https://support.google.com/webmasters/answer/139066?hl=en)** to tell search engines to use the HTTPS version of your website.

Specifying a canonical URL looks like this:

```html
<link rel="canonical" href="https://yoursite.github.io" />
```

In Jekyll, this looks like:

```html
<link rel="canonical" href="{{ site.url }}{{ page.url }}" />
```

Where you've set the `url` field in your site's `_config.yml` file. See [here](https://github.com/18F/18f.gsa.gov/blob/b58cbcd66d2535746bfa43d42f670b9b1c105fd3/_config.yml#L26) and [here](https://github.com/18F/18f.gsa.gov/blob/b58cbcd66d2535746bfa43d42f670b9b1c105fd3/_includes/head.html#L27) for an example.

(Thanks to Ylon for [suggesting this](#comment-54c505e769702d16212a0000)!)

And of course, always link to your own site using its `https://` URL. Go through any supporting sites or blog posts or material and update the link. If there are any prominent external links to your site, ask the site owner to update their link to use `https://`.

### Using a custom domain with CloudFlare

[**Update**: Rewrote this section later in 2014, after CloudFlare released their free SSL plan.]

[CloudFlare](https://www.cloudflare.com/) now offers **[free SSL termination](https://blog.cloudflare.com/introducing-universal-ssl/)** for any website they host, under their "Universal SSL" plan. 

However, until GitHub Pages or CloudFlare fix things, you'll only be able to encrypt the connection between the user and CloudFlare. The connection between CloudFlare and GitHub Pages will need to remain in plaintext, using CloudFlare's "Flexible SSL" option. For more information on why this is the case, read [these](https://github.com/isaacs/github/issues/156#issuecomment-57271637) [comments](https://github.com/isaacs/github/issues/156#issuecomment-60453315) that lay out how it works.

If you're okay with traffic flowing in clear text between CloudFlare and GitHub, you can turn on SSL for free in front of your GitHub Pages site with a custom domain.

But **be careful**. This is a tempting, but incomplete solution. I was [very disappointed](https://github.com/MayOneUS/homepage_redesign/issues/82) to see the [MayDay SuperPAC](https://mayday.us) use this configuration to solicit donations. An attacker who could get between CloudFlare and GitHub could have altered the form in transit to send payment information to anywhere they wanted.

More generally problematic is that the browser has no way of indicating to the user that the connection is not fully secure. Right now, people generally expect that if there's a lock symbol in the browser, the connection is secure between them and the website. CloudFlare's Flexible SSL configuration breaks this expectation, and there is no way from the outside to tell whether a website is using it.

<blockquote class="twitter-tweet" lang="en"><p>Gotta say, I agree with <a href="https://twitter.com/__agwa">@__agwa</a> - CloudFlare has good intentions, but their Flexible SSL dilutes the value of HTTPS: <a href="https://t.co/6B3dqMzHgK">https://t.co/6B3dqMzHgK</a></p>— Eric Mill (@konklone) <a href="https://twitter.com/konklone/status/539543267311091715">December 1, 2014</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

I'm not saying to never use CloudFlare's Flexible SSL - but know exactly what you are doing.

### What's next

_(This section updated in June 2016 to reflect GitHub's progress in HTTPS support for Pages.)_

GitHub needs to work on custom domain support for Pages. GitHub hosts a huge number of developer-oriented project, personal, and conference sites that use custom domains -- including <a href="http://codeconf.com">GitHub's own CodeConf site</a>. These not only continue to put their users at risk, they also set a bad example for the overall developer community.

It's a tall order, but this is something that other services in GitHub's position have done. WordPress [recently deployed complete HTTPS support for every WordPress.com-hosted site](https://en.blog.wordpress.com/2016/04/08/https-everywhere-encryption-for-all-wordpress-com-sites/), whether they use a custom domain or not, using free certificates from [Let's Encrypt](https://letsencrypt.org). [Bitly](http://www.eweek.com/security/bitly-embraces-lets-encrypt-for-short-link-security.html) and [Shopify](https://www.shopify.com/blog/73511365-all-shopify-stores-now-use-ssl-encryption-everywhere) have done the same thing, and Dreamhost now [lets any customer easily turn HTTPS on for their domain](https://www.dreamhost.com/blog/2015/12/03/lets-encrypt-and-dreamhost/). The bar is higher now, and GitHub should meet it.

In the meantime, the rest of the us can speed up the transition by switching repos we own that run github.io sites, and filing tickets with others reminding them to switch theirs. I've been [filing](https://github.com/mozilla/mozilla.github.io/issues/8) [tickets](https://github.com/cfpb/cfpb.github.io/issues/97) myself, and I encourage you to do the same!