# Best VPS Guide: How Much RAM You Need, What the Price Renews At, and Who Handles the Server

Vultr's entry prices are **$5 a month for 1 GB of RAM, $10 for 2 GB and $20 for 4 GB** on the Regular Performance line, or **$6, $12 and $24** for the same sizes on High Performance with NVMe storage. Billing runs hourly with a cap at 672 hours a month, so an instance you destroy after a weekend costs cents rather than a full month. New accounts can apply code **FLY300VULTR** for $300 in credit on select products.

Three things decide whether a VPS is the right purchase: how much RAM the workload actually needs, what the price does after the first term, and who patches the operating system once the server is live. Vultr sits firmly on the self-managed side of that last question, which is the part most "best VPS" lists skip over.

> **Most people:** High Performance 2 GB at $12/month. Two gigabytes covers a small business site or an app with a database, and the newer CPUs plus NVMe cost $2 more than Regular. 👉 [Compare the 2 GB High Performance plan](https://www.vultr.com/pricing/?ref=9738262-9J)
>
> **Cheapest usable:** Regular Performance 1 GB at $5/month for a blog, a staging box or a side project.
>
> **Several sites or steady CPU load:** 4 GB at $20 on Regular or $24 on High Performance.
>
> **Dedicated cores:** VX1 from about $44/month, once shared vCPUs show up as the bottleneck.

## Vultr's plans and what each size is for

Vultr splits its shared-CPU servers into three families. Regular Performance uses previous-generation Intel chips and standard SSD storage and is the cheapest option that can host a real site. High Performance moves to newer AMD or Intel CPUs with NVMe for roughly 20% more, and includes more bandwidth at every size. High Frequency runs 3 GHz+ Intel CPUs on NVMe, priced like High Performance at the small sizes but with more disk and less transfer.

| Plan | CPU / RAM | Storage | Price per month |  |
| --- | --- | --- | --- | --- |
| Regular Performance | Shared vCPU, 1 GB | SSD | $5 | [See current price](https://www.vultr.com/pricing/?ref=9738262-9J) |
| Regular Performance | Shared vCPU, 2 GB | SSD | $10 | [See current price](https://www.vultr.com/pricing/?ref=9738262-9J) |
| Regular Performance | Shared vCPU, 4 GB | SSD | $20 | [See current price](https://www.vultr.com/pricing/?ref=9738262-9J) |
| High Performance | Shared vCPU, 1 GB | NVMe | $6 | [See current price](https://www.vultr.com/pricing/?ref=9738262-9J) |
| High Performance | Shared vCPU, 2 GB | NVMe | $12 | [See current price](https://www.vultr.com/pricing/?ref=9738262-9J) |
| High Performance | Shared vCPU, 4 GB | NVMe | $24 | [See current price](https://www.vultr.com/pricing/?ref=9738262-9J) |
| High Frequency | 3 GHz+ Intel, small sizes | NVMe | Same tier as High Performance | [See current price](https://www.vultr.com/pricing/?ref=9738262-9J) |
| VX1 / Optimized Cloud Compute | Dedicated vCPU | NVMe | From about $44 | [See current price](https://www.vultr.com/pricing/?ref=9738262-9J) |

Below the paid tiers there is a **$2.50 sandbox plan that is IPv6-only**; adding an IPv4 address brings the entry point to $3.50. Above these sizes the pricing page lists larger instances and the Optimized Cloud Compute families. The rows above cover the decision most buyers actually face.

Bandwidth is worth a second look because it differs by family:

| Size | Regular Performance | High Performance |
| --- | --- | --- |
| 1 GB | 1 TB | 2 TB |
| 2 GB | 2 TB | 3 TB |
| 4 GB | 3 TB | 5 TB |

Every account also gets 2 TB of free outbound transfer pooled across all instances and locations, so a quiet server's allowance covers a busy one. Overage runs $0.01 per GB worldwide, and inbound traffic is free.

## What the hourly meter actually charges

Hourly billing is the feature that makes Vultr cheap for short jobs and irrelevant for long ones. The cap sits at 672 hours a month on most plans, which is four weeks. Past that point the meter stops, so a server left running all month costs exactly the listed monthly price. The saving comes from destroying instances, not from keeping them.

| Item | Cost |
| --- | --- |
| Hourly billing | Per hour, capped at 672 hours/month on most plans; VX1 bills actual hours |
| Automatic backups | +20% of the instance price, so $10 becomes $12 |
| Snapshots | $0.05 per GB per month |
| Outbound overage | $0.01 per GB |
| Inbound traffic | Free |
| Stopped (powered-off) instance | Still billed until you destroy it |

That last row catches people. Powering a server off does not stop the charge; deleting it does.

## Managed or self-managed, and where Vultr sits

Every VPS host draws a line somewhere between "we run the box" and "you run the box", and the line sits at the operating system. InMotion Hosting is a useful example because it sells both: managed and self-managed VPS plans on the same hardware in the same data centres. On the managed line, 24/7 support covers the server, the OS, security patches and troubleshooting alongside hardware and network. On the self-managed line, support covers hardware, network and the data centre, and everything above that belongs to the customer.

Vultr sits on the self-managed side. You choose the OS image (Ubuntu, Debian, AlmaLinux and FreeBSD are all documented), you get root and SSH, you install the stack, and you own the firewall rules, the patching schedule and the app configuration. Deployment takes minutes. Keeping the server secure and tuned is the ongoing part of the job.

That trade buys real control. KVM virtualisation gives each instance its own kernel and guaranteed resources, so you can install packages a shared host won't allow, run several applications side by side, and rebuild the environment whenever you want. It also means nobody at the provider is going to notice that your PHP version is three releases out of date.

If you want someone else to handle the OS and the security patches, Vultr's shared plans are the wrong product. Managed options exist elsewhere: DreamHost's managed VPS runs Ubuntu only and doesn't offer Windows, and if you need root to install software there, its Stack plans are the route. InMotion's managed line includes an onboarding service that sets up the server and migrates the site. Those cost more per gigabyte of RAM, and you're paying for the hours you don't want to spend.

## How much VPS you actually need

Rough capacity rules of thumb, assuming a cached and reasonably tuned stack:

- **1–2 GB RAM, 1 core:** 5–10 lightweight sites, or 10,000–50,000 visits a month.
- **4–8 GB RAM, 2–4 cores:** 20–50 sites, or 100,000–500,000 visits a month.
- **16 GB+ with multiple cores:** 1 million visits a month and beyond.

The usual trigger for leaving shared hosting is **90,000 monthly visits**, along with needing root access, needing a PHP module the shared host won't install, running sensitive transactions, or dealing with traffic that spikes hard.

Mapped onto Vultr: a single blog or a low-traffic brochure site fits in the $5 Regular 1 GB instance. A business site with a database and some caching fits in 2 GB, and the $12 High Performance version is worth the extra $2 for the NVMe disk. Three or four sites, or an application with a real database and background jobs, lands on 4 GB at $20 or $24. Only move to VX1 once you can see shared vCPUs limiting you, because $44 a month is a different budget.

If you're still learning FTP, WordPress and cPanel, a self-managed VPS is a costly place to learn. The same applies to non-critical low-traffic sites and to anyone whose budget can't absorb the larger monthly figure.

## What the price does after the first term

Promotional pricing is the biggest source of surprise in this market. Hosting.com advertises a self-managed 8 GB plan at $9.99 a month on a three-year term; it renews at $29. DreamHost's managed plans bill $15, $30, $60 and $90 for the first month and renew at $37.99, $69.99, $137.99 and $169.99. Those are two to three times the headline figure, and the headline is what most comparison tables show.

Vultr's table works differently: one price per size, no renewal column, and the hourly cap means an always-on server costs that listed price. What moves the bill is what you add, and the add-ons are priced clearly enough to plan around. Backups add 20%, so a $10 server becomes $12. Snapshots run $0.05 per GB per month. Overage is a cent a gigabyte, and only outbound counts.

👉 [Check the current per-hour and monthly rates](https://www.vultr.com/pricing/?ref=9738262-9J)

## How the $300 credit works

Vultr's own coupon page lists **FLY300VULTR** for $300 in free credit. The terms printed there: new customers only, select products only, cannot be combined with any other offer, restrictions apply. The page does not state how long the credit stays valid, so plan to use it in your first billing cycles rather than letting it sit.

There's a second offer worth understanding. **VULTRMATCH** matches your first deposit dollar for dollar, up to $100, so a $100 deposit becomes $200 of account credit. If you were going to spend real money anyway, that's a larger effective discount than the free-credit code, and the two can't be stacked.

Practical steps: open the account, apply the code under Billing → Gift Codes before deploying anything, then create the instance. A credit card or PayPal is required even for the free-credit trial, and Vultr places a temporary authorisation hold to verify the card rather than charging it. One promotion per user. Promotional credit doesn't cover tax where tax applies.

👉 [See the current Vultr coupon terms](https://www.vultr.com/coupons/?ref=9738262-9J)

## Questions buyers actually ask

**What is KVM and does it matter?** It's the virtualisation layer that gives each VPS its own kernel and reserved resources instead of a shared slice of one. It's why you can install your own software and run multiple apps on one server, and it's the reason the server needs an administrator.

**Do I need root access?** You get it, and it's the point of self-managed hosting. It's also the risk: root can break the server as easily as it can fix it.

**How much traffic can 8 GB handle?** The general planning figure for 4–8 GB with 2–4 cores is 100,000–500,000 visits a month, with caching and tuned software. Untuned WordPress with heavy plugins will hit the ceiling far earlier.

**Will the price go up?** No promo-then-renewal step appears in Vultr's pricing table. Add-ons, extra IPv4 addresses and outbound overage can raise the bill, so budget the backup fee from day one.

**Can I install Windows?** The documented OS list is Linux and FreeBSD, with one-click stacks for WordPress, LEMP, Docker and Plesk. If Windows is a hard requirement, confirm it on the plan page before paying.

**Is there a money-back window?** Vultr bills by the hour, so the cheapest trial is a small instance you destroy after testing. If a stated refund period matters to you, confirm it at checkout.

## Choosing

A single low-traffic site or a side project: Regular Performance 1 GB at $5. A business site or an app with a database: High Performance 2 GB at $12. Several sites or sustained CPU load: 4 GB at $20 or $24. Dedicated cores only when shared vCPUs are measurably limiting: VX1 from about $44. And if you want someone else to patch the OS and answer the phone, don't buy a self-managed plan at all; pay for a managed host and keep the extra budget for it.

Two checks before you pay: pick the region closest to your users, since pricing varies slightly by location, and confirm the credit landed in your balance before you deploy.

👉 [Start with Vultr's current plans and the $300 credit](https://bit.ly/VuLtr)
