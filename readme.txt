# 🔧 Home Network Router Optimization

## Overview
End-to-end optimization of a JioFibre home network for competitive gaming 
(CS2 + Valorant). Documented with real baseline and post-optimization metrics.

## Hardware
- ISP Router : Jio JHS D200 v2 (ONT)
- Secondary  : Tenda F3 Wireless N300
- Gaming PC  : Windows 11, Ethernet
- Test Device: MacBook (Wi-Fi)

## Tools Used
- iperf3, ping, nslookup, tracert
- Waveform Bufferbloat Test
- TCP Optimizer (SpeedGuide)
- Windows Registry (QoS DSCP)
- Wireshark (standby)

## Key Results
| Metric              | Before   | After    | Delta        |
|---------------------|----------|----------|--------------|
| Google Max Spike    | 228ms    | 36ms     | -192ms       |
| Idle Latency        | 3.95ms   | 2.78ms   | -30%         |
| Download Bufferbloat| +41ms    | +34ms    | -17%         |
| Packet Loss         | 0%       | 0%       | Perfect      |
| DNS Provider        | Jio ISP  | Cloudflare 1.1.1.1 | 9x faster |

## What Was Done
- Cloudflare DNS (1.1.1.1) configured at adapter level (IPv4 + IPv6)
- Static IP locked at 192.168.29.183 via Windows adapter
- MTU verified at 1500 (optimal, no change needed)
- QoS DSCP 46 (Expedited Forwarding) set for CS2 + Valorant via Registry
- TCP stack tuned via TCP Optimizer (Auto-Tuning: Restricted, CTCP)

## Limitations Encountered
- Jio ONT is ISP-locked — no custom firmware possible
- Tenda F3 insufficient flash memory for DD-WRT/OpenWrt
- Port forwarding blocked by ISP (no custom service option)
- SQM requires OpenWrt — hardware upgrade needed for Grade A

## Upgrade Path
TP-Link Archer AX55 or Asus RT-AX58U (~Rs. 4000-5000)
→ OpenWrt support → SQM → Bufferbloat Grade A → Gaming PASS

## Author
Soumya Khaskel | MCA Cybersecurity | LPU | 28-03-2026