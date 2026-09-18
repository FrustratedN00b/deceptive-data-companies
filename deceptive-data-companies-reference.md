# Deceptive Data Companies — Quick Reference

Printable, scannable overview. For full explanations, sourcing, and
install instructions, see [README.md](README.md).

**38 rules** · Regex format `(\.|^)domain\.com$` · Each rule matches the
domain **and all of its subdomains** · License: [CC0 1.0](LICENSE)

## The Kape Technologies umbrella

| Brand | Note |
|---|---|
| Kape | The umbrella itself: ex-Crossrider, owns the reviewers |
| ExpressVPN | Kape-owned; holiday.com is a sibling Kape brand (eSIM) |
| CyberGhost | Kape-owned; cyberghost.pw = legacy mirror (now dead) |
| Private Internet Access | Kape-owned |
| ZenMate | Kape-owned |
| Intego | Kape-owned (Mac security); umbrella block |
| vpnMentor | Kape-owned review site (ranks Kape products highly) |
| Wizcase | Kape-owned review site |
| Webselenese | Kape's review-site publisher parent (2021 acquisition) |
| Crossrider | Kape's former identity; adware platform origin |
| Holiday.com | Kape's eSIM service (ownership umbrella block) |

## Documented no-logs failures

| Brand | Note |
|---|---|
| HideMyAss / HMA | 2011: logs helped UK police identify LulzSec's Topiary |
| EarthVPN | "no-logs" → logs handed to Dutch police, 2016 arrest |
| PureVPN | "strict no-logs" → FBI connection logs, 2017 case |
| IPVanish | "no-logs" → logs handed to DHS, 2016 |

## Data harvesting / deception

| Brand | Note |
|---|---|
| Avast | Jumpshot scandal: sold users' browsing histories (2020) |
| AVG | Avast sibling, same Gen Digital parent |
| CCleaner | Avast-owned Piriform; 2017 supply-chain attack, 2.27M PCs |
| Norton | Gen Digital layer (Avast merged with NortonLifeLock 2022) |
| LifeLock | 2010 FTC settlement; ~$100M contempt judgment 2015 |
| Hola | Sold users' idle bandwidth as residential proxy network |
| Holavpn | Hola family |
| Onavo | Facebook "VPN" = data-collection tool; pulled by Apple |
| Opera Proxy | Browser proxy marketed as VPN |
| Hotspot Shield | 2017 FTC complaint: traffic interception for ad targeting |
| AnchorFree | Ex-owner of Hotspot Shield; FTC complaint 2017 (CDT) |
| Aura | Bought Pango 2020; owns Hotspot Shield/Betternet/TouchVPN |
| Betternet | Aura/Pango lineage; privacy marketing, data harvesting |
| TouchVPN | Aura/Pango lineage |
| Hoxx | Free proxy "VPN"; flagged by independent reviewers |
| TotalAV | Comparitech-documented hard-to-cancel renewal funnel |
| ScanGuard | Scareware tier (TotalAV family) |
| PCProtect | Scareware tier (TotalAV family) |

## Regex rules (copy-paste ready)

```
(\.|^)anchorfree.com$
(\.|^)aura.com$
(\.|^)avast.com$
(\.|^)avg.com$
(\.|^)betternet.co$
(\.|^)betternet.com$
(\.|^)ccleaner.com$
(\.|^)crossrider.com$
(\.|^)cyberghost.pw$
(\.|^)cyberghostvpn.com$
(\.|^)earthvpn.com$
(\.|^)expressvpn.com$
(\.|^)hidemyass.com$
(\.|^)hma.com$
(\.|^)hola.org$
(\.|^)holavpn.com$
(\.|^)holiday.com$
(\.|^)hotspotshield.com$
(\.|^)hoxx.com$
(\.|^)intego.com$
(\.|^)ipvanish.com$
(\.|^)kape.com$
(\.|^)lifelock.com$
(\.|^)norton.com$
(\.|^)onavo.com$
(\.|^)opera-proxy.net$
(\.|^)pcprotect.com$
(\.|^)piavpn.com$
(\.|^)privateinternetaccess.com$
(\.|^)purevpn.com$
(\.|^)scanguard.com$
(\.|^)totalav.com$
(\.|^)touchvpn.net$
(\.|^)vpnmentor.com$
(\.|^)webselenese.com$
(\.|^)wizcase.com$
(\.|^)zenmate.com$
(\.|^)zenmate.io$
```

> **Note:** in this markdown file the dots in domains are not
> backslash-escaped (markdown readability). The authoritative
> `deceptive-data-companies.regex` file has the escaped form
> `(\.|^)domain\.com$` — always load rules from that file.

## Know what you're blocking

The avast.com / avg.com / ccleaner.com / norton.com / lifelock.com rules
stop those products' updates and telemetry. Windows and macOS keep
working (Defender / XProtect). Remove those products before enabling, or
exempt their domains locally if you keep them.
