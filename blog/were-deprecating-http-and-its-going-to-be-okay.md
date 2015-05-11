Mozilla recently announced their **[intent to deprecate the insecure HTTP protocol in Firefox](https://blog.mozilla.org/security/2015/04/30/deprecating-non-secure-http/)**. In practice, they plan to do this by gradually removing the ability for HTTP websites to use various web features. They're joined by the Chrome security team, which declared something similar in December. 

Mozilla's announcement has gotten a lot of attention, more than Chrome's, and much of it negative. There have been various laments, but the most sincere and helpful one is Ben Klemens' ["HTTPS: the end of an era"](https://medium.com/@b_k/https-the-end-of-an-era-c106acded474):

> But the Mozilla foundation’s HTTPS requirement is, to me, the real end of the DIY era. This is not a closed-source corporation, or a startup pushing its new tool, or the arrogant guy at the hackathon, but the Mozilla Foundation — “Our mission is to promote openness, innovation & opportunity on the Web” — saying that if you are building web pages using tools from your desert island, without first filling in registration forms, then you are doing it wrong.

I understand the fear of raising the barriers to entry. As a child, I too fell in love with an internet made by everyone, and have spent my [career](https://konklone.com/resume), my [volunteer work](___), and my [hobbies](___) trying to share what that love has taught me. I want children everywhere in the world to grow up feeling like the internet that permeates their lives is also in their service -- a lego set in real life that you can buy with a week's allowance.

As an adult, I also understand that power for ordinary people is hard to come by and hard to keep. The path of least resistance for human society is for money to buy more money, and might to demand more might. Democracy is designed not so much to expand freedom as it is to give people tools to desperately hold onto the freedom they have.

Put another way: power has a way of flowing away from the varied, strange, beautiful little leaf nodes and into the unaccountable, unimaginative, ever-hungry center.

TCP/IP, DNS, and the Web were each tremendous reversals of this trend, freely giving the means of production to all of us little leafs. It felt like the powers that be just didn't realize what was happening until it was too late.

But here's what I see when I look at the last few years:

* Verizon [injects tracking headers](http://www.forbes.com/sites/kashmirhill/2014/10/28/find-out-whether-this-privacy-killing-super-cookie-is-on-your-phone/) into unencrypted traffic so they can sell your browsing activity to advertisers. This program started in 2012, after [Verizon realized](http://www.fiercemobileit.com/story/verizon-app-usage-monitoring-raises-consumer-privacy-fears/2012-10-16) they "had a latent asset", but wasn't noticed until 2014.
* Other companies like Turn [piggyback on Verizon's tracking header](http://webpolicy.org/2015/01/14/turn-verizon-zombie-cookie/) to sell your data to even more people, because they "are trying to use the most persistent identifier that we can in order to do what we do", says Turn's **chief privacy officer**.
* Comcast [injects ads](http://arstechnica.com/tech-policy/2014/09/why-comcasts-javascript-ad-injections-threaten-security-net-neutrality/) into unencrypted traffic, because "it's a courtesy, and it helps address some concerns that people might not be absolutely sure they're on a hotspot from Comcast".
* Andreas Gal (Mozilla's CTO, in his personal capacity) [has claimed that Yahoo and Bing](http://andreasgal.com/2015/03/30/data-is-at-the-heart-of-search-but-who-has-access-to-it/) "can acquire search traffic by working with large Internet Service providers" to harvest users' Google search results to improve their own -- and strongly implies that they used to do this before Google shut them out through encryption.
* The nation of India [tried and failed to ban all of GitHub](http://techcrunch.com/2014/12/31/indian-government-censorsht/). HTTPS meant they [couldn't censor individual pages](http://ben.balter.com/2015/01/06/https-all-the-things/), and GitHub is too important to India's tech sector for them to ban the whole thing.
* The [nation of China weaponized the browsers of users all over the world](http://www.vox.com/2015/3/30/8315281/github-chinese-ddos-attacks) to attack GitHub for hosting anti-censorship materials (since like India, they can't block only individual pages) by [rewriting Baidu's unencrypted JavaScript files in flight](https://citizenlab.org/2015/04/chinas-great-cannon/).

And I haven't even mentioned the subject that got me and a lot of other people thinking differently about the network -- government surveillance:

* The [NSA](https://www.nsa.gov) scans [just about everything that goes through the internet backbones](https://en.wikipedia.org/wiki/XKeyscore) and saves as much of it as possible, in collaboration with intelligence agencies around the world. This is called "upstream collection", and their "posture" is to ["collect it all"](https://www.aclu.org/files/natsec/nsa/20140722/New%20Data%20Collection%20Posture.pdf).
* The NSA's upstream collection program has not been reformed. It [will not be reformed](https://www.eff.org/deeplinks/2015/05/usa-freedom-markup-glimpse-fight-reform-section-702) by the current draft of the USA Freedom Act, in fact was [endorsed by the only government agency](http://www.nytimes.com/2014/07/03/world/privacy-board-backs-nsa-program-that-taps-internet-in-us.html) whose job it is to review it, and the [most meaningful court victory so far](http://www.theverge.com/2015/5/7/8565111/appeals-court-rules-against-nsa-phone-collection-aclu-clapper) -- while a wonderful and important precedent -- addresses a separate program that only touches data about telephone calls.
* After the Charlie Hebdo attacks, France is now [making bulk internet spying explicitly legal](http://www.nytimes.com/2015/05/06/world/europe/french-legislators-approve-sweeping-intelligence-bill.html?_r=0) and giving its intelligence services vast powers to work with ISPs to surveil the network.
* The United Kingdom is likely to do something similar, after Cameron's [strong re-election](http://www.nytimes.com/2015/05/09/world/europe/david-cameron-and-conservatives-emerge-victorious-in-british-election.html) means he can make good on [his pledge to make all online communication subject to monitoring](http://www.telegraph.co.uk/technology/internet-security/11340621/Spies-should-be-able-to-monitor-all-online-messaging-says-David-Cameron.html).

When I look at all these things, I see companies and government asserting themselves over _their_ network. I see a network that is not just overseen, but actively hostile. I see an internet being steadily drained of its promise to interpret censorship as damage.

In short, I see power moving away from the leafs and devolving back into the center, where power has been used to living for thousands of years.

We really can change this dynamic by making encryption ubiquitous, and on the web that means HTTPS. We can force online surveillance to be as narrowly targeted and inconvenient as law enforcement was always meant to be. We can force ISPs to be the neutral commodity pipes they were always meant to be. This is why the [IETF](https://datatracker.ietf.org/doc/rfc7258/) and [W3C TAG](http://www.w3.org/2001/tag/doc/web-https) have each said it's where we have to go.

But even for all of that: do we still want to make _everyone_ go through the trouble of setting up HTTPS and dealing with certificate authorities?

Fortunately, HTTPS isn't _**nearly**_ as expensive or annoying or insecure as it used to be, and it's getting better all the time. The complaints that people have today about HTTPS and certificate authorities aren't all baseless, but some are misunderstandings, and others are becoming increasingly outdated.

### Certificate authorities aren't gatekeepers

> In other words, as long as your site is not secure, it can be used as a weapon against your users and against other web sites. More non­secure sites means more risk for the overall Web.
>
> -- [Mozilla's HTTP deprecation FAQ](https://blog.mozilla.org/security/files/2015/05/HTTPS-FAQ.pdf)

Certificate authorities are an administrative hurdle, and they're certainly a high-value target for hacking -- but they're not gatekeepers or points of control.

When you run a website over insecure HTTP, you've ceded control of your website entirely to the network. Every company or government with a device in between visitors and your website is a gatekeeper, and they can rewrite or censor your website however they wish.

When you move your website to HTTPS, you take away the network's control in exchange for paying a nominal fee to a trusted outside observer (a certificate authority) to cryptographically sign a statement saying that you owned the domain the last time they checked.

That's all -- certificate authorities have no control over a domain they've issued a certificate for. They don't see your private key, and they can't decrypt your traffic. Certificates can be issued as inexpensively and automatically as a domain name, without any scanning or approval of your website or its content.

In fact, you do have a gatekeeper and point of control: your domain registrar. By using a domain name, you already pay a nominal fee to an organization, often for-profit, to participate in a centralized system.

Your registrar can yank your domain name any time, which is how courts compel this to occur. Registrars are bound by ICANN rules and accreditation, not technical constraints. Moreover, DNS is distributed, not decentralized -- there is a [root server](https://en.wikipedia.org/wiki/Root_name_server) that ultimately controls all of our domain names, and its administration is also overseen by ICANN.

In [his piece](https://medium.com/@b_k/https-the-end-of-an-era-c106acded474), Ben Klemens references the [Debian free software test](https://people.debian.org/~bap/dfsg-faq.html#testing) by saying "An HTTPS site can not be built on a desert island network, because you need a signature from a certificate authority." If your desert island network is local, you can make and trust your own certificate authority. If it's meant to communicate outside the island, I don't see how that's any different than registering a domain name from the public DNS.

Ben also says "A dissident is screwed, because the dissident must give identifying information to the certificate authority." But registrars ask for WHOIS contact information too, and people use fake or non-personal data for that all the time. Certificate authorities only verify that data for certain (needlessly) expensive kinds of certs, which are not a requirement for HTTPS.

All of these pieces -- your domain name, your certificate, even your credit card -- are built on imperfect systems, none of them fully decentralized, but good enough to build an internet on.

<div class="callout">
If you're interested in learning more about the technology, history, and politics of DNS and ICANN, I can't <a href="https://twitter.com/konklone/status/594614743765164033">recommend highly enough</a> this <a href="https://www.newamerica.org/oti/controlling-internet-infrastructure/">policy paper on the IANA transition</a> (<a href="https://static.newamerica.org/attachments/2964-controlling-internet-infrastructure/IANA_Paper_No_1_Final.32d31198a3da4e0d859f989306f6d480.pdf">PDF</a>) by Danielle Kehl and David Post at the Open Technology Institute.
</div>

### HTTPS is getting stronger

The main issue with certificate authorities are that their promises of verification are fallible. While it's uncommon, they [can be fooled](http://www.win.tue.nl/hashclash/rogue-ca/), they [can be hacked](http://www.wired.com/2011/03/comodo-compromise/), and they [can make mistakes](http://googleonlinesecurity.blogspot.com/2015/03/maintaining-digital-certificate-security.html).

Browsers trust ~50 roots and hundreds of intermediaries and resellers, and they can all issue certificates for any domain. This is a...creaky system. They're held in check largely through human mechanisms like auditing, shame, and market competition.

Unlike DNS, certificate authorities are more of an implementation detail. HTTPS just means "secure HTTP". We could replace certificate authorities and guarantee that "S" in other ways.

Moxie Marlinspike has tried very hard: he has a [devastating presentation on CAs](https://www.youtube.com/watch?v=Z7Wl2FW2TcA) from 2011 where he first proposed [Convergence](http://convergence.io), a CA alternative that relies on trusting the consensus vantage point of institutions you trust. In 2012, Marlinspike and Trevor Perrin proposed [TACK](http://tack.io), a TLS extension that reduces dependency on CAs by letting you "pin" your site to your own key.

While these didn't get adopted, they moved the community's thinking forward considerably. Today, people continue to work on [DANE](https://en.wikipedia.org/wiki/DNS-based_Authentication_of_Named_Entities), [Namecoin](https://namecoin.info), and [other novel approaches](https://github.com/okTurtles/dnschain) to replace CAs.

Maybe we'll get there yet. In the meantime, everyone is patching up the CA system we have.

[HTTP Public Key Pinning](https://developer.mozilla.org/en-US/docs/Web/Security/Public_Key_Pinning), similarly to TACK, lets you specify which keys (yours, or a CA's) are allowed to sign a certificate for your domain, making it harder for unpinned CAs to forge certificates for your domain. Even if you don't pin, [Certificate Transparency](http://www.certificate-transparency.org) (once fully operational) hopes to make it possible to detect forged certificates as soon as they are issued.

In recent years, the [CA/Browser Forum](https://en.wikipedia.org/wiki/CA/Browser_Forum) finally formalized a set of [baseline requirements](https://cabforum.org/baseline-requirements/) CAs agree to follow. These make it easier for browsers to hold CAs accountable for operational failures, and helped to [make the case for punishing CNNIC](https://groups.google.com/d/msg/mozilla.dev.security.policy/czwlDNbwHXM/amxjB32uY8AJ) when they mis-issued a certificate.

The last 2 years have also seen a number of (high profile!) [fixed vulnerabilities](https://en.wikipedia.org/wiki/Heartbleed) and [phased-out](https://konklone.com/post/why-google-is-hurrying-the-web-to-kill-sha-1) [protocols](https://tools.ietf.org/html/rfc7465). The [next version of TLS](https://tlswg.github.io/tls13-spec/#rfc.section.1.2) focuses on ripping out code, requiring stronger ciphers, and shortening handshake times.

It's been messy, with a litany of lessons learned, but HTTPS really is getting stronger.

### Everything gets easier when everyone's on board

HTTPS is also getting easier. Have you ever tried [using PGP to send encrypted email](http://www.bitcoinnotbombs.com/beginners-guide-to-pgp/)? Or how about signing up for a [mailman listserve](http://www.metzdowd.com/mailman/listinfo/cryptography)? If so, you've experienced the joy and usability of a technology used exclusively by a small group of power users.

HTTPS has historically been very annoying to set up and maintain, because by and large the only people using it were required to for their jobs. Now that more people are using it and demanding it, this is finally changing, and a real marketplace is forming.

When I taught myself how to set up HTTPS, I [suffered through StartSSL](https://konklone.com/post/switch-to-https-now-for-free) for a free certificate. As more people like me started getting into HTTPS, [SSLMate](https://sslmate.com) emerged to make our lives **a lot** easier. My team at work has [moved entirely to SSLMate](https://github.com/18F/tls-standards/tree/master/certificates) to secure our .gov domains. The extra ease of use has meant more of our teammates are comfortable setting up HTTPS, and the ease of automation means we can [integrate HTTPS into our tools](https://github.com/18F/sslmate-cookbook).

A lot of people point to [Let's Encrypt](https://letsencrypt.org), a non-profit free CA backed by Mozilla and EFF that promises automated certificates for $0. It's not ready yet, but I'm optimistic and confident it will work and make a lot more people comfortable and happy with HTTPS. Behind Let's Encrypt is the [ACME protocol](https://github.com/letsencrypt/acme-spec), a standard for automatic certificate issuance that could make it easier for more CAs to get started, and reduce prices across the industry.

But even if Let's Encrypt totally fails, and ACME goes nowhere, everything will be okay. There will be others. Shared hosts will start baking it into their services, and CDNs and other services will be forced to drop the premium they charge for HTTPS.

The only way HTTPS will scale to the whole web is for it to Just Work -- it needs to be as simple as registering a domain name, or close to it. The only way to generate the investment necessary to make that possible is for everyone to get on board.

### Technology is politics

Technology alone can't solve all of our problems, but technology is never alone. Solutions to societal problems are political, and technology is political. TCP/IP and DNS are political. [The IETF is political](https://tools.ietf.org/html/rfc7258). [The W3C is political](http://www.w3.org/2001/tag/doc/web-https).

And Mozilla's deprecation of HTTP is political. It's meant to normalize something that currently sounds extreme. It's meant to seize a moment during a time of war over control of the network, and to make it harder for the opposing forces to seize their own. It's an act of leadership, and a strong decision made despite a complicated set of tradeoffs.

The transition to HTTPS won't be painless, but it is necessary, and it will get better every year. The web will evolve, and when it does we'll have pushed some of its power back out of the center and into its edges for another generation to wield, love, and defend.
