---
{"dg-publish":true,"permalink":"/random-thoughts/do-it-self-mostly/","dgPassFrontmatter":true}
---

*Sunday, September 8, 2024 @ 10:50 AM - Colorado*

Tailscale has changed my life, seriously.

I got into computers in the 80's, and the Internet in the 90's, and by 1998 I was running my own version of a tiny datacenter on a single computer with a dial-up modem. It was a Linux box that routed Internet to all computers in the house, auto-dialing when requested. It hosted my email as well along with a file server. Basically any simple service an office might have, I wanted to replicated it on my own and make it "online" so that I could reach it away from home.

In the 2000's I was using the basic data features of my phone with Bluetooth to connect a tiny Sharp Zaurus device from Japan that ran Linux to my home hosted service so that I could have access to my stuff anywhere that I could get a signal.

# Three things happened since then

## Online Services for Everyone
Basically, Gmail, but not just Gmail. Dropbox, Google Maps, Rhapsody, Spotify, Netflix, it just kept coming. This wasn't just a service to replace either self-hosted or at least individually paid-for services (like your own email account on your own domain, run by some random company for a small fee), it was an ecosystem that promised limitless possibilities, ease, and a subscription. They weren't wrong either. Dropbox would keep your files available 24x7, anywhere in the world, with almost zero effort on your part, and even have them if your house burned down or home Internet died, all while adding value like helping you find things in images.

It was a strong commercialization of everything in a way that made sense, especially as I started a career and a family and started to have more free money than time. Why should I run my own server when for pennies a day someone else would do it for me, and far better?

## Smartphones
I was using my Zaurus, and a series of Palm devices, and eventually Windows CE devices for over a decade before the slow (it ran only on 2G when 3G existed) iPhone without even the basic feature of copy/paste (yes, the initial iOS had no copy/paste feature) came out. I felt like it was a very odd device, entering the market so much later than CE devices and missing the most basic features.

What Apple got right though, they got very right, and it captured the minds of millions of people who had sneered at the quirky keyboard laden, stylus requiring, CE devices. (Even my Zaurus had a stylus, as the screen was resistive and way too tiny to use a finger on while displaying an entire Gnome desktop.)

The initial iPhone was far too limited for me, but they quickly moved forward, based on the wild success and overtook everything else. I too had an iPhone soon, and eventually Android also caught up and I switched to that more open platform.

These devices were both the perfect interface to self-hosted services, but also the death of them. While you could self-host, the easier way to use these devices was with built-in and downloadable Apps. Apps that were not built as generic "email clients" or "file explorers", though these did exist just barely, these Apps were all built to pull you into the commercial online service ecosystems. If you felt the least bit disinterested in the benefits of Gmail or Dropbox before, the Smartphone sealed the deal. The entire "mobile first" movement was all about monetization, and it was being done very well.

Basically smartphones were the gateway to make all of these commercial services easier to reach, more valuable, and more ubiquitous. Before smartphones only a few people cared about accessing their email or files away from home, but now everyone did. Suddenly my dad wanted Dropbox.

## Security
In the late 60's seemingly nobody was thinking much about security on the Internet, and by the late 90's, still few people were, at least too few. The services I was hosting were locked down as well as I knew how, and truly the content was of little value anyway.

However, as I grew older the content I had became more valuable, both on a personal level (pictures of kids, not just cats) and a financial one (I had bank accounts!), and the landscape of international hacking grew.

Initially on dial-up we all had our own IP and anything we hosted was just on that IP. It changed on every connection, but that is what dynamic DNS providers were for. Then with DSL came NAT that was done by a router I wasn't in control of, so instead of hosting directly I was "punching holes" to ports in the NAT. Either way, my devices were more or less directly listening on the Internet and it was up to me to harden them against attack.

If I didn't expose them to the Internet, then I couldn't reach them myself, but if I could reach them, anybody could, and so it was always a risk.

Eventually I felt it wasn't worth the risk in most cases and I relied on commercial services to both host my data and provide security for it. Sure, Dropbox might get hacked, but it was more likely that I would get hacked personally than that an army of skilled IT workers would fail at Dropbox. A bigger risk was just them giving my data away, but it was a risk I was willing to trade for the ease of use.

