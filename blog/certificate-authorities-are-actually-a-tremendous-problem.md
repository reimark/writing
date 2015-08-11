I was surprised to see myself quoted in [Marc Ambinder's post](http://theweek.com/article/index/245963/how-does-nsa-hack-into-e-mails) this morning on the viability of the NSA collecting Gmail data in bulk — not through court orders, but by tapping the network itself:

> Unless NSA has found a way to mess with the traffic cops — the certifying authorities — I don't see how NSA possibly reads Google emails in real-time, looking for content, using keyword searches. Indeed, I don't know NSA would be able to break the encryption of an email that somehow fell under what secret safe harbor provisions they have for emergencies. They really do need Google's help to read every email they do not steal from either end of the communication.
> 
> Eric Mill, a developer for the Sunlight Foundation, summed it up for me in a Tweet: "NSA can and does sniff traffic as it moves across the Internet, especially through backbones. Encrypted traffic is safe-ish."
> 
> <cite>Marc Ambinder, [How does NSA hack into emails?](http://theweek.com/article/index/245963/how-does-nsa-hack-into-e-mails)</cite>

It's very important to emphasize the "-ish", because there are **huge concerns** over "the traffic cops" (the CAs) that very much bring the integrity of encrypted traffic into serious question, as I'll explain a bit later on. Encrypted traffic is only safe-ish *by comparison* to the plain text emails that live on Google's servers. 

And it's that comparison I was initially trying to make, because I thought when Marc first [posed his question](https://twitter.com/marcambinder/status/347497069684068352) about NSA bulk collection, he was mistaking transport encryption for content encryption.

<blockquote class="twitter-tweet"><p><a href="https://twitter.com/marcambinder">@marcambinder</a> Marc: the SSL Google (and banks, etc.) use only encrypts the data during transport. On Google's servers, it's just plain text.</p>— Eric Mill (@konklone) <a href="https://twitter.com/konklone/statuses/347556751215837187">June 20, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" data-conversation="none"><p><a href="https://twitter.com/marcambinder">@marcambinder</a> The NSA can + does sniff traffic as it moves across the Internet, esp through backbones. Encrypted traffic there is safe-ish.</p>— Eric Mill (@konklone) <a href="https://twitter.com/konklone/statuses/347556990769311744">June 20, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" data-conversation="none"><p><a href="https://twitter.com/marcambinder">@marcambinder</a> But the programs here are Google doing lookups of its own user data (in plain text) to provide to the NSA (in plain text).</p>— Eric Mill (@konklone) <a href="https://twitter.com/konklone/statuses/347557115486937089">June 20, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Once I noticed that Marc [already understood this](https://twitter.com/marcambinder/status/347498799813500928), and that I'd taken his tweets out of context, I realized "safe-ish" was ambiguous and overly generous, so I followed up:

<blockquote class="twitter-tweet"><p><a href="https://twitter.com/marcambinder">@marcambinder</a> just saw this. then, yeah, it's a lot safer. However, the "safe-ish" comes from the vulns in the Certificate Authority system.</p>— Eric Mill (@konklone) <a href="https://twitter.com/konklone/statuses/347558356195635200">June 20, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

I didn't elaborate further or provide more links, mostly because I felt embarrassed at taking his original tweets out of context. But since the same has now happened to me, I think it's important I point to how flawed Marc's downplaying of the NSA's data collection ability is.

The reason your browser trusts your bank's website and doesn't yell at you to GET OUT OF THERE is because your bank has had its encryption "certificate" signed by a "[certificate authority](http://en.wikipedia.org/wiki/Certificate_authority)" (CA). Verisign is the most widely known CA; there are many others, and browsers trust [a long list](http://www.mozilla.org/projects/security/certs/included/) of them. If anyone hacked or coerced Verisign or **any** other trusted CA, they could fake a certificate for any website using that CA that any browser would trust, and then decrypt all the traffic they could intercept.

How bad is this? [Slate covered the state of affairs](http://www.slate.com/articles/technology/webhead/2010/08/the_internets_secret_back_door.html) in 2010, and pointed to [the EFF's research](https://www.eff.org/observatory) [right There's even a [fun color map](https://www.eff.org/files/colour_map_of_CAs.pdf)!] showing the Internet's 600+ points of security failure: 

> Who are these certificate authorities? At the beginning of Web history, there were only a handful of companies, like Verisign, Equifax, and Thawte, that made near-monopoly profits from being the only providers trusted by Internet Explorer or Netscape Navigator. But over time, browsers have trusted more and more organizations to verify Web sites. Safari and Firefox now trust more than 60 separate certificate authorities by default.  Microsoft's software trusts more than 100 private and government institutions.
> 
> Disturbingly, some of these trusted certificate authorities have decided to delegate their powers to yet more organizations, which aren't tracked or audited by browser companies. By [scouring the Net](https://www.eff.org/observatory) for certificates, security researchers have uncovered more than 600 groups who, through such delegation, are now also automatically trusted by most browsers, including the Department of Homeland Security, Google, and Ford Motors—and a UAE mobile phone company called Etisalat.
>
> <cite>[The Internet's Secret Back Door](http://www.slate.com/articles/technology/webhead/2010/08/the_internets_secret_back_door.html)</cite>

Sure enough, in 2011, [two CAs were hacked](http://www.wired.com/threatlevel/2011/03/comodo-compromise/) by an Iranian IP address. Browsers had to [ship updates](http://blog.mozilla.org/security/2011/08/29/fraudulent-google-com-certificate/) revoking their trust in the hacked CAs for users to stay safe. In January of 2013, the same thing [happened again](http://thenextweb.com/google/2013/01/03/google-microsoft-and-mozilla-revoke-two-fraudulent-turkish-certificates-used-in-targeted-attacks/) with two Turkish CAs. It will continue to happen — in fact, there's no reason to assume other CAs aren't currently compromised.

At this point, no one likes the Certificate Authority system (except the institutions which benefit from it), but there's no clear path to change it. After the 2011 incident, [Moxie Marlinspike](https://twitter.com/moxie) got mad and designed [Convergence](http://convergence.io), which attempts to work around the CA system by letting you choose whose eyes you trust to see the world. It's a brilliant idea, but has not gone anywhere, and I'm not sure what the security community's vision is for where to go next.

But the biggest reason I didn't enjoy being quoted in this way is more personal. 

I've been utterly [horrified](http://konklone.com/post/children-of-the-internet) and completely changed by the long ([and](http://thenextweb.com/insider/2013/06/20/the-nsa-can-retain-and-use-data-inadvertently-collected-from-communications-of-us-citizens/) [ongoing](http://www.guardian.co.uk/world/2013/jun/20/fisa-court-nsa-without-warrant)) chain of disclosures Edward Snowden has made about the NSA — at this point, we simply [should not assume we know the limits of what the NSA is capable of](http://www.schneier.com/blog/archives/2012/03/can_the_nsa_bre.html). And I'm not comfortable empowering anyone's argument that we should believe we do understand those limits and calm down. The Internet is a [very long term project](/post/2000-year-problems) and its future as a decentralized and empowering force is under serious threat. We should be working to secure it.