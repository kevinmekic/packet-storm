# PACKET STORM ⚡

Playable real-time 3D cyber defense game in a **single HTML file** — one-shotted by GPT-5.6 Sol (plus one bug report).

**▶ Play it:** https://kevinmekic.github.io/packet-storm/

Built for [@sama's challenge](https://x.com/sama) — "show me interesting things people have built with 5.6 sol."

## What happens

A ~160-second scripted attack chain against an enterprise network:

1. **SYN flood DDoS** — spoofed half-open sessions fill the firewall state table
2. **Port reconnaissance** — sequential probes enumerate the attack surface
3. **Lateral movement** — patient zero spreads over SMB, RDP and WinRM
4. **Data exfiltration** — an established TLS channel moves data toward C2

## Your job

| Key | Action |
|-----|--------|
| `1` | SYN rate limiting (token bucket, 650 pps / burst 1,100) |
| `2` | Inline IPS |
| `3` | Cut links — traffic reroutes live (real Dijkstra, cache invalidation) |
| `Q` | Quarantine the selected host |

Score = uptime of legitimate services.

## Tech

Single HTML file, no build step. three.js with InstancedMesh packet pools,
UnrealBloom post-processing, fixed-timestep deterministic simulation,
WebAudio. Made by a network engineer — the attacks behave like the real thing.
