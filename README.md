# Experiment 1 – Network Topologies in Cisco Packet Tracer

## Overview
This experiment demonstrates three LAN topologies — Star (Switch), Bus-like (Hub), and Ring-like (Loop with STP) — using Cisco Packet Tracer. Students configure IPv4 addressing and verify connectivity using ICMP ping.

---

## Files Included

| File | Description |
|------|-------------|
| `exp1_topologies.pkt` | Cisco Packet Tracer project file with all 4 tasks |
| `output_exp1.txt` | Ping results and topology observations |
| `report_exp1.pdf` | Full lab report with diagrams and conclusions |
| `README.md` | This file — setup and testing guide |

---

## Requirements

- **Cisco Packet Tracer** version 7.x or later (8.x recommended)
- Download free from: [Cisco NetAcad](https://www.netacad.com/courses/packet-tracer)

---

## How to Open the File

1. Install and launch **Cisco Packet Tracer**
2. Click **File → Open**
3. Navigate to and select `exp1_topologies.pkt`
4. The file contains **4 labeled workspaces / topology areas**

---

## Topology Layout in the .pkt File

| Area | Task | Description |
|------|------|-------------|
| Top-Left | Task 1 | Star Topology — 1 Switch + 4 PCs |
| Top-Right | Task 2 | Bus-like — 1 Hub + 4 PCs |
| Bottom-Left | Task 3 | Ring-like — 3 Switches + 6 PCs |
| Bottom-Right | Task 4 | Ring with one disconnected link (Failure Test) |

---

## IP Addressing Scheme

### Tasks 1 & 2 (Star / Hub)
| Device | IP Address | Subnet Mask |
|--------|------------|-------------|
| PC1 | 192.168.10.1 | 255.255.255.0 |
| PC2 | 192.168.10.2 | 255.255.255.0 |
| PC3 | 192.168.10.3 | 255.255.255.0 |
| PC4 | 192.168.10.4 | 255.255.255.0 |

### Task 3 & 4 (Ring)
| Device | IP Address | Subnet Mask |
|--------|------------|-------------|
| PC1 | 192.168.10.1 | 255.255.255.0 |
| PC2 | 192.168.10.2 | 255.255.255.0 |
| PC3 | 192.168.10.3 | 255.255.255.0 |
| PC4 | 192.168.10.4 | 255.255.255.0 |
| PC5 | 192.168.10.5 | 255.255.255.0 |
| PC6 | 192.168.10.6 | 255.255.255.0 |

---

## How to Test Connectivity

### Method 1 — Realtime Mode (Quick Test)
1. Click any PC → **Desktop tab** → **Command Prompt**
2. Type: `ping 192.168.10.X` (replace X with target PC's last octet)
3. Observe replies — 0% loss = success

### Method 2 — Simulation Mode (Detailed Packet View)
1. Switch to **Simulation Mode** (bottom-right clock icon)
2. Add a **Simple PDU** (envelope icon) from source to destination PC
3. Click **Play** or **Capture/Forward**
4. Watch packet path in the event list

---

## Testing Each Task

### Task 1 — Star Topology
- Open PC1 → Command Prompt
- Run: `ping 192.168.10.2`, `ping 192.168.10.3`, `ping 192.168.10.4`
- Expected: All replies successful

### Task 2 — Hub Topology
- Repeat pings as Task 1
- Switch to Simulation Mode — observe that frames are flooded to ALL ports
- Note slightly higher latency vs switch

### Task 3 — Ring Topology
- Wait ~30 seconds for STP to converge (port LEDs turn green)
- Ping across switches: PC1 → PC3, PC1 → PC5, PC3 → PC6
- Expected: All successful after convergence

### Task 4 — Failure Test
- In the ring topology area, click the cable between Switch A and Switch B
- Press **Delete** to disconnect the link
- Immediately ping PC1 → PC3 — expect timeout during STP reconvergence
- After ~30–50 seconds, pings should resume via alternate path
- Note the automatic failover behavior

---

## Common Issues & Fixes

| Problem | Solution |
|---------|----------|
| Ping fails in Task 1/2 | Check IP addresses match the scheme above |
| Ring pings fail after opening | Wait 30 seconds for STP to converge |
| Hub shows no broadcast flooding | Switch to Simulation Mode to see it |
| Task 4 never recovers | Ensure all 3 switch-to-switch links were present before deleting one |

---

## Notes
- Subnet used: `192.168.10.0/24` across all tasks
- Default Gateway is not required (all devices in same subnet)
- STP is enabled by default on all Cisco 2960 switches in Packet Tracer
- Hub does not support STP — no loop prevention (do not create loops with hubs)

---

*Experiment 1 | Computer Networks Lab*
