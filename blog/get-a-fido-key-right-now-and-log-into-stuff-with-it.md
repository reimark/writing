<figure><a target="_blank" href="http://www.amazon.com/Yubico-Y-123-FIDO-U2F-Security/dp/B00NLKA0D8/ref=sr_1_1?ie=UTF8&qid=1416087355&sr=8-1&keywords=%22FIDO+U2F+Security+Key%22&pebp=1416087293560"><img src="/assets/images/blog/fido/fido-key-1.jpg" style="width: 650px" /></a>
<figcaption>This is a stock photo, but it's the same model I own.</figcaption>
</figure>

`<update>` Since posting this, **[Dropbox](https://blogs.dropbox.com/dropbox/2015/08/u2f-security-keys/)** and **[GitHub](https://github.com/blog/2071-github-supports-universal-2nd-factor-authentication)** have both added support for U2F keys. Microsoft Edge has [begun development](https://dev.modern.ie/platform/status/fido20webapis/) on integrating U2F. Mozilla hasn't made any announcements, but [this is Firefox's tracking bug for the feature](https://bugzilla.mozilla.org/show_bug.cgi?id=1065729). `</update>`

I just got a [U2F security key](http://www.amazon.com/gp/product/B00NLKA0D8/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1), for less than $20, to use as the second factor to log into my Google account. My model is by Yubico, sometimes called a "Yubikey". It's a super-light USB wafer you put into your computer, with a button you tap to log in to websites.

This is a new thing: Google just recently [announced support for security keys](http://googleonlinesecurity.blogspot.com/2014/10/strengthening-2-step-verification-with.html) for their login system. Chrome is the first to ship support for them, but other browsers should follow soon.

These keys are based on an [open standard](https://fidoalliance.org/), and you should **absolutely use one instead of Google Authenticator or SMS**. For one, the usability of "just push the button" is a hell of a lot better than fishing out your phone, opening an app, and typing in a 6-digit number. For another, the keys use fancy crypto to **[completely protect you from phishing and tracking](https://security.stackexchange.com/a/71704/37288)**:

> In the case of U2F, the device creates a public/private key pair for each site and burns the site's identity into the "Key Handle" that the site is supposed to use to request authentication. Then, that site identity is verified by the browser each time before any authentication is attempted. The site identity can even be tied to a specific TLS public key. And since it's a challenge-response protocol, replay is not possible either. And if the server accidentally leaks your "Key Handle" in a database breach, it still doesn't affect your security or reveal your identity.
>
> **Employing this device effectively eliminates phishing as a possibility**, which is a big deal to a security-sensitive organization.

The keys also never identify _themselves_ to the site, meaning that no one can track use of the same key across multiple websites — even _the site owners themselves_.

It's a great step forward, and you can expect to see more support announcements from major websites in the near future. **[Just go buy one](http://www.amazon.com/s/?field-keywords=%22FIDO%20U2F%20Security%20Key%22).** I got [mine](http://www.amazon.com/gp/product/B00NLKA0D8/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1)  for $18.

The keys will Just Work on Mac and Windows (and recently, on Debian stretch). Unfortunately for Ubuntu users...

## Getting it working on Ubuntu

While U2F works out of the box on Debian 9 (stretch), it doesn't yet work on Ubuntu. I also couldn't find a simple set of instructions anywhere. Fortunately, it's extremely easy.

You need to get your computer to recognize the key by adding a `udev` file to your system and rebooting. Yubico makes this easy by [publishing the rules file you need on GitHub](https://github.com/Yubico/libu2f-host/blob/master/70-u2f.rules):

```text
ACTION!="add|change", GOTO="u2f_end"

KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{idVendor}=="1050", ATTRS{idProduct}=="0113|0114|0115|0116|0120", TAG+="uaccess"

LABEL="u2f_end"
```

Copy the text of that file to `/etc/udev/rules.d/70-u2f.rules`, and run:

```bash
sudo service udev restart
```

Then unplug and re-plug in the U2F key, and it should work.

If things don't work, well, try rebooting. If that still doesn't work, leave a comment, [email me](mailto:eric@konklone.com), or [edit my blog post](https://github.com/konklone/writing/blob/writing/blog/get-a-fido-key-right-now-and-log-into-stuff-with-it.md) to fix it.
