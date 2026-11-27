# Which IP for an Amazon Seller Central account? One static ISP IP per account (2026)

**Give each Seller Central account its own static ISP IP, keep that IP for as long as the account exists, and reach Seller Central only through a browser profile that serves that one account.** Staff sign in as their own Seller Central users inside that profile, so the account sees one steady address and Amazon's own records show who did what. Proxy302 maintains this repository and sells these proxies. Our Amazon ISP is made for this job: 12 PTC (1 PTC = US$1) per 30 days, the first IP half price (6 PTC), and every IP is checked before delivery to confirm it is not a datacenter address. A regular static ISP IP does the same job for $7.99 per 30 days, or $0.50 for a one-day test. Static IPs of 30 days or longer are dedicated to the buyer. An IP only keeps a legitimate account's connection consistent. Who may open an account, how many accounts a business may hold and how verification is passed are Amazon's decisions, and no IP changes them.

> Proxy302 maintains this repository and sells the IPs described here; we are a vendor, not a neutral reviewer. 中文：[README.zh-CN.md](README.zh-CN.md)

## Contents

1. [What Amazon decides, whatever the IP](#1-what-amazon-decides-whatever-the-ip)
2. [Plan it before you buy](#2-plan-it-before-you-buy)
3. [Amazon ISP or a regular static ISP IP](#3-amazon-isp-or-a-regular-static-isp-ip)
4. [Setup](#4-setup)
5. [A monthly five-minute check](#5-a-monthly-five-minute-check)
6. [Mistakes that undo the setup](#6-mistakes-that-undo-the-setup)
7. [FAQ](#7-faq)
8. [Related](#8-related)

## 1. What Amazon decides, whatever the IP

- **Number of accounts.** Amazon's Seller Code of Conduct (in Seller Central Help) allows one Seller Central account per region you sell in, unless you have a legitimate business need for a second one and all your accounts are in good standing. A separate IP per account does not create that need. Ask Seller Support before you open a second account.
- **Regions and marketplaces.** Amazon groups marketplaces into regions, and one Seller Central account can list in several marketplaces of a region. Count IPs by account, not by marketplace.
- **Verification.** Identity and business verification is passed with genuine documents that match your registration, plus whatever further step Amazon's request names. The network you connect from plays no part in it, and nothing here helps an application whose details are not true.
- **Location.** Pick an IP in the place your business really operates from and keep it there. An IP is never a way to present the business as operating from a place its registration does not show.

## 2. Plan it before you buy

Write the mapping down once; most later problems come from skipping this step.

| Seller Central account | IP | Browser profile | Who signs in there |
|---|---|---|---|
| Account A (your one regional account) | IP 1 | Profile "A" on the office PC, copied to the manager's laptop | Owner, two staff, each with their own Seller Central user |
| Account B (only if Amazon confirmed a legitimate need) | IP 2 | Profile "B" | Its own people |

Rules that follow from the table:

- One account, one IP, one profile. Never both accounts in one profile or on one IP.
- Staff work inside the account's profile, signed in as themselves (Settings, then User Permissions, in Seller Central). The owner's password and two-step verification stay with the owner.
- If a staff member also sells on their own account, that account lives in a different profile on a different IP.

## 3. Amazon ISP or a regular static ISP IP

| | Amazon ISP | Regular static ISP IP |
|---|---|---|
| Made for | Signing in to Seller Central; checked before delivery to confirm it is not a datacenter address | Any long-lived account, Amazon included |
| Price | 12 PTC per 30 days, first IP 6 PTC | $0.50 for 1 day, $7.99 for 30 days, the same in every country |
| Longer terms | Renew every 30 days | Also 60 days $15.98 and 90 days $23.97 |

Black Friday, 24 Nov to 4 Dec 2026 (UTC+8): the regular static ISP IP costs $14.00 for 60 days and $18.00 for 90 days (1 to 30 days unchanged).<!-- bf2026 -->

Choose Amazon ISP when Seller Central is the only thing the IP is for and you want the pre-delivery check. Choose a regular static ISP IP when the same business also runs a shop on another platform, or to try the setup for a day first. Both keep their address for the whole term. Rotating residential traffic ($1.50/GB) is only for logged-out checks, such as viewing your listing as a shopper in another marketplace; never sign in to Seller Central through it. The countries offered are on the order page, and all prices are on [proxy302.com/pricing](https://proxy302.com/pricing/).

## 4. Setup

1. **Buy one IP per account** in the country your business operates from. A static ISP IP is sold as HTTP or SOCKS5, chosen at purchase; HTTP is the safe choice for Chrome and other Chromium browsers, which cannot log in to a SOCKS5 proxy with a username and password.
2. **Check the exit before you use it** (USER, PASS, HOST and PORT are placeholders):

   ```bash
   curl -sS -x "http://USER:PASS@HOST:PORT" https://ipinfo.io/json
   ```

   `ip` should match your order, `country` the country you bought, and `org` an internet operator rather than a hosting company.
3. **Create the account's browser profile** (a separate Chrome profile with a proxy extension, or a profile in an antidetect browser), enter host, port, username and password, and open `https://ipinfo.io/json` inside it to see the same result.
4. **Sign in to Seller Central from that profile** and complete two-step verification on the owner's phone or authenticator app.
5. **Add staff as users** with only the permissions they need, and have them work in the same profile.
6. **Turn on auto-renew** for the IP, or put the end date in a calendar. Renewing keeps the same IP; a lapsed IP is released and the next order brings a new address.

## 5. A monthly five-minute check

- Run the `curl` line from step 2 again: the `ip` should not have changed.
- Look at the IP's end date and the auto-renew switch in your console.
- In Seller Central, review the user list and remove people who have left.
- Confirm nobody has copied the account's proxy into another profile.

## 6. Mistakes that undo the setup

| What happens | Why | What to do |
|---|---|---|
| Seller Central keeps sending new sign-in alerts | Someone signs in outside the profile, on the office network or at home | Make the profile the only way in; bookmark Seller Central there only |
| Two accounts end up on one address | A profile was cloned with its proxy settings | Give every account its own IP and check each profile's exit |
| The profile stops connecting one day | The IP's term ended | Renew earlier, or turn on auto-renew |
| `org` shows a hosting company | A datacenter IP was bought by mistake | Replace it with Amazon ISP or a static ISP IP |
| 407 Proxy Authentication Required | The profile holds a mistyped username or password | Copy them again from the console; HTTP versus SOCKS5 must match the purchase |
| A staff member's own shop is opened in the work profile | Convenience | Separate profile, separate IP, separate device if possible |

## 7. FAQ

**Is one IP enough for several marketplaces in the same region?**
Yes. It is one Seller Central account, so it gets one IP.

**My staff work from another country. Which country should the IP be in?**
The country your business operates from, kept the same for the account's life. Staff work in the account's profile and sign in as their own Seller Central users, so Amazon's own records show who did each task.

**Can I use the Amazon Seller app on my phone?**
It is your own account on your own phone, so that is ordinary use. What to avoid is signing in to two different seller accounts on the same phone or the same IP.

**Amazon asked me to verify my identity again. Will the IP help?**
No. Submit genuine documents that match your registration and follow the steps Amazon names.

**Is there a free trial?**
No. The lowest-cost way to try the setup is a static ISP IP rented for a single day at $0.50; with Amazon ISP, the first IP you buy costs half.

## 8. Related

- [What proxy should I use for an Amazon Seller Central account?](https://github.com/proxy302/proxy-guides/blob/main/proxy-for-amazon-seller-account/README.md)
- [Static vs dynamic residential IP](https://github.com/proxy302/proxy-guides/blob/main/static-vs-dynamic-residential-ip-zh/README.md) (Chinese)
- [How can I tell if a proxy IP is residential, ISP or datacenter?](https://github.com/proxy302/proxy-guides/blob/main/check-if-ip-is-residential/README.md)
- [proxy-dnsbl-check](https://github.com/proxy302/proxy-dnsbl-check): is an IP on a spam blocklist?

*Facts checked 23 November 2026.*
