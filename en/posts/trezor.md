---
title: "Trezor - Fake e-mail analysis"
date: 2022-04-02T11:30:00+02:00
draft: false
authors: [Bruno Geronimo]
summary: "Did you get an e-mail saying you were victim of a data leak? It's a fake one, 
and I'm gonna explain why."
---
# Trezor - Fake e-mail analysis

I woke up with an unexpected e-mail today:

{{< cdn src="trezor/email.jpg" alt="E-mail falso" >}}

Generally, I always delete these kinds of e-mails, specially when the content is very "alarming".

For those who don't know, I invest in some criptocurrencies, and I decided to buy a hard wallet 
from [Trezor](https://trezor.io). I have a habit to create accounts using e-mail aliases. 
Instead of using hi@bruno.ge, I use hi+specificword@bruno.ge when creating an account. In most 
cases, it works.

However, what led me to believe this e-mail was the fact I received it **with** the alias.

When I opened the URL, I got redirected to the following page:

{{< cdn src="trezor/fake_trezor_page.png" alt="Fake Trezor website" >}}

When I decided to open the main page, trezor.com, I noticed something was wrong. I ended up in a 
Russian store that sells beautiful and robust lockers:

{{< cdn src="trezor/trezor.com.png" alt="Russian store selling beautiful lockers" >}}

Did you notice something odd in the URL? The page I ended up on was suite.trẹzor.com, with **ẹ**,
not **e**. The domain is a bit different in this case:

{{< cdn src="trezor/converted-domain.png" alt="Converted domain" >}}

This scam is known as [IDN homograph attack](https://en.wikipedia.org/wiki/IDN_homograph_attack).
These domains are very identical to the original one, but using non-latin characters, such as 
cyrillic or with accents, like ã or ẹ, in this case.

Looking at the page, I decided to click on `Trezor suite for web` to see where I would lend. The 
link points to web.trezorwallet.org, which is different than the official URL, https://suite.
trezor.io/web/.

With these suspitions in mind, I decided to check the registration date of these domains, which 
is also a bit odd:

| Domain                                             | Creation date               |
|----------------------------------------------------|-----------------------------|
| xn--trzor-o51b.com (trẹzor.com) - Página principal | 27.03.2022 - 11:09:17 (UTC) |
| trezorwallet.org - Página do webclient             | 27.03.2022 - 07:03:32 (UTC) |
| trezor.us - Domínio do remetente do golpe          | 09.07.2021 - 00:01:19 (UTC) |

Trezor is an existing company since 2013. Having such brand-new domains is also a scam indication.

Another thing to keep in mind is the fact that most Trezor built apps are [open-source](https://github.com/trezor),
including [Trezor Suite](https://github.com/trezor/trezor-suite), the 
[landing page](https://github.com/trezor/trezor-suite/tree/develop/packages/suite-web-landing) 
and their own [website](https://github.com/trezor/trezor-suite/tree/develop/packages/suite-web).
Anyone is able to download the source-code, edit the clients and create scam apps or pixel 
perfect pages due to that.

After analyzing all these factors, even though the e-mail convinced me at the beginning due to 
the alias, everything suggests that their e-mail list got leaked somehow and these e-mails are 
an attempt of scam.

Trezor also announced on their [Reddit](https://www.reddit.com/r/TREZOR/comments/tv5yn9/we_are_investigating_a_potential_data_breach_of/) 
about the pottential data leak from MailChimp. 

I reported the incident to all companies involved on the domain registration by checking their 
WHOIS, to the [Internet Crime Complaint Center](https://www.ic3.gov/) and to the 
[Internet Beschwerdestelle](https://www.internet-beschwerdestelle.de/en/index.html).
