The Internet's [not in a great place](http://www.guardian.co.uk/world/the-nsa-files), and neither are we. We've learned to depend more on fewer companies, and so we've given up much of the control the Internet was designed to give us. We're easy pickings.

So how do we turn this ship around? As a start, I recently switched my public email address from `konklone@gmail.com` to [eric@konklone.com](mailto:eric@konklone.com). 

Because it uses my name instead of Google's, I have an email address to last me my whole life. It turns out this is actually <strong>cheap and easy to do</strong>. You don't have to do anything technical or give up any convenience. In fact, I still send and receive all my email through Gmail. But if I ever want to leave Google, it's going to be a *hell* of a lot easier.

There are lots of ways to pull this off, but the simplest way is to set up **email forwarding**. Now, emails sent to [eric@konklone.com](mailto:eric@konklone.com) get instantly →'d right on to `konklone@gmail.com`. Emails I send are addressed as [eric@konklone.com](mailto:eric@konklone.com). There's no hassle.

I'm going to take you through setting this up for yourself:

* [Buying a domain name](#buying-a-domain-name), and [creating a forwarding account](#setting-up-email-forwarding). (*15 minutes*)
* [Connecting](#connecting-things-together) that domain and that account together. (*15 minutes*)
* [Flipping the switch](#flipping-the-switch), and [easing the transition](#using-your-new-email-address). (*oh, hey: 15 minutes*)

When you're done, you'll have something in short supply on the Internet these days: a measure of control.

## So why bother?

*"Email forwarding?",* you might say, *"This is trivial stuff. You're not throwing off the corporate yoke of Google at all! And the NSA can still grab everything!"*

Well, you're right. This is only the first step. But even if you only take this one step, putting your own domain out in front of the world **profoundly** shifts your relationship with the Internet — and the companies who are increasingly running it — in your favor. 

To see what I mean, think about your cell phone. When you get fed up with AT&T and decide to switch, you expect to keep your cell phone number. We generally take this for granted, but in the US this is a right guaranteed by [government regulations](http://www.fcc.gov/guides/portability-keeping-your-phone-number-when-changing-service-providers "FCC: Keeping Your Telephone Number When You Change Service Provider") mandating portability. 

And you can imagine why: if switching meant a new phone number, changing carriers would be such a tremendous hassle that many people would simply never switch. The US telecom market is terrible enough — cell phone portability is one of the few levers consumers have to avoid lock-in and force carriers to actually compete for their business.

As much goodwill as Gmail has among its users, the marketplace of email providers is not a competitive one. A mere 3 companies — Microsoft, Google, and Yahoo — dominate the market [the world over](http://www.escapistmagazine.com/news/view/120534-You-Probably-Use-Gmail-Now "You Probably Use Gmail Now"). If you want to switch between them, or move to a smaller company like [FastMail](https://www.fastmail.fm/ "FastMail") or [Pobox](https://pobox.com/), you have no guarantees of keeping your provider-assigned email address. In fact, you have the opposite guarantee: **portability is literally impossible** when your address is sporting a company's domain name.

The answer is to use your own. It's simple, inexpensive, and requires no technical skills. Once it's done, you're trusting a company with your email because they do a good job, not because you're stuck there.

So let's take control.

## Buying a Domain Name

If you already own a domain, [skip ahead](#setting-up-forwarding). 

If you don't, good news! It takes all of **about 5 minutes**. We're going to use [iwantmyname](https://iwantmyname.com/), a pleasant, pro-consumer company that [wants you to own things](https://iwantmyname.com/about "Seriously.").  Their site is clean and well designed, and doesn't get in your way. 

Their domains are also reasonably priced, at $15 for the most common types (.com, .net., and .org). This is more expensive than some, [right Like GoDaddy. But [never](http://www.ibtimes.com/super-bowl-2012-godaddys-naked-lady-scantly-clad-pussycat-ads-irk-viewers-video-405086 "Never!") [use](http://thetechblock.com/why-you-should-never-use-go-daddy-again/ "Use!") [GoDaddy](http://www.zdnet.com/blog/networking/wikipedia-is-leaving-go-daddy-because-of-sopa/2108 "GoDaddy!").] but as we'll see, iwantmyname also provides other domain name services that will make email forwarding easy.

<div class="callout">
<strong>What kind of domain should I buy?</strong><br/><br/>
You can buy anything iwantmyname sells, but when in doubt, just buy a <code>.com</code>. They're cheap, and everyone recognizes them. You can also get a <code>.org</code>, but that can imply you're a non-profit or public interest <strong>org</strong>anization.
</div>

To begin, type in the domain you want [into their box of freedom](https://iwantmyname.com/):

<img src="/assets/images/domains/iwantmyname-register.png" class="block upper border" />

You'll see a list of search results. If you're lucky, the domain you want will be happily available:

<img src="/assets/images/domains/iwantmyname-available.png" class="block upper border" />

Click on it to add it to your cart, then click the "Checkout" button on the right. You'll be asked to sign up for an account, enter some basic contact information, and then to, you know, pay them. 

And then, you're done! You'll see this:

<img src="/assets/images/domains/iwantmyname-account-1.png" class="block upper border" />

That's it, you've got a domain name. It's your own little chunk of the Internet, and you can use it with whatever and whoever you want. You don't even have to stick with iwantmyname - you have the right to transfer your domain to another registrar any time you want. The Internet is designed so anyone can be in the driver's seat.

## Setting up email forwarding

Now that you have a domain, we'll set up an account with an email forwarding service, and then "point" your domain at that service.

There are many services out there that offer email forwarding, but I have been especially impressed with [Pobox](http://pobox.com "Pobox Lifetime Email"). They've been around since 1995, and they care about this stuff.:

> Your email address, your identity, is how you keep in touch, what you use to access many websites... indeed, it's how you're known. Email forwarding lets you easily change where you read your mail, without getting a new address.
> <cite>[Pobox FAQ](http://pobox.com/faq#fwd)</cite>

Because they care, they offer two very reasonable [pricing tiers](http://pobox.com/pricing) especially designed for people who only want email forwarding. They'll forward 1,000 messages a day for <strong>$20</strong>/year ($2/month), and if you're worried that might not be enough, bump it up to 2,000 messages a day for all of <strong>$35</strong>/year ($3/month). Unless you're on a truly insane number of mailing lists, either of these plans will cover you easy.

<div class="callout">
<strong>Peace of mind</strong>: If you use Gmail and are curious how many emails you actually get in a day, try a few searches like this and page through the results:
<br/><br/>
<code>in:anywhere after:2013/6/19 before:2013/6/20</code>.
<br/><br/>
You can also check your <a href="https://www.google.com/settings/activity">Google Account Activity report</a> for email statistics.
</div>

Start by [signing up for a new account](https://pobox.com/signup). When you're asked to choose a username, just leave the domain as `pobox.com`. You're not actually going to use this email address for either forwarding or receiving email, it's just to get a unique username with Pobox. You'll tell Pobox about your new domain name later. 

<img src="/assets/images/domains/pobox-signup-1.png" class="block upper border" />

A little further down the form, you'll tell Pobox the email address you'll be forwarding mail to (your current email address, e.g. Gmail or Yahoo):

<img src="/assets/images/domains/pobox-signup-2.png" class="block upper border" />

After you've signed up, Pobox will send you a verification email. Click on the verification link in your email to see this:

<img src="/assets/images/domains/pobox-done-2.png" class="block upper border" />

Unfortunately, now you really do just have to wait for Pobox to approve your account. It can take something like a day. When it's done, they'll email you. Until then, bookmark <a href="#connecting-things-together">the next section</a>.

## Connecting Things Together

Now that you picked up your shiny new domain name and your fancy new Pobox account, we're going to perform some introductions between the two.

We'll start by **telling your domain name about your email**. 

If you're using [iwantmyname](https://iwantmyname.com/), they make this as easy as pushing a couple buttons. Seriously: just [visit their Email apps](https://iwantmyname.com/dashboard/apps/email-hosting/), click on Pobox, click "Add Pobox" next to your domain, then click "Install Pobox" on this screen:

<img src="/assets/images/domains/iwantmyname-install.png" style="display: block" />

And that's it!

If you're **not** using iwantmyname, then you'll need to log in to your registrar and find their DNS settings. You're going to add **MX records** to your domain's DNS. These records -- the MX stands for **M**ailbo**X** -- tell servers on the Internet how to deliver mail to you.

If you're using:

* **Dreamhost**, they have a [wiki page explaining MX records](http://wiki.dreamhost.com/MX_record#Changing_MX_records_for_your_Dreamhost-hosted_domain), which they configure at a [special page](https://panel.dreamhost.com/index.cgi?tree=mail.mx) in their control panel.
* **GoDaddy**, well for one: [Never](http://www.ibtimes.com/super-bowl-2012-godaddys-naked-lady-scantly-clad-pussycat-ads-irk-viewers-video-405086) [use](http://thetechblock.com/why-you-should-never-use-go-daddy-again/) [GoDaddy](http://www.zdnet.com/blog/networking/wikipedia-is-leaving-go-daddy-because-of-sopa/2108)! But if you *do* regrettably use GoDaddy, use [this brief guide to setting MX records inside GoDaddy's confusing control panel](https://github.com/our/email/tree/master/godaddy#setting-up-email-forwarding-in-godaddy). Thanks to [Ben Chartoff](https://twitter.com/benchartoff).
* **Namecheap**, use these [instructions for adding MX records](https://github.com/our/email/tree/master/namecheap#setting-up-email-forwarding-in-namecheap) in their control panel. Thanks to [Michael Weinberg](https://twitter.com/mweinbergPK).
* **Someone else**, you'll just have to poke around, but it's usually not difficult.

Pobox has a [nice explainer on MX records](http://www.pobox.com/helpspot/index.php?pg=kb.page&id=52), but you don't have to understand how it works. Just obey orders and paste [Pobox's MX records](http://www.pobox.com/helpspot/index.php?pg=kb.page&id=42) into the right fields once you've found them:

> mx-1.rightbox.com<br/>
> mx-2.rightbox.com<br/>
> mx-3.rightbox.com

If you get asked for a priority, use `10`. If you get asked for a name or subdomain, use `@`.

Next, we'll go the other direction, and **tell your email about your domain**. 

At the end of Part 1, we were waiting for Pobox to approve your account. Now that it's been approved, you're going to tell Pobox about your domain. Log back into [Pobox's dashboard](https://pobox.com/home), and look to the sidebar:

<img src="/assets/images/domains/pobox-configure-0.png" class="block upper border" />

Click "Domain" to go to a tiny form, where you'll enter in the domain name you own.

<img src="/assets/images/domains/pobox-domain-checking.png" class="block upper border" />

Pobox will check the domain, then ask you whether you own it (say "Yes"), and whether you're already using it for email (say "No" or "Only a website"). Then hit "Add Domain". 

<img src="/assets/images/domains/pobox-domain-ownership.png" class="block upper border" />

If you set your MX records correctly (either by using iwantmyname's "Install Pobox" button, or your other registrar's DNS settings), then your domain should be **automatically approved**.

## Flipping the Switch

Now that Pobox has verified and added your domain, you'll see it appear on your [Pobox dashboard]((https://pobox.com/home)):

<img src="/assets/images/domains/pobox-configure-1b.png" class="block upper border" />

Click "Add user" to finally pick your shiny new email address:

<img src="/assets/images/domains/pobox-configure-2.png" class="block upper border" />

And close the deal by pointing it to your current one:

<img src="/assets/images/domains/pobox-configure-3.png" class="block upper border" />

You are finally done! Go ahead and send yourself a test email — ideally from an unrelated address, like a work account. If it works, then look at you: **you own your email address**.

## Using Your New Address

Your new address will only matter if it actually gets used in place of your old one. You can certainly email blast everyone you know and tell them to use your new address, but there are quieter ways.

**1. Send email "as" your new address.** Gmail's Settings screen has an Accounts tab that lets you add any email address you own, and make it your default "From" address. Click "Add another email address you own":

<img src="/assets/images/domains/gmail-new-email-1.png" class="block upper border" />

Then enter your new email address in the popup window, and click "Next Step".

<img src="/assets/images/domains/gmail-new-email-2.png" class="block upper border" />

Next, Google will ask you which servers should send your email. You can leave it as "Send through Gmail" if you want — but if you do that, many mail clients will show both of your email addresses to people. So, I recommend choosing "Send through [your domain's] SMTP servers" instead, and filling it out like so:

<img src="/assets/images/domains/gmail-new-email-3.png" class="block upper border" />

That's an SMTP server address of `smtp.pobox.com`, a username of `[username]@pobox.com` (where `[username]` is the username your Pobox account is tied to), and your Pobox password. Choose port 587, and a "secured connection using TLS".

**Note**: If you ever set up [two factor authentication for Pobox](https://www.pobox.com/profile/otp) (and [you should](https://konklone.com/post/protect-your-domain-name-with-two-factor-authentication)), you will need to [create an app-specific password](https://www.pobox.com/profile/apptoken) and give that to Gmail, instead of your normal Pobox password.

Finally, Google will send you an email with a verification link. After you click it, go back to the Accounts settings and click "make default" next to your new email address. This will send emails "as" your new address, and when people reply to you, they'll automatically send it to that new address. This will work your new address into other people's contacts, and over time people should begin to always email your new address.

(You can do similar things with your [Microsoft](http://windows.microsoft.com/en-US/windows/outlook/other-email-accounts) and [Yahoo!](http://help.yahoo.com/kb/index?locale=en_US&y=PROD_ACCT&page=content&id=SLN2058) emails. Any other decent email provider should offer you the same option.)

**2. Add it to your entire Google Account as an "associated email address".** Visit your [Google Account information settings page](https://accounts.google.com/b/0/EditUserInfo?hl=en) to tell the rest of Google's properties about your new email address. This lets you do things like accept Google Group invites at your new email address.

<img src="/assets/images/domains/google-associated-email.png" class="block upper border" />

Once you've done this, you can also update your Google Calendar settings to let you accept invitations sent to your new email address. To do this, go to the Settings area, to the Calendar tab, and look for your primary calendar (probably the topmost one). Click "Reminders and Notifications".

<img src="/assets/images/domains/calendar-settings.png" class="block upper border" />

At the bottom of the page, you should see a checkbox that lists your alternate email, and allows you to receive invites at that address. Check the box, and hit the Save button below it.

<img src="/assets/images/domains/calendar-settings-2.png" class="block upper border" />

**3. See how it's going.** To test whether that strategy will actually work, I first set up a filter for `to:eric@konklone.com` that auto-labels incoming email as `eric@` and colors them an attractive blue. This gives me a sense, at a glance, of how well my email address transition is going:

<img src="/assets/images/domains/email-label.png" class="block upper border" />

Once the majority of your emails are getting labeled like that, you can reverse the filter so that emails to your **old** address get labeled instead. That way, you can quickly spot outliers and update your information wherever necessary.

**4. Gradually update your online accounts.** It may be obvious, but don't stress out about updating all of your online accounts. It's impossible to remember all of them, and impractical to go update them all at once. It's much easier to make it a habit to go change your email address whenever you end up on a site you have an account with. You'll naturally get the most important ones changed quickly.

**5. (iOS only) Set it up on your phone.** If you use Gmail and an iPhone or iPad, and you use the default Mail app, you can configure it to use your own domain name. Phil Montero at The Anywhere Office has [a video walkthrough](http://www.youtube.com/watch?feature=player_embedded&v=0qx_UfsronA) of the process, and a [larger article](http://www.theanywhereoffice.com/digital-lifestyle/how-to-send-mail-from-your-own-domain-using-gmail-and-iphone.htm) that describes it along with some other things.

<p style="text-align: center"><iframe class="youtube" src="https://www.youtube.com/embed/0qx_UfsronA" frameborder="0" allowfullscreen></iframe></p>

Thanks to Clayton, who wrote in asking about iPhone support, tried out Phil's video, and has this to share for anyone using it:

> My experience:  You might receive a few error messages at first (when sending test emails), even as the emails are being sent from your iPhone.  For example, your iPhone might tell you that the username or password is incorrect, even as it proceeds to send the emails.  Just give it a few minutes -- everything seems to connect after a while and the error messages stop.

If you use iCloud, check out [these instructions for updating your iCloud email](https://github.com/our/email/tree/master/icloud#update-your-email-address-in-apple-and-icloud). Thanks to [@pessimism](https://twitter.com/pessimism) for writing and donating them!

**6. Ignore Pobox spam emails when they don't catch anything.** Pobox emails you regular reports of spam messages, but annoyingly, they still do this even when they don't catch anything. To suppress these, add a filter for `from:pobox subject:"we caught 0 messages for you"` and have them archived or deleted.

## And Hey

It's pretty cool that you really went through and did all of this stuff! I hope you found it worthwhile, maybe even a little eye-opening. You didn't have to be a company or get licensed or anything, and you made a working email address on 100% your own terms.

As you encounter services and companies on the Internet, consider whether they will make you more or less powerful. It's not always an easy question. Companies like [iwantmyname](https://iwantmyname.com/) and [Pobox](http://pobox.com/) are designed to give you more power: they free you from long term dependency, and they're easy to leave. Not coincidentally, they cost money. But their real market challenge is subtler and dangerous: they require you to learn a couple of concepts about the Internet.

The goal of many other successful Internet companies is to convince you not to bother with all that learning, so that they can be a part of your identity and extract as much value from your daily life as possible. Free services like Twitter and Google offer lots of benefits, and certain kinds of power. But I think we've all felt that uncomfortable gut sensation we get when we see a bad news headline, or a canned product, or really anything that reminds us how much we depend on these free, smiling behemoths and how little control we have over them.

Getting a domain name and sticking it in your email is just a small step towards online independence. There's a lot more you can do. But it is a real step, and you've taken it.