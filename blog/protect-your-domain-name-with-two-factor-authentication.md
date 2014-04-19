<a href="http://halfelf.org/2013/two-factor-authentication/">
<img src="/assets/images/blog/two-factor-auth.png" class="border block" />
</a>

<span style="font-size: 80%">*Jump below for [links to domain providers who offer two factor authentication](#providers-who-offer-2fa).*</span>

Naoki Hiroshima's "[How I lost my $50,000 Twitter username](http://thenextweb.com/socialmedia/2014/01/29/lost-50000-twitter-username/)" is a fascinating, terrifying description of how Hiroshima had his Twitter handle, `@n` (now [@n_is_stolen](https://twitter.com/n_is_stolen)) stolen by an attacker. The mundane, articulate emails from the attacker are particularly chilling to me.

The attacker also uses a method that, though very simple, I haven't heard of before. The attacker compromised Hiroshima's GoDaddy account and got control of his domain name, and then used this to take control of Hiroshima's email address that used it. The attacker didn't need to compromise Hiroshima's email **service provider** (Google Apps) -- just his email address' **domain provider** (GoDaddy).

Hiroshima describes in great detail the spiral of terrible corporate security, social engineerng, and customer service that allowed the attack to succeed from that point onwards. His account reveals many different problems -- including some services using credit card numbers to verify identity -- and it's put a number of companies' security policies into the spotlight.

## Gmail Addresses Aren't the Answer

Unfortunately, Hiroshima then comes to a mistaken conclusion. In a section titled "Avoid Custom Domains for Your Login Email Address", Hiroshima cautions against registering for services with emails using your own domain:

> I changed the email address I use at several web services to an @gmail.com address. Using my Google Apps email address with a custom domain feels nice but it has a chance of being stolen if the domain server is compromised. If I were using an @gmail.com email address for my Facebook login, the attacker would not have been able to access my Facebook account.

The only reason that a @gmail.com address would have been more secure for Hiroshima is that he would have Google's [two factor authentication](http://en.wikipedia.org/wiki/Two-step_verification) (2FA) enabled. 2FA requires an attacker to not only know your password, but also have access to something you own (typically your phone). Hiroshima does acknowledge 2FA's importance:

> Using two-factor authentication is a must. It’s probably what prevented the attacker from logging into my PayPal account. Though this situation illustrates that even two-factor authentication doesn’t help for everything.

But of course, 2FA *can* help you protect your domain -- but only if your **domain provider offers it, and you use it**. That's the real lesson here. 

Using your own domain for email is a hugely important way to [take control of your identity](https://konklone.com/post/take-control-of-your-email-address) online. This is a good reminder that when you do that, you need to choose a domain provider whose security you trust.

In fact, it it looks like GoDaddy actually [does provide 2FA](http://support.godaddy.com/help/article/7502/enabling-twostep-authentication) (not that I would *ever* recommend using GoDaddy). Even if Hiroshima didn't turn it on, I don't blame him! My domain provider, [iwantmyname](https://iwantmyname.com/), [also provides 2FA](http://help.iwantmyname.com/customer/portal/articles/1139898-how-can-i-enable-two-factor-authentication-), but I hadn't thought of enabling it until reading Hiroshima's account. I witnessed a number of friends [make](https://twitter.com/jaquith/status/428595474057424896) the [same](https://twitter.com/npdoty/status/428616183894388736) [decision](https://twitter.com/btj/status/428592436840251392).

While I'm sorry that this event happened to him, I'm extremely glad he wrote it up like this. Our domain providers have the responsibility to provide **at least** the same level of security we get from our social networks, and we're responsible for taking advantage of that security when it exists.

## Providers who offer 2FA

**Update**: I'd like the below list to remain timely and useful, but [Twofactorauth.org](http://twofactorauth.org/) is probably going to be a more comprehensive, up-to-date resource - they take contributions [via GitHub](https://github.com/jdavis/twofactorauth).

Here's how to set up two factor authentication on your domain's registrar or DNS provider.

* [iwantmyname](http://help.iwantmyname.com/customer/portal/articles/1139898-how-can-i-enable-two-factor-authentication-) (recommended!)
* [Namecheap](https://www.namecheap.com/support/knowledgebase/article.aspx/9253/45/how-to-two-factor-authentication)
* [DNSimple](http://blog.dnsimple.com/2012/08/protect-your-dnsimple-account-with-two-factor-authentication-from-authy/)
* [DNS Made Easy](http://www.dnsmadeeasy.com/press-release/dns-made-easy-adds-two-factor-authentication-with-time-based-passwords/)
* [Gandi](http://wiki.gandi.net/en/contacts/login/2-factor-activation)
* [Dreamhost](http://wiki.dreamhost.com/Enabling_Multifactor_Authentication)
* [Hover](http://www.hover.com/blog/two-step-signin-is-here/)
* [Pobox](http://www.pobox.com/helpspot/index.php?pg=kb.page&id=360)
* [Directnic](https://directnic.com/knowledge/article/137:how+do+i+set+up+two-factor+authentication%3F)
* [GoDaddy](http://support.godaddy.com/help/article/7502/enabling-twostep-authentication) (but still, don't use GoDaddy)
* [NameSilo](http://www.namesilo.com/Support/2~Factor-Authentication)

## Providers who DON'T offer 2FA

And here are some domain providers who need some shaming.


* [Bluehost](http://www.bluehost.com/) - demand it from [@bluehostsupport](https://twitter.com/bluehostsupport)
* [1and1](http://www.1and1.com/) - demand it from [@1and1_4U](https://twitter.com/1and1_4U)
* [Network Solutions](http://www.networksolutions.com/) - they [says it's supported](https://twitter.com/netsolcares/status/428650523110416384) but you have to call to activate it, and it's not publicly documented. Nowhere near easy or good enough.
* [Namesco](http://www.names.co.uk/) - demand it from [@Namesco](https://twitter.com/Namesco)
* [Domainmonster.com](https://www.domainmonster.com/support/) - demand it from [@domainmonster](https://twitter.com/domainmonster), because they have a [broken idea of two-factor](https://twitter.com/domainmonster/status/428929545061031937)
* [No-IP](http://www.noip.com/) - Can't find it mentioned anywhere, demand it from [@NoIPcom](https://twitter.com/NoIPcom)
* [DynDNS](http://dyn.com/dns/) - demand it from [@Dyn](https://twitter.com/Dyn) as a standard feature, they apparently [only offer 2FA to premium accounts](https://twitter.com/Dyn/status/430796586223161346)

## Providers working on 2FA now

* [Rackspace](http://www.rackspace.com/) - they've updated [their support thread](http://feedback.rackspace.com/forums/71021-product-feedback/suggestions/1633921-please-provide-2-factor-access-for-the-management-) to say it's coming this summer, and to offer early access

Tweet at [@konklone](https://twitter.com/konklone) with any providers I'm missing, and I'll add them to the list.

<span style="font-size: 80%">*Update*: Mentioned the social engineering aspect to the attack, which 2FA wouldn't have prevented.</span>

<span style="font-size: 80%">*Image credit: [http://halfelf.org/2013/two-factor-authentication/](http://halfelf.org/2013/two-factor-authentication/)*</span>