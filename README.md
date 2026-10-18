# windows server hosting: what the Windows Server license really costs, where Vultr fits, and the billing traps to check before you deploy

Type "windows server hosting" into a search bar and you're usually trying to get one of a few things done: run a .NET app or an MSSQL database, hand out remote desktops to a small team, or put a game server online without wrestling with Linux. All of that works. The part the pricing pages don't lead with is the license. IONOS's own numbers make the gap obvious: a dedicated server listed at $41/month becomes roughly $79 once you add the $38 Windows Server license — before that machine serves a single request.

The short version of everything below: if you're comfortable running the box yourself, Vultr is a strong option — it documents Windows Server 2016, 2019, 2022, and 2025 images, adds the license fee to the instance price, and bills by the hour, including on single-tenant bare metal across 32 locations. If you'd rather never open a server admin panel, Liquid Web's managed Windows VPS from $105.50/month is the better call.

> **Quick picks**
>
> - **Self-managed Windows VM or bare metal:** Vultr — hourly billing, Windows Server 2016–2025 images, license added at the instance level.
> - **Managed Windows hosting:** Liquid Web, Windows VPS from **$105.50/month**.
> - **License-included dedicated server:** Contabo, around **$160/month** with Windows Server Standard preinstalled.
>
> Or [👉 see Vultr's Windows Server options and current pricing](https://bit.ly/VulTR).

## Does the price include the Windows license? Usually not

Most Windows hosting prices you see quoted are hardware prices, and the license is a separate line. That's why two providers with similar headline numbers can end up far apart at checkout.

The clearest published example: IONOS lists its entry dedicated server from $41/month, then adds a $38 Windows Server license. HowToHosting's May 2026 price check put the realistic total near $79/month for that machine. IONOS's cloud side is more transparent — Cloud Cube XS starts at $5.76 per 30 days, with Windows licensing at about $5.69 per vCPU per 30 days. Two vCPUs of Windows on that Cube works out to roughly $17 per 30 days, license included in the math.

Kamatera is the classic trap here. The $4/month figure that shows up in half the comparison charts is a bare Linux VM price; CloudsPress's August 2026 guide points out it's not an all-in Windows number, and the license plus add-ons only surface as you configure.

A few providers do fold the license in. Contabo ships dedicated servers with Windows Server Standard preinstalled and no published license add-on — its entry 12-core Ryzen 9 7900 with 64 GB RAM and 1 TB NVMe lands around $160/month (EUR 136.40), and the rate doesn't jump at renewal. ScalaHosting includes the license on its Windows VPS too, at $39.95/month introductory and $44.95/month on renewal. Vultr takes the middle path: the license is added to the instance price, so the checkout figure — not the base plan rate — is the number to compare.

That's the habit worth building for any Windows hosting purchase: compare checkout totals, then check whether the renewal rate differs from the promo.

## What Vultr actually offers for Windows Server

Vultr runs Windows two ways: as documented images on its self-managed cloud VMs, and on single-tenant bare metal servers. The image list covers Windows Server 2016, 2019, 2022, and 2025 — and that last one matters. ScalaHosting's Windows VPS page, for comparison, still tops out at Windows Server 2022, so if running the current release is the point, Vultr's documented list already includes it.

The bare metal line is built on AMD EPYC processors with NVMe storage behind a 25 Gbps network, deployable across 32 locations with on-demand provisioning and hourly billing. HostAdvice's October 2026 roundup of Windows dedicated server providers lists the line at three price points:

| Plan | CPU | RAM | Storage | Listed price |  |
| --- | --- | --- | --- | --- | --- |
| Bare Metal (Ryzen) | 12 cores × 3.7 GHz | 64 GB | 1 TB | $161.10/mo | [ Deploy this plan](https://bit.ly/VulTR) |
| Bare Metal (EPYC Genoa) | 24 cores × 2.5 GHz | 128 GB | 2 TB | $215.10/mo | [ Deploy this plan](https://bit.ly/VulTR) |
| Bare Metal (EPYC Turin) | 32 cores × 3.55 GHz | 128 GB | 2 TB | $431.10/mo | [ Deploy this plan](https://bit.ly/VulTR) |

Hourly billing means the monthly figure is what you'd pay running the machine full-time; shorter-lived projects cost proportionally less. The Windows images aren't reserved for bare metal either — the same documented versions deploy onto regular cloud VMs at VPS-level pricing, with the license added per instance.

If you've outgrown a single VM — a Hyper-V host that needs to carve one machine into several Windows roles, or an MSSQL workload that wants dedicated cores — bare metal is the tier that fits. [👉 Compare Vultr's bare metal and cloud plans](https://bit.ly/VulTR) before deciding which side of that line you're on.

## Two billing traps to know before you deploy on Vultr

Two documented quirks are worth knowing before the first deploy, and neither shows up in the plan comparison tables.

**Stopped instances keep billing.** Shutting down a Vultr VM doesn't pause the charge. The instance keeps costing money until you actually destroy it, and because the Windows license rides on the instance price, an idle stopped Windows box costs more per hour than a stopped Linux one. If you're spinning up a short-lived test environment, make the destroy step part of the project, not an afterthought.

**Custom Windows ISOs aren't supported.** Deployment runs through Vultr's documented images (2016–2025). If your plan involved mounting your own ISO or a specific build, that path doesn't exist here. Most people won't care; a few will care a lot, and it's cheaper to find out now.

Neither quirk is a dealbreaker for the typical Windows workload. They're the kind of details that turn a "cheap test server" into a line item you forgot about, though. [👉 Set up a Windows Server instance on Vultr](https://bit.ly/VulTR) once you've factored both in.

## How Vultr stacks up against the other Windows hosts

Short answer: Vultr's edge is hourly flexibility, current Windows versions, and automation-friendly provisioning, while competitors clearly win on managed service, absolute cheapest entry, and license-included dedicated hardware.

| Provider | Product type | Windows licensing | Verified entry price | Stands out for |
| --- | --- | --- | --- | --- |
| Vultr | Self-managed cloud VM + bare metal | License added to instance price | Bare metal from $161.10/mo | Hourly billing; WS 2016–2025 images; 32 locations |
| Kamatera | Elastic cloud VM | Added at configuration; the $4 headline is a Linux price | $19/mo (30-day trial, $100 credit) | 19 datacenters; hourly billing |
| IONOS Cloud | Cloud Cube IaaS | ~$5.69 per vCPU per 30 days | Cube XS $5.76/30 days + license | Transparent license math; 99.99% written SLA on dedicated |
| Liquid Web | Managed Windows VPS / cloud | Windows Server 2022 on listed products | VPS from $105.50/mo | Managed service; 59-second response guarantee |
| InterServer | Windows VPS | Confirm image and edition at order | $10/mo (1 core, 4 GB RAM, 80 GB SSD, 4 TB transfer) | Cheapest verified Windows entry |
| ScalaHosting | Windows VPS | WS 2019/2022 Standard included | $39.95 intro / $44.95 renewal | License-included, simple self-managed VPS |
| Contabo | Dedicated server | WS Standard preinstalled; BYOL accepted | ~$160/mo (EUR 136.40) | Most hardware per dollar |

A few honest notes on where the competition genuinely wins. Liquid Web is the pick if you want the vendor handling patching and support — it costs several times what a self-managed VPS does, and that's what the money buys. Contabo's contractual SLA is 95% network uptime, well under the 99.9% its marketing implies and far below IONOS's written 99.99% commitment, so read that twice if a written guarantee matters to you. InterServer's $10 tier is unbeatable on entry price, but it's basic support with you managing the guest OS, and it's built for single-server workloads rather than anything multi-server.

Vultr's slot in that lineup: you administer the machine, the hourly billing and API suit automated or short-lived deployments, and Windows Server 2025 is already documented. If those three things describe how you work, it's the natural fit.

## Matching the workload to the plan

The right product depends on what the server will actually do — the same budget buys very different outcomes depending on the job:

- **Remote desktops for a mobile workforce.** A handful of users fits comfortably on an entry Windows VPS. InterServer's $10/month tier (1 core, 4 GB RAM, 80 GB SSD) handles a small RDP setup, and IONOS's per-vCPU license keeps one- or two-vCPU Cubes cheap as long as you watch the math.
- **.NET app plus MSSQL on IIS.** A mid-size Windows VPS covers most small eCommerce stores. Hand it to Liquid Web if you want patching and backups handled; run ScalaHosting or a Vultr VM yourself if you don't mind being the admin.
- **Hyper-V and multi-role Windows servers.** Exchange, a secondary DNS, mail filtering, a lab of VMs — single-tenant bare metal is where these belong. Vultr's bare metal and Contabo's license-included dedicated are the two verified options in that bracket.
- **Game servers.** Start with the cheapest Windows VPS tier that meets the game's RAM requirement and scale up before you hit the ceiling. Hourly billing on Vultr or Kamatera helps here, since a server for a weekend event doesn't need to run all month.

One provider to skip in 2026: GoDaddy has retired its dedicated servers and is moving existing customers to VPS, so any dedicated Windows offer still floating around there is stale inventory.

## Windows server hosting FAQ

Quick answers to the questions that come up most, with the license and billing caveats baked in.

### Does Vultr's price include the Windows Server license?

No. The license is added to the instance price, so the checkout total is the number to compare — the base plan rate on its own understates the bill.

### Which Windows Server versions can I run on Vultr?

Windows Server 2016, 2019, 2022, and 2025 are all documented images. The 2025 release is included, which several budget Windows VPS providers don't list yet.

### Can I upload my own Windows ISO or bring my own license to Vultr?

Custom Windows ISOs aren't supported, and bring-your-own-license isn't part of Vultr's documented Windows setup — the license is added to the instance price. If applying existing licenses to your own media is central to your plan, Contabo is the provider in this comparison that explicitly accepts BYOL on dedicated servers.

### What's the cheapest way to run Windows Server legally?

A low-spec Windows VPS. The verified floor here is InterServer at $10/month for 1 core, 4 GB RAM, 80 GB SSD, and 4 TB of transfer. Just don't anchor on Linux-style headline prices: Kamatera's well-advertised $4 figure, for instance, is a bare Linux VM, not a Windows all-in.

### Is Windows hosting more expensive than Linux hosting?

Yes, at every tier — the license line is the difference. HowToHosting's comparison describes the Linux dedicated market as a clear step cheaper, and the same pattern holds further down the price ladder.

## Where that leaves you

- Want the vendor to manage everything → Liquid Web's Windows VPS, from $105.50/month.
- Want the cheapest legal Windows box → InterServer's $10/month VPS.
- Want a license-included dedicated server you admin yourself → Contabo, around $160/month.
- Comfortable with a server admin panel and want hourly billing plus Windows Server 2025 → Vultr, and [👉 deploy your Windows Server instance here](https://bit.ly/VulTR).

Two checks before you click buy on any of them: confirm the Windows license line at checkout, because the headline price almost never includes it; and on Vultr specifically, remember that a stopped instance keeps billing until you destroy it — if it's a short-lived test box, put the destroy step in the plan.
