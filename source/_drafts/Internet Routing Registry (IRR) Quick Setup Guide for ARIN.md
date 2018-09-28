# Introduction
If you operate an [AS](https://www.thousandeyes.com/learning/glossary/as-autonomous-system), and more specifically [Provider Independent IP address space](https://www.nanog.org/mailinglist/mailarchives/old_archive/1995-05/msg00095.html), you’ve probably heard of this whole IRR thing. Usually a `ROUTE-SET` or `AS-SET` object is asked for when you’re ordering a new IP Transit service, or establishing a new peer.

If you’re not familiar, I’ll break it down as simply as possible:

### Why
- Prefix lists are easy when you’re one company with a handful of peers, and almost no changes are regularly required.
- When you step over to the network|cloud|content provider side...this is less true.
- Customers and peers get new prefixes, or sell old ones, or change routing policies constantly.
- They need a way to automate this so they can safely filter inbound and outbound prefix announcements.
- This is a good idea for enterprises too, because when they *do* make changes, those changes could happen automatically instead of opening a week long change request.

### What
Enter Internet Routing Registries.

> To help automate this task, the Internet Routing Registry (IRR) and the Routing Policy Specification Language (RPSL) were developed to allow you to, in a formal way, describe your routing policy and post it online. This is done by the network of [mutiple IRR databases](http://www.irr.net/docs/list.html) (notable ones include radb, altdb, and those run by the Regional Internet Registries) who allow you to create RPSL objects in their database, which they then serve to others answering their whois queries generating BGP filters.
> <cite> [fcix.net](http://fcix.net/whitepaper/2018/07/14/intro-to-irr-rpsl.html)</cite>

### Where
If you’re in the Europe region, the [RIPE Database](https://www.ripe.net/manage-ips-and-asns/db/support/documentation/ripe-database-documentation) is your friend. 

If you’re like me, and are in North America, and therefore maintain resources from ARIN, you’re not quite as lucky. While [ARIN](https://www.arin.net) has [announced](https://www.arin.net/vault/resources/routing/2018_roadmap.html) their intention to overhaul their IRR implementation, for now, as of late 2018, we still play like its 1995 and manage **all** IRR database changes via email. Sad face.

I had a number of problems getting this to work as expected, at first, primarily due to a lack of adequate, *aggregated*, and concise documentation. Thus, I will try to right that ship for the next lucky sailor.

### How
