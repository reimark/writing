<!-- <img src="https://konklone.com/assets/images/github-world.png" /> -->

In recent days, my usage of [Github Pages](http://pages.github.com/) has **drastically** increased. It's an incredibly useful way to get things online for free, and since it's part of a developer-friendly platform, you can repurpose it for all sorts of things.

I think I've stretched GitHub Pages pretty far, and so I thought it'd be helpful to describe the different ways I've found it valuable in my personal and professional work.


1. **Publishing a dynamic, nice-looking document.** At [unitedstates/licensing](https://github.com/unitedstates/licensing), we're using GitHub Pages to host a [best practices document for government licensing](http://theunitedstates.io/licensing/), and I think it came out looking pretty great. Using Jekyll, we can update our document by editing a [single Markdown file](https://github.com/unitedstates/licensing/blob/gh-pages/index.md). This was inspired by the White House's use of GitHub and Jekyll for [Project Open Data](http://project-open-data.github.io/) — and like them, it gives us a great reason to [collaborate out in the open](https://github.com/unitedstates/licensing/pull/1) using GitHub's excellent pull request and issue system.

2. **Quickly getting files online.** At [konklone/ny-elections](https://github.com/konklone/ny-elections), I'm holding the Excel files of election result data that New York State gave me in response to a [Freedom of Information request](https://gist.github.com/konklone/6884484). I don't expect anyone to visit the repository; I just needed to be able to link to them somewhere, to support [a piece I wrote for the Open Elections project](http://blog.openelections.net/2013/10/18/new-york-i-love-you-but-your-data-is-hard) on the process of getting this data and how much was missing. Tossing them into a new repository's `gh-pages` branch is about as simple as using Amazon S3, with the added benefit that it's free.

3. **Giving a simple home to a working community.** At [unitedstates/unitedstates.github.io](https://github.com/unitedstates/unitedstates.github.io), we have a bit of HTML that makes up the tiny landing page at [theunitedstates.io](http://theunitedstates.io), which is used as the home for [an open data collaboration](http://sunlightfoundation.com/blog/2013/08/20/a-modern-approach-to-open-data/). It's still super rudimentary, but after a year of just pointing people to [github.com/unitedstates](https://github.com/unitedstates), we wanted something just a little more memorable and friendly to the layperson. By using the custom domain for the whole organization, pages for projects automatically use it, like [/licensing](http://theunitedstates.io/licensing).

4. **Creating a simple data hub.** At [isitchristmas/data](https://github.com/isitchristmas/data), I've published a mix of CSVs and PDFs with data from running [isitchristmas.com](https://isitchristmas.com) in years past. By putting the CSVs on a `gh-pages` branch, I get two benefits at once: linking to a lean, clean [in-browser presentation](https://github.com/isitchristmas/data/blob/gh-pages/2012/countries.csv) of the CSV, and a [direct download link](http://isitchristmas.io/data/2012/browsers.csv).

5. **Creating a sophisticated data hub.** At [unitedstates/glossary](https://github.com/unitedstates/glossary), I've built a working prototype of a glossary where the definitions are [edited in prose form](http://prose.io/#unitedstates/glossary/edit/master/definitions/congress/Cloture) and automatically [published as data](http://theunitedstates.io/glossary/definitions/congress/Cloture.json). Any time a definition in the master branch is updated, a corresponding JSON file in the GitHub Pages branch is immediately updated. This works by using GitHub's [Post-Receive Hooks](https://help.github.com/articles/post-receive-hooks) to hit a Heroku app, [whose code](https://github.com/unitedstates/glossary/tree/dat#glossary-transformation) is on a third branch called `dat`. This app watches for changes, does the transform, and commits the results back to GitHub Pages using the recently announced [CRUD support](https://github.com/blog/1498-file-crud-and-repository-statistics-now-available-in-the-api) in their [Contents API](http://developer.github.com/v3/repos/contents/). That same Contents API allows anyone who wants to use the resulting data to easily integrate it, like we have in Scout (see "cloture" [in this speech](https://scout.sunlightfoundation.com/item/speech/CREC-2013-12-10-pt1-PgS8581-5.chunk3/sen-harry-reid-workforce-investment-act-of-2013--motion-to-proceed)).

6. And finally, **its original purpose: project documentation**. At [sunlightlabs/congress](https://github.com/sunlightlabs/congress/tree/gh-pages), I keep the documentation for [Sunlight's Congress API](http://sunlightlabs.github.io/congress/). Originally, we generated our documentation using [DocumentUp](http://documentup.com/), which meant freezing the .html files into GitHub, and remembering to run a compiling script before every push. I recently [reworked the docs to use Jekyll](https://github.com/sunlightlabs/congress/pull/425), so now I can just push changes to Markdown files, and our docs are automatically published in the same crisp layout.


Clearly, GitHub Pages is my erstwhile companion, for technical projects and for collaborative authoring. But GitHub Pages could definitely be made better.

## A Friendlier Editor

GitHub's [built-in editor](https://github.com/blog/905-edit-like-an-ace) might have been okay in 2011, but nowadays it feels pretty bad, especially for prose. Recognizing that, a lot of projects make use of [prose.io](http://prose.io/#konklone/fisa/edit/master/README.md), which does a fine job when it works.

But prose.io has been [suffering](https://github.com/prose/prose/pull/614) from [bugs](https://github.com/prose/prose/issues/643) that make it not work, and standing up your own copy means also standing up an intermediary app called [gatekeeper](https://github.com/prose/gatekeeper) to proxy OAuth requests to GitHub. Prose.io is also missing really fundamental features for people not used to Markdown editing, like live preview.

So right now, it's tough to provide the general public a link to a reliable, simple editor for content hosted on GitHub -- especially for prose hosted on GitHub Pages.

## Standardizing Markdown

GitHub's made Markdown the de facto writing format for geeks, but the Markdown ecology is chaotic and inconsistent.

I published the documentation for [Sunlight's Congress API](http://sunlightlabs.github.io/congress/) using GitHub Pages, and recently migrated it to use Jekyll. It turned out that I [couldn't have everything I wanted](https://github.com/jekyll/jekyll/pull/1558#issuecomment-29853283), and so I eventually had to [make a bunch of ugly tradeoffs](https://github.com/sunlightlabs/congress/pull/425) to finally make our API documentation a bunch of Markdown files that get templated on the fly.

GitHub seems to be trying to bring order by banking on [redcarpet](https://github.com/vmg/redcarpet), but redcarpet is primarily written in C, and so even though I'd prefer to fill in redcarpet's gaps myself, I [couldn't meaningfully contribute](https://github.com/vmg/redcarpet/issues/330).

I think it's fair to say that as a user of Markdown, the situation is confusing. The community has long since moved beyond [Gruber's original spec](http://daringfireball.net/projects/markdown/syntax), but everything beyond that spec is splintered, and shows no signs of un-splintering. It's good to have competing Markdown parsers, but **it's time to expand the Markdown standard** so that the features that have emerged as widely desired become present and consistent across those parsers.


## Support HTTPS

GitHub uses HTTPS everywhere on github.com, and in general is an extremely security-conscious company, but GitHub Pages doesn't support encryption at all.

As GitHub Pages grows as a hosting platform, this is only going to become more important. In a time when every aspect of our browsing activity is subject to bulk collection and analysis for suspicious behavior, the world's other major tech companies are moving to [encrypt everything](http://www.pcworld.com/article/2065479/encrypt-everything-googles-answer-to-government-surveillance-is-catching-on.html) they possibly can, and [HTTP 2.0 will require encryption](http://lists.w3.org/Archives/Public/ietf-http-wg/2013OctDec/0625.html). GitHub should figure this out.

There are two different kinds of situations here. The simplest case, where the site uses GitHub's provided `*.github.io` domain, GitHub can provide their own wild-card certificate, and pay their CDN to provide SSL support. This would be a terrific start.

For the harder case, where the site is using a custom domain, the owner needs a way to give GitHub their private key and certificate, on a per-project basis. This would be a complicated feature for GitHub to add, but potentially worthwhile. Alternatively, the owner can put a third party service like [CloudFlare](https://www.cloudflare.com/) in front of it for a fee ($20/month per site right now). GitHub could point people in the direction of services like that, or even create a partnership with one of them where people can turn it on from inside GitHub, without having to go register and manage a separate account.

## GitHub as Automatic Publisher

Automatically syncing data with GitHub Pages, like we did with [our glossary](https://github.com/unitedstates/glossary), feels like a Useful Thing, and there's more I'd like to do with it.

For example, we keep data on members of Congress at [unitedstates/congress-legislators](https://github.com/unitedstates/congress-legislators) in YAML. We use YAML as the canonical, versioned format for a variety of reasons — ease of editability for beginners and [readability of diffs](https://github.com/unitedstates/congress-legislators/pull/155/files) among them. But YAML isn't widely used, and we'd like to offer CSV and JSON downloads of the data — without having to remember to run a transform script before every commit.

Right now, we'd have to do that by setting up another app on Heroku solely to do that work. Developing and maintaining a suite of Heroku apps isn't super fun, and feels like a disproportionate amount of work for running a small amount of transform code after each push. This is theoretically Jekyll's role, but vanilla Jekyll is optimized for basic content publishing, and GitHub Pages doesn't support plugins. Even if GitHub Pages one day did support Jekyll plugins, which have to be written in Ruby, that's not totally ideal either — our project is in Python, and doing anything context-specific will mean re-implementing a bunch of project-wide logic and utilities in Ruby.

I believe there's an opportunity here for GitHub Pages. Maybe it's offering some simple sandboxed code execution as a post-push hook, without needing to host something at an external URL. Maybe it's extending Jekyll somehow. Maybe it's a service like [Travis](https://travis-ci.org/), but designed expressly for potentially destructive code execution. Whatever it is -- automatic public URLs whose contents are programmatically relevant to the **substance** of your project is a powerful idea, and right now GitHub Pages is optimized only for documenting it.


## Simple Publishing of Any File

A small thing, with consequences: though you can create, read, update, and delete (CRUD) text-based files through the GitHub web interface, it's not possible to upload binary files that way. So, if you want to include an image on your website, you have to take it to the terminal, or a native application.

If I were running a workshop on Publishing My First Website, I'd absolutely choose GitHub Pages. You can point and click your way to expressing yourself on the public Internet, without having to deal with the overhead of a system designed for blogging. Registrars like [iwantmyname](https://iwantmyname.com/), that are not only user-friendly but provide point-and-click [Github Pages integration](https://iwantmyname.com/services/developer/github-pages-custom-domain), make it possible for that workshop to let people leave with their own URL and content, all from within the web browser.

But the simple act of including an image or PDF would complicate that workshop. Yes, you can use other file-hosting services, but that's more for people to learn and manage. This is a barrier to GitHub Pages' accessibility to people new to the web and technology.


## Everyone is Here in The Future

If it's not obvious, I think GitHub Pages' potential is huge. It fills a role that Amazon S3, Tumblr, and Wordpress do not, and its inherent programmability gives it potential that no one else can have. It has a better balance of simplicity, power, collaboration, and price than any of its competitors.

But my sense is that it's not seen that way yet by the larger Internet. GitHub's core audience has (and may always be) developers and tech-minded folks, but GitHub Pages is an approach to web publishing with much broader value. In time, I hope it earns a broader appeal.