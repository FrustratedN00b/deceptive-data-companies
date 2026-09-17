# Deceptive Data Companies — Blocklist

DNS blocklist targeting companies whose business model is built on
**misleading people in order to collect their data** — currently focused on
the consumer VPN industry and its corporate ownership, including the VPN
review sites owned by the very companies they rank.

This is *not* a "block all VPNs" list. It targets a specific pattern:
products marketed on privacy trust while their operators have documented
histories of deception, undisclosed ownership conflicts, or data harvesting.

## Format

Two files, same 38 domains but **different coverage**:

- **`deceptive-data-companies.regex`** — Pi-hole regex rules. One rule matches
  a domain *and all of its subdomains* (e.g. every VPN gateway under
  `expressvpn.com`). **This is the strongly preferred version** — it is the
  only one that catches subdomains.
- **`deceptive-data-companies.txt`** — plain domains, one per line, for tools
  that don't support regex. **Caution:** Pi-hole adlists match domains
  *exactly*, so this version blocks `expressvpn.com` but **not**
  `www.expressvpn.com` or any VPN gateway subdomain. Use it only if your
  filtering tool cannot handle regex, and prefer the regex file whenever
  possible.

## Install (Pi-hole)

### Regex version (preferred)
1. Pi-hole admin → **Group Management → Regex / Wildcard filters**
2. Paste the contents of `deceptive-data-companies.regex` into the description-free
   regex field (or add rules individually)
3. Optionally assign to a dedicated group so you can toggle it per-client

Or via CLI on the Pi-hole host (Pi-hole v6; verified syntax):
```
while read r; do pihole --regex -q --comment "Deceptive Data Companies" "$r"; done < deceptive-data-companies.regex
```
(Drop `-q` if you want to see each rule echoed as it is added.)

Note: the regex file is a **manual import** — Pi-hole's adlist mechanism
subscribes to URLs only for exact-match domains, so remote regex lists
cannot be auto-synced. Re-run the one-liner after any update to this
repo, or paste the rules in the web UI.

### Domain version (standard adlist)
1. Pi-hole admin → **Group Management → Adlists**
2. Add the raw URL of `deceptive-data-companies.txt` on this repo
3. `pihole -g`

## Why these companies?

