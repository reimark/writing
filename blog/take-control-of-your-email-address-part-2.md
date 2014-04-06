<h2 id="part-two">Part 2: Connecting Things Together</h2>

Now that you picked up your shiny new domain name and your fancy new Pobox account, we're going to perform some introductions between the two.

We'll start by **telling your domain name about your email**. 

If you're using [iwantmyname](https://iwantmyname.com/), they make this as easy as pushing a couple buttons. Seriously: just [visit their Email apps](https://iwantmyname.com/dashboard/apps/email-hosting/), click on Pobox, click "Add Pobox" next to your domain, then click "Install Pobox" on this screen:

<img src="/assets/images/domains/iwantmyname-install.png" style="display: block" />

And that's it!

If you're **not** using iwantmyname, then you'll need to figure out where your DNS is managed. Not every domain registrar manages DNS, but many popular ones like [Dreamhost](http://dreamhost.com/domains/) and GoDaddy [right [Never](http://www.ibtimes.com/super-bowl-2012-godaddys-naked-lady-scantly-clad-pussycat-ads-irk-viewers-video-405086) [use](http://thetechblock.com/why-you-should-never-use-go-daddy-again/) [GoDaddy](http://www.zdnet.com/blog/networking/wikipedia-is-leaving-go-daddy-because-of-sopa/2108)!] do. If you're pretty sure your domain registrar doesn't manage DNS, you can also buy DNS management a la carte from companies like [DNSimple](https://dnsimple.com/) and point your registrar's "nameservers" in their direction. Or, you can just [transfer your domain to iwantmyname](https://iwantmyname.com/domains/domain-transfer)! They're great, I'm not sure if I've mentioned them yet.

Either way, figure out where your DNS settings are. You're going to add **MX records** to your domain's DNS. These records -- the MX stands for **M**ailbo**X** -- tell servers on the Internet how to deliver mail to you. The location and form's going to be different for everyone. For example, if you use Dreamhost, they have a [special page](https://panel.dreamhost.com/index.cgi?tree=mail.mx) for entering MX records. [right [Email me](mailto:eric@konklone.com) links to manage MX records on other popular hosts (except GoDaddy), and I'll add them here.]