I always hosted some things but either they were basic things I felt provided little risk, like a Minecraft server on a random port (which as far as I can tell nobody ever even found, much less got into) or of course I had a full on Wireguard VPN eventually, but only connected to that rarely for full-on access to my network.

# A return to Do It Self

So how is the landscape different in 2024 than it was a few years ago when I was happy to use Dropbox and Gmail and more or less have no access to my home network?

## Enshitification
This word is useful mostly because it covers an enormous range of sins now, from "I don't trust them not to share my info with governments" to "I'm tired of being the product" to "I don't want my stuff scraped for AI".

Basically, the promise of Gmail from decades ago has been broken, and even the services we may find aren't broken, we don't trust anymore.

## REALLY fast Internet
I have 5 Gigabit up and down now at home! Yeah, that is nuts! I realize I'm in a minority, but even 1 Gigabit is getting more and more common. This is amazing for so many things, but it makes self-hosting basic documents and such a non-issue. Nobody even notices this bandwidth.

## Docker
Docker has been around for a long time now, but it is super mature now. Mature to the point that it has kind of itself been partly enshitified but also partly replaced. At this point you can "use docker" as in, containers, without actually using any Docker code.

Basically, it is both free/open and almost anyone can use it because it is has been around long enough to be robust and well documented.

## Tailscale
The problem then in 2024 with self-hosting anything is the logistics and security

### Logistics

#### IP Addresses, Ports and DNS Names
If you want to host two things, you need two IP's or if you hate yourself and don't mind typing `:1234`, `:1235` after every connection in every dialog and on every web page, you can hang, in theory, up to 65,535 things off of your one IP, "punching one hole" per service through your NAT in the router.

#### VPN Logisitcs
VPN is an all or nothing proposition: The other option is to VPN your devices into your home network, run your own DNS (another headache) and now you have access to all of your services (although the IP/port thing is still an issue if you want to run 2+ things on one computer), but **now all of your Internet traffic away from home passes through your home Internet connection.** This might work OK with my 5 Gigabit connection, but the reality is even if that works well it adds a lot of latency and also bogs down my home network with traffic that should never go there.

### Security
If we go the all-on VPN route that is OK, but if we punch holes, now **each service** is exposed to the Internet, and while maybe I locked down my video service well did I also lock down my file server well? **Any one** of them could have a vulnerability, or more likely, a simple misconfiguration on my part, like a missed/forgotten default account that suddenly gives all of my stuff to everyone on the Internet.

Tailscale fixes **all** of this!
1. Security: It is a VPN, so my connection to it and the traffic going to/from it is secure to me, nobody else can access or even see that it exists!
2. Per Connection VPN: This is the brilliant part. Several people were telling me about Tailscale, but I wasn't getting it. I kept saying, "I just use Wireguard." Reddit kept telling me, "Tailscale is just Wireguard for people who don't want to learn to set up Wireguard." This is wrong though. Tailscale almost isn't Wireguard. Instead it is a re-implementation of Wireguard protocols in a way that lets me set up infinite services, all on the same computer, each with their own DNS entry, each on whatever port I want, all visible to my phone, my computer, my whatever, on the Internet as an individual service, without routing any other traffic over that "VPN". It is a per-service VPN.

So now in 2024 that I'm no longer enamored with commercial services, and I've learned to get good at Docker, and the self-hosting revolution has produced a lot of really nice ready-to-go services that are easy to deploy and use, and Tailscale has enabled me to spin them up in a way that is both easy to access with a simple URL and secure, I'm going nuts.

In the past few weeks I've set up over a dozen self-hosted services and I use them daily now!

The future looks bright again, the way it did in the late 90's, and I have Tailscale to thank for it.

### Final dose of reality
Of course, when will Tailscale be enshitified? It is a commercial service, and the promises they make sound a lot like what Google told us 20+ years ago.

All I can say here is that there **is** an open-source version of Tailscale, so my hope is that much like Docker, if Tailscale ever turns away from their open roots, we will already be able to basically do it without them by then, which is good. Much like, even if you dislike Chrome, you have to thank Google for Chromium, Tailscale also supports FOSS, which is part of why I love them.

For Tailscale's own take on this topic, I suggest reading their blog article:
[The New Internet](https://tailscale.com/blog/new-internet)