### The Kape Technologies umbrella
[kape.com](https://kape.com) (formerly **Crossrider**) owns:
- **ExpressVPN**
- **CyberGhost**
- **Private Internet Access (PIA)**
- **ZenMate**
- **Intego** (Mac security software)
- **Holiday.com** (eSIM travel connectivity, launched by ExpressVPN)

Crossrider's legacy: an app platform whose SDK was widely abused to inject
ads and install adware; Microsoft and others flagged it, and researchers
documented its distribution pipeline delivering unwanted software. That
company rebranded to Kape Technologies and went on to acquire a large
share of the consumer VPN market.

Critically, Kape **also owns vpnMentor.com and Wizcase.com** — two of the
most visible "independent" VPN review sites, which consistently rank
Kape-owned products near the top. Reviewing your own competitors without
disclosure is the definition of misleading consumers. Kape acquired the
review sites' parent publisher, **Webselenese**, in 2021; this list blocks
the corporate parent (`webselenese.com`) as well as both review brands.

### Other operators with documented deception issues
- **HideMyAss / HMA** — the most famous VPN-logs case on record: in 2011,
  HMA handed connection logs to UK law enforcement that helped identify and
  arrest LulzSec member Jake Davis ("Topiary") — despite marketing itself
  as a privacy service. Its own logging policy at the time made the
  betrayal possible.
- **EarthVPN** — advertised a no-logs policy, then in 2016 handed user
  logs to Dutch police in a harassment case, leading to a subscriber's
  arrest. Another "no-logs" claim disproven by a real-world subpoena.
- **Hoxx** — free browser-extension "VPN" that independent reviewers
  (theBestVPN, VPN Critic, PrivacyAffairs, among others) have repeatedly
  flagged for weak or no meaningful encryption and unclear logging
  practices — monetizing a user base that believes it is being protected.
- **Hola (Hola Networks)** — free "VPN" that sells users' idle bandwidth as
  a residential proxy network (Luminati); users' exits were used for
  other people's traffic.
- **Hotspot Shield / TouchVPN / Betternet (Aura, via Pango, ex-AnchorFree)** —
  subject of a 2017 FTC complaint by the Center for Democracy & Technology
  alleging traffic interception and redirection for ad targeting despite
  privacy marketing. Ownership lineage verified: AnchorFree's Pango
  acquired TouchVPN and Betternet; Aura bought Pango in 2020, putting
  Hotspot Shield, Betternet, TouchVPN (and VPN 360) under one roof.
- **Onavo (Facebook/Meta)** — "free VPN" that was a data-collection tool;
  pulled from Apple's App Store for circumventing its data policies.
- **IPVanish (Ziff Davis, ex-Highwinds/StackPath)** — claimed to keep no
  logs, then handed logs to the U.S. Department of Homeland Security in a
  2016 case.
- **Opera Proxy (Opera, owned by a Chinese consortium)** — built-in
  "browser VPN" that routes traffic through Opera servers; marketing
  obscures that it is a browser-scoped proxy with full traffic visibility.
- **Avast / AVG (now Gen Digital)** — the 2019–2020 **Jumpshot scandal**
  (PCMag, Motherboard/Vice): Avast's antivirus collected users' complete
  browsing histories — including visits to corporate, medical, and adult
  sites — and sold that data through its Jumpshot subsidiary to Google,
  Microsoft, Yelp, Home Depot, and others. The product whose entire pitch
  was "protection" was the data collection tool. Jumpshot was shut down
  after exposure. Also of note: Avast-owned Piriform's CCleaner was
  compromised in a 2017 supply-chain attack that pushed malware to 2.27M
  machines. Avast merged with NortonLifeLock in 2022 to form **Gen
  Digital**; this list therefore covers the parent and its consumer
  brands: **avast.com, avg.com, ccleaner.com, norton.com, lifelock.com**.
  (Norton itself carries a separate record: LifeLock paid a 2010 FTC
  settlement, then a ~$100M contempt judgment in 2015 for failing to fix
  the advertising practices that settlement covered.)
- **PureVPN** — advertised a strict no-logs policy, then handed FBI
  connection logs to a 2017 cyberstalking case; the discrepancy between
  its marketing and its actual logging is on the court record.
- **TotalAV / ScanGuard / PC Protect** — the fear-marketing tier of
  consumer antivirus. Comparitech's hands-on review documents the
  retention funnel: auto-renewal is on by default, renewal prices jump
  steeply, and users must cancel their entire account to stop recurring
  charges. r/antivirus has a thread literally titled "TotalAV scam," and
  independent testers widely flag this family as the industry's
  scareware tier — aggressive "your PC is infected" funnels backed by
  hard-to-cancel subscriptions.
- **Crossrider** — Kape Technologies' former identity; the adware
  platform documented above. Listed directly so the origin name cannot
  reappear as a "new" brand.

### Covered brands (38 rules)
AnchorFree, Aura (identity-protection parent of Hotspot Shield / TouchVPN /
Betternet), Avast (full parent — Jumpshot), AVG, Betternet, CCleaner,
Crossrider, CyberGhost (including legacy `cyberghost.pw` mirror — currently
unresolving, retained in case the brand reactivates it), EarthVPN,
ExpressVPN, HideMyAss (HMA), Holiday.com (Kape's eSIM service — blocked
under the ownership umbrella; no individual scandal required, same as
Intego), Hola, Hoxx, Hotspot Shield, Intego, IPVanish,
Kape Technologies, LifeLock, Norton, Onavo, Opera Proxy, PC Protect,
Private Internet Access, PureVPN, ScanGuard, TotalAV, TouchVPN, vpnMentor,
Webselenese, Wizcase, ZenMate.

## Know what you're blocking

Blocking `avast.com`, `avg.com`, `ccleaner.com`, `norton.com`, and
`lifelock.com` **stops updates and telemetry for those specific products**.
If you run Avast, AVG, CCleaner, or Norton 360, their definition updates,
cloud lookups, and licence checks will fail while this list is active. The
operating systems themselves are unaffected (Windows ships its own
Defender; macOS ships XProtect), so machines keep working — but decide
consciously: either remove those products before enabling this list, or
exempt their domains locally if you choose to keep them.

## Design decisions

- **Regex, not brute-force host lists.** One rule per domain family. Blocks
  current *and future* subdomains (new VPN gateways, new landing pages)
  with no maintenance.
- **Blocks the corporate layer** (`kape.com`, `vpnmentor.com`, `wizcase.com`,
  `intego.com`), not just the products. No other published list does this.
- **No ad networks, no trackers, no false positives padding.** This list is
  deliberately small and 100% intentional. Every entry is there because of
  the ownership/deception pattern, not because a VPN brand was seen in a
  log file.

## License

[CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/) — public
domain. Use it, fork it, embed it.

## Donations

Donations aren't expected but are appreciated. A bigger "payment" is to
spread the word! Thanks for using my blocklist.

- **Monero (XMR):**
  `8AxzaN48KUxi8UW1HUND2zMQrgZvgxC4BU7rdvDRMAxyeh7yF8wgeM7fy2UPAcKKireGNKAvpYrhBBhGiGW8so1p57F9sQk`
- **Zcash (shielded z-addr only):**
  `u18xy57cmzvgtjw8nrph766zqzpv6khjmemwde4z2j9qerly06aagkull5u097ptr3usa2qfm540820cy9ep5ezpxtt8cgjhn830em7tc8nnrjwryz9kzpdzsumr4eqmwekwww66nmr9m0j8zzkx99gfyyhcl28qwc4t6trswezy8unssl`