Pobox has a [nice explainer on MX records](http://www.pobox.com/helpspot/index.php?pg=kb.page&id=52), but you don't have to understand how it works. Just obey orders and paste [Pobox's MX records](http://www.pobox.com/helpspot/index.php?pg=kb.page&id=42) into the right fields once you've found them:

> mx-1.rightbox.com
> mx-2.rightbox.com
> mx-3.rightbox.com

Next, we'll go the other direction, and **tell your email about your domain**. 

At the end of Part 1, we were waiting for Pobox to approve your account. Now that it's been approved, you're going to tell Pobox about your domain. Log back into [Pobox's dashboard](https://pobox.com/home), and look to the sidebar:

<img src="/assets/images/domains/pobox-configure-0.png" class="block upper border" />

Click "Domain" to go to a tiny form, where you'll enter in the domain name you own.

<center><img src="/assets/images/domains/pobox-configure-1.png" class="block upper border" /></center>

If you set your MX records correctly (either by using iwantmyname's "Install Pobox" button, or your other registrar's DNS settings), then your domain should be **automatically approved**.

<h2 id="part-three">Part 3: Flipping the Switch</h2>

Now that Pobox has verified and added your domain, you'll see it appear on your [Pobox dashboard]((https://pobox.com/home)):

<img src="/assets/images/domains/pobox-configure-1b.png" class="block upper border" />

Click "Add user" to finally pick your shiny new email address:

<img src="/assets/images/domains/pobox-configure-2.png" class="block upper border" />

And close the deal by pointing it to your current one:

<img src="/assets/images/domains/pobox-configure-3.png" class="block upper border" />

You are finally done! Go ahead and send yourself a test email — ideally from an unrelated address, like a work account. If it works, then look at you: **you own your email address**.

<h2 id="using-new-address">Using Your New Address</h2>

Your new address will only matter if it actually gets used in place of your old one. You can certainly email blast everyone you know and tell them to use your new address, but there are quieter ways.

**1. Send email "as" your new address.** Gmail's Settings screen has an Accounts tab that lets you add any email address you own, and make it your default "From" address. Click "Add another email address you own":

<img src="/assets/images/domains/gmail-new-email-1.png" class="block upper border" />

Then enter your new email address in the popup window, and click "Next Step".

<img src="/assets/images/domains/gmail-new-email-2.png" class="block upper border" />

Google will send you a verification link. After you click it, go back to the Accounts settings and click "make default" next to your new email address. This will send emails "as" your new address, and when people reply to you, they'll automatically send it to that new address. This will work your new address into other people's contacts, and over time people should begin to always email your new address.

(You can do similar things with your [Microsoft](http://windows.microsoft.com/en-US/windows/outlook/other-email-accounts) and [Yahoo!](http://help.yahoo.com/kb/index?locale=en_US&y=PROD_ACCT&page=content&id=SLN2058) emails. Any other decent email provider should offer you the same option.)

**2. See how it's going.** To test whether that strategy will actually work, I first set up a filter for `to:eric@konklone.com` that auto-labels incoming email as `eric@` and colors them an attractive blue. This gives me a sense, at a glance, of how well my email address transition is going:

<img src="/assets/images/domains/email-label.png" class="block upper border" />

Once the majority of your emails are getting labeled like that, you can reverse the filter so that emails to your **old** address get labeled instead. That way, you can quickly spot outliers and update your information wherever necessary.

**3. Gradually update your online accounts.** It may be obvious, but don't stress out about updating all of your online accounts. It's impossible to remember all of them, and impractical to go update them all at once. It's much easier to make it a habit to go change your email address whenever you end up on a site you have an account with. You'll naturally get the most important ones changed quickly.

**4. (iOS only) Set it up on your phone.** If you use Gmail and an iPhone or iPad, and you use the default Mail app, you can configure it to use your own domain name. Phil Montero at The Anywhere Office has [a video walkthrough](http://www.youtube.com/watch?feature=player_embedded&v=0qx_UfsronA) of the process, and a [larger article](http://www.theanywhereoffice.com/digital-lifestyle/how-to-send-mail-from-your-own-domain-using-gmail-and-iphone.htm) that describes it along with some other things.

<p style="text-align: center"><iframe class="youtube" src="https://www.youtube.com/embed/0qx_UfsronA" frameborder="0" allowfullscreen></iframe></p>

Thanks to Clayton, who wrote in asking about iPhone support, tried out Phil's video, and has this to share for anyone using it:

> My experience:  You might receive a few error messages at first (when sending test emails), even as the emails are being sent from your iPhone.  For example, your iPhone might tell you that the username or password is incorrect, even as it proceeds to send the emails.  Just give it a few minutes -- everything seems to connect after a while and the error messages stop.

<h2 id="and-hey">And Hey</h2>

It's pretty cool that you really went through and did all of this stuff! I hope you found it worthwhile, maybe even a little eye-opening. You didn't have to be a company or get licensed or anything, and you made a working email address on 100% your own terms.

As you encounter services and companies on the Internet, consider whether they will make you more or less powerful. It's not always an easy question. Companies like [iwantmyname](https://iwantmyname.com/) and [Pobox](http://pobox.com/) are designed to give you more power: they free you from long term dependency, and they're easy to leave. Not coincidentally, they cost money. But their real market challenge is subtler and dangerous: they require you to learn a couple of concepts about the Internet.

The goal of many other successful Internet companies is to convince you not to bother with all that learning, so that they can be a part of your identity and extract as much value from your daily life as possible. Free services like Twitter and Google offer lots of benefits, and certain kinds of power. But I think we've all felt that uncomfortable gut sensation we get when we see a bad news headline, or a canned product, or really anything that reminds us how much we depend on these free, smiling behemoths and how little control we have over them.

Getting a domain name and sticking it in your email is just a small step towards online independence. There's a lot more you can do. But it is a real step, and you've taken it.