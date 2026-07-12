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

## The prompt

<details>
<summary>Click to expand the original prompt</summary>

```
Use your parallel agents and split the work: one agent owns the three.js 
engine & rendering, one owns the network/attack simulation logic, one owns 
UI/HUD & interactions, one does final integration, performance and visual 
polish.

Build a single self-contained HTML file (three.js from CDN, no build step) 
called "PACKET STORM" — a playable, cinematic 3D cyber-defense game where 
an enterprise network comes under live attack.

THE NETWORK: stylized 3D topology on a dark grid — internet edge, border 
router, zone-based firewall (security zones rendered as translucent colored 
volumes: outside / dmz / inside), core and access switches, server racks, 
clients. Legitimate traffic flows as calm cyan packet orbs with technically 
correct behavior (TCP 3-way handshakes as triple pulses, DNS lookups, TLS).

THE ATTACK — escalating waves, technically accurate:
1) SYN flood DDoS: swarms of red packets hammering the edge, connection 
   tables filling up shown as live gauges
2) Port scan: a probing sweep lighting up services one by one
3) Lateral movement: one compromised client infecting neighbors, spreading 
   through the inside zone
4) Data exfiltration: gold packets trying to sneak out past the firewall

THE DEFENSE — player actions: enable rate limiting on the firewall, cut or 
restore links and watch traffic reroute in real time along recomputed paths, 
quarantine infected hosts, activate an IPS that inspects and drops malicious 
packets with satisfying zap effects. Score = uptime of legitimate services. 
HUD shows live pps, blocked/allowed counts, per-service health.

FEEL: dark cyberpunk NOC aesthetic, bloom/glow post-processing, cinematic 
camera with smooth easing plus free orbit, subtle screen shake on big attack 
waves, ambient hum and alert stingers via WebAudio. Smooth 60fps, degrade 
particle counts gracefully under load.

Accuracy matters: attacks, reroutes and mitigations should behave like the 
real thing — this is built by a network engineer. Polish until a screenshot 
looks like a AAA game trailer.
```

**Plus one bug report:** the one-shot had a single undeclared variable 
(`ended`) that threw a ReferenceError in strict mode and prevented the 
simulation from starting. One follow-up prompt describing the bug fixed it.

</details>
