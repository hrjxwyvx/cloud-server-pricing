# Inexpensive cloud servers: is $3/month enough, what do IPv4 and transfer overage add, and which plan actually fits? (full plan table)

A usable Linux VPS now starts around $3–$4 a month. Cloudzy lists 1 GB RAM, 1 vCPU and 25 GB NVMe at $3.48/mo against a $6.95 list price, and UpCloud's Starter tier opens at €3/mo for 1 GB. Those are the numbers to beat. Two other numbers decide what you actually pay: the price after the promo ends, and whether a second IPv4 or an extra terabyte of transfer gets billed on top.

SpinServers sits in a different spot in that market. Its smallest KVM configuration is 2 vCPU, 2 GB RAM, 40 GB RAID-10 SSD and 4 TB of monthly transfer on a 1 Gbps port, with IPv4 and IPv6 included. That is a bigger machine and far more transfer than a $3 sandbox, which makes it the tier to look at when your bottleneck is bandwidth rather than RAM. Below are the KVM configurations published on SpinServers' VPS page, the verified entry prices from the rest of the market, and the line items that decide what the plan costs in year two.

> **Short answer if you're in a hurry**
> - **Single site, bot, monitoring agent, VPN hop, small API:** 1 GB is enough. Cloudzy's $3.48/mo tier and UpCloud Starter at €3/mo are the benchmarks.
> - **2+ vCPU, several TB of transfer, a real 1 Gbps port:** SpinServers' entry KVM tier ships 2 vCPU / 2 GB / 40 GB SSD / 4 TB with IPv4 and IPv6 included.
> - **MySQL, PHP and Redis on one box:** skip 1 GB. Go to 2 vCPU / 4 GB, which is $14.48/mo on Cloudzy's promo or €12/mo on UpCloud Starter.
>
> 👉 [Check SpinServers' current KVM specifications and live prices](https://bit.ly/Spinservers)

## SpinServers KVM VPS plans, tier by tier

The KVM line splits into Simple Application Servers (2 to 8 vCPU) and Advanced Application Servers (12 to 32 vCPU). Every configuration lists Intel Xeon cores, DDR4 memory, RAID-10 SSD storage, a 1 Gbps network port, one IPv4 and one IPv6 address. Monthly transfer runs from 4 TB to 20 TB.

| KVM plan | vCPU / RAM | RAID-10 SSD | Transfer @ port | Price |
| --- | --- | --- | --- | --- |
| Simple Application Server | 2 vCPU / 2 GB DDR4 | 40 GB | 4 TB @ 1 Gbps | [ Live price](https://bit.ly/Spinservers) |
| Simple Application Server | 6 vCPU / 8 GB DDR4 | 120 GB | 8 TB @ 1 Gbps | [ Live price](https://bit.ly/Spinservers) |
| Simple Application Server | 8 vCPU / 8 GB DDR4 | 160 GB | 10 TB @ 1 Gbps | [ Live price](https://bit.ly/Spinservers) |
| Advanced Application Server | 12 vCPU / 12 GB DDR4 | 160 GB | 10 TB @ 1 Gbps | [ Live price](https://bit.ly/Spinservers) |
| Advanced Application Server (Xeon) | 16 vCPU / 16 GB DDR4 | 320 GB | 15 TB @ 1 Gbps | [ Live price](https://bit.ly/Spinservers) |
| Advanced Application Server (Xeon) | 32 vCPU / 32 GB DDR4 | 500 GB | 20 TB @ 1 Gbps | [ Live price](https://bit.ly/Spinservers) |

The published spec sheet lists hardware and transfer without a fixed list price beside each tier, so the price column goes to the live figure instead of a number that may already be out of date. Billing terms and any current promotion get confirmed at checkout.

Two things stand out in that list. There is no 1 GB tier: the floor is 2 vCPU / 2 GB / 40 GB, so a workload that fits comfortably in 1 GB lands on a larger machine than it needs. At the other end, 32 vCPU with 32 GB and 20 TB of transfer is a lot of VPS for a single instance, and it is the configuration that makes the Advanced tier worth a look for consolidating several small servers.

One limitation applies to every VPS in the lineup: port 25 is closed by default to prevent IP abuse. Reopening it requires a support ticket with a justification, and SpinServers reserves the right to refuse. If your plans involve sending mail directly from the instance, whether a newsletter, app notifications or a full mail server, budget for an SMTP relay or choose a host that permits outbound SMTP.

SpinServers also runs a bare-metal line in Dallas and San Jose. A 2026 third-party review of that line lists entry dedicated hardware at $79/month for 4 cores, 32 GB RAM, 1 TB NVMe and 30 TB of transfer on 2×10Gbps ports, with Linux, Windows and ESXi auto-install plus IPMI or iKVM remote management. That is the price band to jump to only if shared virtualisation stops being enough.

## What inexpensive cloud servers actually charge at the entry tier

| Provider / plan | vCPU / RAM / disk | Transfer | Price | Included |
| --- | --- | --- | --- | --- |
| Cloudzy 1 GB | 1 vCPU / 1 GB / 25 GB NVMe | 1 TB @ 40 Gbps | $3.48/mo (list $6.95) | IPv4 + IPv6, 14-day refund |
| Cloudzy 4 GB | 2 vCPU / 4 GB / 120 GB NVMe | 5 TB @ 40 Gbps | $14.48/mo (list $28.95) | IPv4 + IPv6, 14-day refund |
| UpCloud Starter 1 GB | 1 core / 1 GB / 10 GB SSD | 250 Mbit/s port | €3/mo | IPv4, 99.99% SLA |
| UpCloud Starter 4 GB | 2 cores / 4 GB / 30 GB SSD | 500 Mbit/s port | €12/mo | IPv4, 99.99% SLA |
| SpinServers entry KVM | 2 vCPU / 2 GB / 40 GB SSD | 4 TB @ 1 Gbps | live price | IPv4 + IPv6, RAID-10 |

Cloudzy's figures are a 50% promo against the crossed-out list price; UpCloud prices in euro and Cloudzy in dollars, so convert before comparing. Cloudzy's smallest tier, 512 MB at $2.48/mo on promo, is cheaper still but too tight for anything with a database attached.

Transfer is where SpinServers separates from the $3 pack. Four terabytes on the smallest tier against 1 TB on Cloudzy's 1 GB plan, and a gigabit port against UpCloud Starter's 250 Mbit/s ceiling. For offsite backups, container image pulls, log shipping or a media mirror, the allowance and port speed matter more than an extra gigabyte of RAM.

The disk type is a genuine trade-off. RAID-10 SSD gives you mirroring inside the plan; NVMe wins on random read/write IOPS. For a database with heavy random access, the NVMe tiers are the fair comparison. For a workload that mostly streams data or needs redundancy at the storage layer, RAID-10 is the more useful default.

## Is a $3 plan enough for real work?

Yes for a single WordPress or static site behind a cache, a Discord or Telegram bot, a WireGuard or SSH jump host, uptime monitoring, a small API serving a few requests per second, or a CI runner that spends most of its time waiting.

No for MySQL, PHP and Redis on one box (the MySQL buffer pool alone fights the operating system for memory), a JVM application, Docker with three or more containers, or build jobs where `npm install`, `composer update` or `pip` spike memory and get OOM-killed halfway through.

A rough allocation: 1 GB handles a process, 2 GB handles a process with a database, 4 GB handles a database plus a cache plus a web server. When transfer rather than RAM is the constraint, the SpinServers entry tier's 4 TB at 1 Gbps covers most of the cases where a 1 TB allowance needs watching.

## What the plan costs in month 13

Cloudzy's prices carry a 50% discount across the board: $3.48 now against $6.95 list, $14.48 now against $28.95 list. Annual billing is a 50% discount on the monthly equivalent, paid 12 months upfront, and it does not auto-renew: the invoice arrives before renewal so you can downgrade, upgrade or cancel. A year on the 1 GB tier therefore costs roughly the promo rate times twelve, and the risk sits at renewal rather than inside the term.

UpCloud has announced price changes to previous Cloud Server plans, Standard and Archive block storage, and Windows Server licences, effective 16 November. The new Starter plans replace the current Developer plans at roughly 25% less on average with the same 99.99% SLA. If you are holding a quote from earlier in the month, check which side of that date it falls on before comparing.

For a market-wide sanity check: a 2024 comparison put basic virtual servers at about $4/mo at the low end, with Kamatera from $4/mo per vCPU, DreamHost at $4.50/mo for 1 vCPU / 1 GB / 100 GB SSD, Hostwinds at $4.99/mo and Hostinger at $8.99/mo for 2 vCPU / 3 GB / 200 GB NVMe. Two years on, the floor has not moved much, which is why almost every cheap cloud server list starts in the same $3–$4 band.

## IPv4 and transfer: the two line items that move the total

UpCloud charges €3.47/mo for an additional public IPv4 address and €3.47/mo for a floating IP. On a €3 Starter plan, a second IP costs more than the server itself. Public IPv6, private IPv4, SDN networking and the firewall are €0.00, and transfer is €0.00/GiB in both directions.

Cloudzy includes IPv4 and IPv6 on every tier and charges $2.50/mo for a floating IP. Transfer is metered against the plan allowance, and passing the allowance produces a notice rather than a charge or a throttle, so a heavy month does not generate a surprise invoice. The allowance is still a real ceiling to watch.

SpinServers lists one IPv4 and one IPv6 on every KVM tier plus 4–20 TB of monthly transfer at 1 Gbps. If your setup needs a second public address (a separate mail gateway, another TLS endpoint, a VPN with its own IP), ask before ordering. Elsewhere in this market that single line item can rival the plan price.

## Does shutting the server down stop the bill?

Usually not. UpCloud's Starter and Premium plans bill 24/7/365 until the server is deleted. Only Cloud Native plans are pay-as-you-go and billed while powered on, and even there storage and IPs keep billing because they stay allocated. Cloudzy bills hourly, monthly or annually. With SpinServers, confirm the billing granularity at checkout rather than assuming a stopped instance costs nothing.

In practice, deleting is the only saving you can count on. A powered-off VM normally keeps paying for disk and addresses.

## Refunds, trials, and what to test in week one

Cloudzy offers 14 days money-back, does not require a card to start, applies the same window to annual plans, and holds a 4.5/5 rating across 719 Trustpilot reviews. The one exception in its FAQ is repeated sign-ups to claim refunds. UpCloud runs a 30-day free trial, and Kamatera's trial also runs 30 days with no charge if you cancel.

SpinServers: a 2026 third-party review of its dedicated line notes that month-to-month services generally carry no refund policy. Treat the first month as the trial and test what is expensive to change later: disk throughput under your real workload, whether outbound port 25 matters to you, and latency from your users' region to Dallas or San Jose.

👉 [Start on the smallest SpinServers KVM tier and test it for a month](https://bit.ly/Spinservers)

## Who should skip the cheapest tier

- **You need to attach storage separately.** Cloudzy bundles disk into the instance and does not sell a separate block storage product. UpCloud does: €0.220/GB/month on MaxIOPS, 1 GB to 4 TB per volume, up to 16 volumes and 64 TB, which is the model you want when data has to outlive the server.
- **You need to send mail from the box.** SpinServers closes port 25 by default on every VPS and opens it only by ticket, with the right to refuse. Use a relay or pick a host that allows SMTP.
- **You need Windows.** UpCloud's Windows Server licence pricing changes on 16 November, so price the licence before comparing server costs.
- **You need multi-node object storage.** MinIO in single-node single-drive mode runs on one large instance; distributed mode needs four or more nodes, which changes the cost calculation completely.
- **You need NVMe-grade random IOPS.** SpinServers' KVM tiers are RAID-10 SSD. If the workload is random-read heavy, compare NVMe plans rather than SATA or SAS SSD.

## How to choose

- **Fits in 1 GB, needs one address:** Cloudzy's $3.48/mo tier or UpCloud Starter at €3/mo, both with IPv4 included.
- **Needs 2 GB, several TB of transfer and a gigabit port:** SpinServers' entry KVM tier, priced live.
- **Needs a database plus a web server:** 2 vCPU / 4 GB, at $14.48/mo on Cloudzy's promo or €12/mo on UpCloud Starter.
- **Needs 8+ vCPU with 10–20 TB:** SpinServers' Advanced tiers run to 32 vCPU / 32 GB / 500 GB / 20 TB.
- **Needs bare metal:** SpinServers' dedicated servers in Dallas and San Jose, with entry configurations around $79/mo per that 2026 review.

Two things to confirm before paying: the price once any promotion ends, and whether a second IPv4 or extra transfer bills on top. Everything else can be fixed later by resizing the instance.

👉 [See SpinServers' current KVM configurations and live pricing](https://bit.ly/Spinservers)
