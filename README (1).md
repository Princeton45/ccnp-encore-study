# CCNP ENCOR v1.2 (350-401) — Master Study Guide & Network Engineering Roadmap

> **Mission:** Pass ENCOR while building the design, implementation, verification, troubleshooting, operational, security, and automation skills of an enterprise network engineer. **Blueprint checked:** 2026-11-03. **Exam:** 120 minutes. **Exam version:** v1.2, effective 2026-03-19. **No claimed question count, passing score, or guaranteed lab selection.**
>
> **Source of truth:** [Cisco ENCOR v1.2 blueprint (PDF)](https://learningcontent.cisco.com/documents/marketing/exam-topics/350-401-ENCORE-v1.2.pdf) and [Cisco v1.2 release notes](https://learningcontent.cisco.com/documents/marketing/exam-topics/CCNP_Enterprise_v1.1_and_1.2_Release_Notes.pdf). Check the current blueprint again before booking. Exam domains, exact wording, and weights below follow that blueprint, not anecdotes.

> **Your dated schedule (added):** **Day 1 = Mon 9 Nov 2026 → Exam Day = Fri 16 Jul 2027 (D250).** 36 weeks, ~14 h/week, every day written out in [§13](#13-day-by-day-schedule-d1--d250-exam-day). Main video course: **Arash Deljoo's CCNP ENCOR v1.2 course** (all non-wireless sections mapped in [§12](#12-arash-deljoo-course-map-non-wireless)). Hands-on: **your own labs (Containerlab or CML) + Boson ExSim simulation labs, repeated**. Active recall: **Anki + NotebookLM/Gemini quiz notebooks** ([§11.3](#113-notebooklm--gemini-active-recall-system)). Automation is practised **every single day** from Day 1 ([§11.6](#116-daily-automation-track-python--json--apis)).
>
> **How to use this README:** sections 1–10 are the *what* and the *standards* (blueprint, labs, cards, practice exams, tracking). Sections 11–14 are the *how and when*: open §13 every morning, do that day's line, tick it off.

**Certification context:** Passing ENCOR alone earns the Cisco Certified Specialist – Enterprise Core credential and satisfies the CCNP Enterprise **core** requirement; earning CCNP Enterprise also requires a qualifying concentration exam. This roadmap deliberately focuses only on ENCOR v1.2.

## Contents

1. [Operating principles](#1-operating-principles)
2. [Long-range schedule and milestones](#2-long-range-schedule-and-milestones)
3. [Learning process, lab standards, and Containerlab](#3-learning-process-lab-standards-and-containerlab)
4. [The complete v1.2 blueprint study plan](#4-the-complete-v12-blueprint-study-plan)
   - [1.0 Architecture — 15%](#10-architecture--15)
   - [2.0 Virtualization — 10%](#20-virtualization--10)
   - [3.0 Infrastructure — 30%](#30-infrastructure--30)
   - [4.0 Network Assurance — 10%](#40-network-assurance--10)
   - [5.0 Security — 20%](#50-security--20)
   - [6.0 Automation and Artificial Intelligence — 15%](#60-automation-and-artificial-intelligence--15)
5. [Reproducible lab catalogue](#5-reproducible-lab-catalogue)
6. [Troubleshooting, automation and capstone projects](#6-troubleshooting-automation-and-capstone-projects)
7. [Flashcards and knowledge retention](#7-flashcards-and-knowledge-retention)
8. [Practice exam strategy and exam-day skills](#8-practice-exam-strategy-and-exam-day-skills)
9. [Study tracking and graduation criteria](#9-study-tracking-and-graduation-criteria)
10. [Resources and reference links](#10-resources-and-reference-links)
11. [Study resource stack, NotebookLM, Boson ExSim and the daily template](#11-study-resource-stack-notebooklm-boson-exsim-and-the-daily-template) *(added)*
12. [Arash Deljoo course map (non-wireless)](#12-arash-deljoo-course-map-non-wireless) *(added)*
13. [Day-by-day schedule: D1 → D250 exam day](#13-day-by-day-schedule-d1--d250-exam-day) *(added)*
14. [Exam day and after](#14-exam-day-and-after) *(added)*
15. [Appendix A — Numbers to memorise](#appendix-a--numbers-to-memorise) · [Appendix B — Verified Python & JSON drill bank](#appendix-b--verified-python--json-drill-bank) *(added)*
16. [Original first-14-days sequence (kept for reference)](#first-14-days--concrete-starting-sequence)

---

## 1. Operating principles

### 1.1 What the blueprint actually requires

| Domain | Exam weight | Your preparation allocation (suggested, **not** official) | Primary deliverable |
|---|---:|---:|---|
| 1. Architecture | 15% | 13% | Annotated network designs, comparison tables, QoS packet-traces |
| 2. Virtualization | 10% | 13% | Verified VRFs, GRE/IPsec, underlay/overlay packet traces |
| 3. Infrastructure | 30% | 30% | Repeatable switch/routing/service deployments and fault isolation |
| 4. Network Assurance | 10% | 12% | Telemetry, capture, API, and troubleshooting lab portfolio |
| 5. Security | 20% | 19% | AAA/ACL/CoPP configurations, secure API workflows, threat models |
| 6. Automation & AI | 15% | 13% | Working Python, JSON, EEM, Ansible, REST/NETCONF clients |

The **study allocation** deliberately boosts hands-on virtualization and assurance. Reallocate when your diagnostic scores reveal weaknesses. Some topics such as Python, ACLs, QoS, BGP, and VRF also require earlier prerequisite review.

**Interpret Cisco's verbs correctly:**

- **Configure / verify / construct:** know syntax and workflow from a blank configuration, test both success and failure, save and restore the device. For `construct` code, write working scripts or EEM applets—not just identify keywords.
- **Troubleshoot / diagnose:** interpret running configuration, `show` output, packet captures, counters and logs; isolate the fault, change the smallest possible thing, and prove the fix.
- **Interpret:** read complete configuration and predict what happens to a specific packet, neighbor, request, or event. Do targeted mini-labs, but do not overinvest in platform-specific configuration beyond scope.
- **Explain / describe / compare:** create accurate mental models, contrast terminology and design tradeoffs, and **lab selectively** when a demonstration materially improves understanding. A software-defined controller lab is optional; a Wireshark VXLAN capture or Postman request is highly valuable.

**Critical distinction:** your source Reddit experiences are *anecdotal*. They provide useful priorities (VRF+GRE, OSPF, L2 fixes, BGP, CoPP, NetFlow, SPAN, IP SLA, API debugging and Python), but cannot predict your exam's labs, question mix, sequence or scoring. Cisco's blueprint is authoritative. Never study leaked or recalled live questions.

**v1.2 scope controls:** Dedicated WLAN deployment, RF, roaming and wireless security objectives from older guides are **not** v1.2 objectives. **Do** learn the **fabric WLC** in SD-Access because it appears within the still-listed architecture objective. Do not omit wired QoS: `1.4 Interpret QoS configurations` remains. Understand legacy terms (vBond/vSmart/vManage/DNA Center) **and** current names (SD-WAN Validator/Controller/Manager/Catalyst Center).

### 1.2 Two levels of mastery

**Exam-ready:** explain the objective without notes; interpret realistic configurations; perform required config tasks; spot subtle distractors under time pressure.

**Engineer-ready:** start with a business requirement, write a proposed design and risk assessment, implement, validate with test traffic and operational evidence, inject faults, restore, document rollback, and automate repeatable checks.

**Definition of Done (DoD) for every objective:**
1. Explain the concepts and any tradeoffs in your own words.
2. Answer five new questions or one scenario without notes, including *why* the distractors fail.
3. Where applicable, deploy + verify + break + repair and prove the behavior with evidence.
4. Record a one-page summary and useful CLI/API/packet-trace examples.
5. Revisit after 1, 7, 21 and 45 days; demonstrate retention before marking **Mastered**.

### 1.3 Prerequisite refresh — before starting the blueprint

Budget 1–3 weeks if these are rusty. Do not spend months redoing CCNA: IPv4/VLSM and route summarization; IPv6 addressing, neighbors, RA/NDP, link-local routes; ARP; MAC learning; Ethernet/trunks/VLANs; TCP/UDP/ICMP; default gateway; DNS/DHCP; routing/forwarding table distinction; Linux shell, SSH, Git, Docker, Python venvs, YAML, Wireshark and `tcpdump`. Drill subnetting and exact wildcard masks at speed. The blueprint mentions dual-stack context, so use IPv6 where supported even when an example is IPv4-focused.

---

## 2. Long-range schedule and milestones

**Suggested standard pace:** ~28–36 weeks at 10–14 focused hours/week (roughly 280–500 hours). A shorter or longer schedule is fine. Advancement depends on mastery gates, **not** elapsed weeks. Reserve one day each week for consolidation or rest. Do not try to maintain thousands of low-quality flashcards.

| Phase | Suggested weeks | Focus | Exit gate |
|---|---|---|---|
| 0. Foundation and infrastructure | 1–2 | Baseline diagnostic; Linux/Docker/Git; image licensing; networking and Python refresh | Lab deploy/destroy/redeploy + baseline score recorded |
| 1. Core campus | 3–6 | Trunk, LACP/PAgP, RSTP/MST, guards, VLANs; FHRP | Blind troubleshooting of 6 distinct L2 failures |
| 2. Routing core | 7–12 | OSPFv2/v3, EIGRP concepts, eBGP, route math, NAT/PAT, PBR, multicast | Multi-area OSPF, eBGP and NAT built from blank |
| 3. Virtualization | 13–16 | VRF, GRE and IPsec; LISP/VXLAN; host/virtual switch basics | Explain both tunnel VRFs; prove 3 tunnel variants |
| 4. Assurance + operational security | 17–21 | NetFlow, SPAN family, IP SLA, telemetry, troubleshooting, AAA, ACL, CoPP | Combined network observability/security incident lab |
| 5. Architecture and security design | 22–25 | SD-WAN/SD-Access, QoS interpretation, enterprise design, NGFW, TrustSec, MACsec | Draw diagrams and defend design alternatives |
| 6. Programmability | 26–29 | Python, JSON, YANG, NETCONF, RESTCONF, APIs, EEM, orchestration comparison | Own script+API+EEM lab, including failure cases |
| 7. Integration & readiness | 30–36 | Mixed tasks, scenario exams, targeted remediation, runbooks and capstone | Two clean mocks + blind rebuilds + full blueprint signoff |

**The order is intentionally not sequential by exam domain.** Start a light Python routine during Phase 0 and use it throughout; review QoS and Cisco terminology weekly from Phase 1 onward. If 36 weeks is too long, merge phases; if you need depth, add time to labs and capstones rather than redundant passive videos.

**Weekly pattern (example, ~12 h):** 3 h primary course/reading + primary-source verification; 5 h configuration, packet captures and troubleshooting; 1.5 h Python/API/automation; 1 h flashcard reviews; 1 h recall questions and design explanation; 0.5 h postmortem and planning. Increase programming later; no need to follow exact percentages every week.

**How the dated schedule in §13 implements these phases (added).** The dated plan follows the *teaching order of the Arash Deljoo course* (L2 → routing → tunnels → services → overlays → architecture → assurance → security) so each video builds on the last, but **pulls the automation videos forward to weeks 20–21** and runs a daily automation track from Day 1, because first-hand v1.2 reports stress automation heavily. Every phase gate in the table above is still used, just at the week shown here.

| Phase (table above) | Weeks in §13 | Dates | Exit gate run on |
|---|---|---|---|
| 0. Foundation and infrastructure | W1–W2 | 9–22 Nov 2026 | D14 |
| 1. Core campus (L2; FHRP later in W24) | W3–W8 | 23 Nov 2026–3 Jan 2027 | D56 |
| 2. Routing core (OSPF, EIGRP, eBGP, PBR; NAT/multicast later) | W9–W17 (+W22–W24) | 4 Jan–7 Mar 2027 | D119 (NAT part D167) |
| 3. Virtualization (VRF, GRE, IPsec; LISP/VXLAN in W27) | W18–W19 (+W27) | 8–21 Mar 2027 | D132 |
| 6. Programmability (moved earlier on purpose) | W20–W21 + daily track | 22 Mar–4 Apr 2027 | D147, re-gated D236 |
| 2b. IP services: multicast, NTP/PTP, FHRP, NAT | W22–W24 | 5–25 Apr 2027 | D167 |
| 5a. QoS interpretation | W25–W26 | 26 Apr–9 May 2027 | D181 |
| 3b/5b. LISP, VXLAN, server virtualization, design, SD-Access, SD-WAN | W27–W29 | 10–30 May 2027 | D203 |
| 4. Assurance + operational security | W30–W33 | 31 May–27 Jun 2027 | D231 |
| 7. Integration & readiness | W34–W36 | 28 Jun–16 Jul 2027 | D244 (graduation test §9.4) → **Exam D250** |

**Every four weeks:** redo two older labs from blank; complete a mixed 30–45-question self-test; score a blueprint heat map; update your error log; have a short oral 'teach-back' for the weakest area. Aim for **several months of meaningful practice**, not an arbitrary Reddit completion time.

---

## 3. Learning process, lab standards, and Containerlab

### 3.1 The five-pass approach for each objective

1. **Model:** Read Cisco documentation and a course/book; draw packet flows, dependencies, control/data/management planes.
2. **Build:** Start at a known baseline; configure the minimum viable working topology **without copying a completed config**.
3. **Observe:** `show` and `debug` appropriately, capture traffic, generate test traffic, record expected/actual states.
4. **Break:** Inject at least 2–5 realistic faults; describe symptoms before touching the config; fix minimally.
5. **Automate & teach:** write a verification/backup script where applicable; build scenario flashcards; explain the feature without notes.

Make **expected result** versus **observed result** the core of every exercise. Screenshots of successful pings alone are not sufficient evidence.

### 3.2 Containerlab implementation strategy

Containerlab excels at reproducible topologies, versioned configurations, traffic-generator hosts, telemetry containers and automated validation. It is an orchestration framework, **not** itself a Cisco IOS image and **not** a guarantee of hardware-specific feature fidelity.

- **Fast, free/open dataplane demonstrations:** Linux namespaces/containers, FRRouting (FRR), `iperf3`, Scapy, Wireshark, `tcpdump`, Python, FreeRADIUS/TACACS+ services, syslog/flow collectors. Good for routing, VRF, GRE, BGP, IPv6, packet behavior, APIs and testing; Cisco CLI and feature semantics may differ.
- **Cisco-specific CLI/labs:** use legitimately licensed Cisco virtual platforms that are supported by Containerlab, e.g., Cisco IOL/IOL-L2 or Catalyst 8000V where **license conditions explicitly permit the intended environment**. A platform may not implement all L2 ASIC features, RSPAN/ERSPAN, CoPP, EEM, IP SLA, IPsec or NetFlow in a VM—test availability before committing.
- **Important licensing restriction:** Cisco explicitly states that CML reference-platform VM images are licensed for use **within CML only**, absent a separate applicable license. Do not assume having CML grants the right to extract/repackage them in Containerlab. If those are your available images, run that Cisco CLI lab in **CML** rather than in Containerlab. See [CML image licensing](https://developer.cisco.com/docs/modeling-labs/vm-images-for-cml-labs/) and [Containerlab supported kinds](https://containerlab.dev/manual/kinds/).
- **Controller features:** use approved [Cisco DevNet sandboxes](https://developer.cisco.com/docs/sandbox/) or vendor documentation/UI demos for Catalyst Center/SD-WAN rather than pretending a single container simulates an entire enterprise fabric.
- **Resource budget:** measure RAM/CPU and cold boot time per image. Containerlab documents Cisco IOL as comparatively lightweight, and Catalyst 8000V as heavier. Select image and interface numbering per lab, and **version-pin** the images.

**Before every Cisco-specific lab:** create a feature-support matrix: feature, image/platform, version, command supported?, control plane functional?, data plane functional?, known limitation, fallback. If a feature is unavailable, use an appropriate CML/sandbox image or a standards-based conceptual lab, and log the difference.

### 3.3 Recommended repository layout (architecture only; topology files come later)

```text
encor-engineering/
├── README.md                      # This document
├── 00-foundations/
├── 01-architecture/
├── 02-virtualization/
├── 03-infrastructure/
│   ├── l2/
│   ├── ospf/
│   ├── bgp/
│   └── ip-services/
├── 04-network-assurance/
├── 05-security/
├── 06-automation/
├── 07-integrated-scenarios/
├── 08-mock-exams/                 # Scores and reflections ONLY, not copied exam items
├── flashcards/                    # Your own cards, tagged to blueprint IDs
├── scripts/
└── docs/{diagrams,runbooks,postmortems,glossary}/
```

Each future lab directory should contain `README.md` (business scenario, objectives, assumptions, steps and expected outcomes), topology definition, **clean baseline** config, broken variants, tests, packet captures/screenshots, `solution.md`, and `lessons.md`. **No topology files are supplied now**, as requested.

### 3.4 Gold-standard lab contract

Record these fields for each lab:

```yaml
lab_id: ENCOR-3.2b-OSPF-MULTIAREA
blueprint: [3.2.b]
platforms: [document_actual_image_and_version]
prerequisites: [IPv4/IPv6, OSPF adjacency, VLSM]
scenario: 3 offices with Area 0 and two normal areas
starting_state: initial broken or blank configuration
success_checks:
  - all intended adjacencies reach FULL
  - prefixes and summaries match design exactly
  - traffic follows intended paths, including return path
  - unrelated prefixes remain unreachable
fault_injections: [area mismatch, MTU mismatch, passive-interface, bad summary]
evidence: [show_output, traceroute, pcap, exported_config]
rollback: revert to versioned baseline
estimated_effort: measured after completion
```

**Lab validation tiers:** (A) config parses and feature exists; (B) protocol state correct; (C) data-plane traffic correct *both directions*; (D) failure/recovery behavior as expected; (E) configuration persistence after restart; (F) automation checks pass. Always check **return path**, routing table/VRF, ACLs and counters.

**Golden workflow:** deploy → note baseline state → configure → verify → inject fault → diagnose → repair → save config (`copy running-config startup-config`, when appropriate) → destroy → recreate → run independent tests. Lab persistence is separate from Containerlab startup-config mechanics; do not assume a running configuration automatically becomes the future startup state.

**Useful tooling:** Git and PR-style commits; VS Code; Docker/Containerlab; Python + `pytest`, `requests`, `netmiko`/Scrapli, `ncclient`; Ansible; Postman or Bruno; curl; Wireshark/tcpdump; iperf3; Scapy; an SNMP/syslog/flow collector; and GitHub Actions or local CI for tests. Keep secrets in environment variables/credential stores, never in source control.

---

## 4. The complete v1.2 blueprint study plan

> Each section covers **every listed blueprint item**, plus carefully identified practical extensions. Use the `Know → Do → Prove` format. **Priority labels** are personal study recommendations, not claims about the exam question pool.

### 1.0 Architecture — 15%

#### 1.1 Explain enterprise network design principles

**1.1.a High-level design: 2-tier, 3-tier, fabric, cloud**

- **Know:** access/distribution/core functions; collapsed core vs full three-tier; campus vs WAN vs data center; L2/L3 boundaries; fault domains; routing convergence; failure isolation; scale; ECMP; oversubscription, uplink speed, uplink diversity; north-south vs east-west traffic; underlay vs overlay; cloud VPC/VNet concepts and hybrid connectivity at a *high level*. Explain why business constraints change a topology choice.
- **Do (recommended despite `explain`):** draw the same fictional enterprise as 2-tier, 3-tier and fabric; compare cost, high availability, segmentation, complexity, failure domains and migration risk. Build a tiny routed campus with redundant uplinks and remove a core or aggregation link; time recovery. Map an equivalent cloud hub/spoke concept without pretending the implementations are identical.
- **Prove:** given offices, endpoint counts, uptime targets and failure requirements, choose a design and defend the alternative you rejected. Explain **where** a VLAN ends and **where** first-hop/gateway routing occurs.

**1.1.b Redundancy, FHRP, Stateful Switchover (SSO)**

- **Know:** redundant links/devices/supervisors, failure domains, single points of failure, ECMP/LAG, FHRP virtual IP/MAC and active router, HSRP/VRRP basics, hello/hold and preemption, tracking; **SSO** supervisor-state synchronization versus FHRP gateway redundancy and NS/NSF concepts (support-dependent). Distinguish failover of a control plane from end-host default-gateway failover.
- **Do:** build redundant gateways (ties into 3.3.c), track WAN reachability and force active gateway failure; diagram an SSO chassis event if physical dual-supervisor simulation unavailable.
- **Prove:** predict gateway selection after an interface fails, and explain when active/standby FHRP does *not* protect end-to-end connectivity.

#### 1.2 Explain Cisco Catalyst SD-WAN working principles

**1.2.a Control and data planes; 1.2.b Benefits and limitations**

- **Know current + legacy names:** **SD-WAN Manager** (`vManage`) = centralized management; **SD-WAN Controller** (`vSmart`) = routing/policy control via OMP; **SD-WAN Validator** (`vBond`) = initial validation/orchestration/NAT traversal; **WAN Edge** (`vEdge` or IOS XE-based edge) = data forwarding. Also know transport networks, TLOCs, site ID, system IP, color, OMP routes/TLOC/service routes, transport vs service VPN/VRF, overlay encryption, control connections and common DTLS/TLS/IPsec roles; application-aware routing and SLA-based policies at an architectural level.
- **Do (selective):** draw onboarding from an unconfigured site to a policy-controlled overlay; map flow of a packet from branch A to B; use a controller sandbox or API demo where available; compare dual ISP brownouts with manual BGP routing. Make a one-page matrix of the four planes with device responsibility and failure implications.
- **Tradeoffs:** central policy and application visibility, multi-transport, automation and segmentation vs controller dependency, cost/licensing, overlay and underlay troubleshooting complexity, cloud connectivity and operational migration.
- **Prove:** answer "who authenticates, learns routes, instructs policy and forwards the packet?" with a narrated timeline; distinguish *OMP/control routes* from actual data-plane forwarding.
- **Primary reading:** [Cisco Catalyst SD-WAN Design Guide](https://www.cisco.com/c/en/us/td/docs/solutions/CVD/SDWAN/cisco-sdwan-design-guide.html).

#### 1.3 Explain Cisco SD-Access working principles

**1.3.a Control/data planes; 1.3.b Traditional campus interoperability**

- **Know:** **Catalyst Center** (formerly DNA Center) orchestrates/assures; **LISP** maps endpoint IDs (EIDs) to routing locators (RLOCs) in the control plane; **VXLAN** transports user frames/packets in the data plane; **TrustSec/SGTs** govern policy. Recognize fabric edge, control-plane, border, and **fabric wireless controller** roles; ISE; anycast gateway; underlay/overlay; virtual networks (VN/VRF), SGT policy, transit, extended nodes, external connectivity, L2 vs L3 handoff and migration.
- **LISP role flashcards:** ITR = ingress encapsulation/lookup; ETR = egress decapsulation/registration; xTR = both; MS/MR = map server/resolver; PxTR = proxy ingress/egress; PITR/PETR = proxy ingress/proxy egress. Relate SD-Access fabric roles rather than memorize unrelated acronyms.
- **Do:** draw registration and forwarding from Host A in one fabric edge to Host B on another, and an endpoint going to a *non-fabric* legacy campus or Internet; label each VXLAN encapsulation/decapsulation and policy boundary. For stretch learning, use Linux VXLAN/FRR/EVPN analogues **without claiming EVPN is the SDA LISP control plane**. Observe real WLC/fabric behaviors via vendor design docs or sandbox when available.
- **Prove:** explain where WLC control traffic goes vs where fabric-enabled wireless client data goes, and how fabric border provides legacy interoperation. Be able to distinguish **VN/VRF segmentation** from **SGT-based microsegmentation**.
- **Primary reading:** [Cisco SD-Access Design Guide](https://www.cisco.com/c/en/us/td/docs/solutions/CVD/Campus/cisco-sda-design-guide.html).

#### 1.4 Interpret QoS configurations (priority: high for configuration reasoning)

- **Know:** classification, marking, trust boundaries; DSCP/CoS, IP precedence and PHB/EF/AF/BE; `class-map`, `match-all` / `match-any`, ACL match order, `policy-map`, `service-policy` applied input/output; class-default; queueing, LLQ/priority, bandwidth, WRED, policing vs shaping, bursts/tokens, counters/drops, congestion and direction. CBWFQ vs priority queues, hierarchical QoS, parent/child policies, congestion avoidance versus congestion management. Describe which actions depend on congestion and which are unconditional.
- **Do (recommended even though `interpret`):** annotate full 1-page sample configs with three to four class maps plus ACLs and parent policy; build traffic generators with DSCP marks, packet sizes, bandwidth contention and bursts; inspect class/policy counters and packet capture. Compare shaping and policing with an `iperf3` stream. Hardware queue mechanisms may be unfaithfully simulated—document if you use a model rather than an actual queue dataplane.
- **Prove:** for 20 packet scenarios, identify ACL hit → class selection (including first-match behavior where applicable) → marking → action → whether queued, sent, shaped, or **possibly** dropped, based on congestion and policer state. **Do not claim packet size alone guarantees a drop:** rates, burst tokens, queue occupancy and time matter. Be able to explain why `service-policy` on a different interface/direction changes everything.
- **Critical drills:** DSCP versus L2 CoS; `set dscp`, `police ... conform-action ... exceed-action ...`, `shape average`, `priority`, `bandwidth remaining`; interpreting `show policy-map interface` statistics.

### 2.0 Virtualization — 10%

#### 2.1 Describe device virtualization technologies

**2.1.a Hypervisors type 1/type 2; 2.1.b Virtual machine; 2.1.c Virtual switching**

- **Know:** bare-metal versus hosted hypervisors; CPU/memory/IO scheduling; VM versus container; NIC/vNIC, vSwitch/vDS/bridge, vNIC attachment, port groups, VLAN-tagging, virtual uplinks, host networking, VXLAN overlay at a conceptual level; management/data plane separation; snapshot vs persistent storage; performance and failure tradeoffs; virtualized network function lifecycle.
- **Do (recommended):** deploy two Linux VMs or containers on separate isolated bridges, add tagged interfaces and observe ingress/egress in a pcap. Compare bridge/macvlan/veth behavior, with attention to how Containerlab's management network differs from data links.
- **Prove:** sketch one vSwitch with three VLANs, mark where tags are inserted, and explain why VMs on the same physical host might never traverse a physical switch.

#### 2.2 Configure and verify data path virtualization technologies

**2.2.a VRF (priority: very high)**

- **Know:** multiple independent forwarding/routing tables; VRF-lite, global/default VRF, overlapping IPv4 prefixes, VRF-aware interfaces and static routes, per-VRF OSPF/BGP where supported, route leaking **as an extension**; RD/RT concept boundaries (especially MPLS L3VPN versus VRF-lite); common IPv6 VRF behaviors. Know what happens to an interface IP after changing `vrf forwarding` in IOS XE (can be removed; reapply if necessary).
- **Do:** 2 routers + 2 client VRFs `BLUE` and `RED`, same host subnet in both, two-way reachability only within same VRF; add intentional incorrect static route, interface VRF and next hop, then fix. Probe with `ping vrf`, `traceroute vrf`, `show ip route vrf`, `show vrf` or platform equivalent. Add explicit route leaking as optional engineer extension; verify **no accidental leakage**.
- **Prove:** show independent RIBs/FIBs and why identical prefixes don't conflict. Rebuild VRFs and routes from scratch without notes.

**2.2.b GRE and IPsec tunneling (priority: very high)**

- **Know:** GRE outer/inner packet formats, protocol 47 (GRE, not TCP/UDP port 47), tunnel source/destination and routing resolution, recursive routing failure, MTU/MSS, overhead, GRE does **not** encrypt, IPsec encapsulation/integrity, AH vs ESP, transport vs tunnel modes, IKEv1/v2 conceptual negotiation, SA/lifetimes/crypto maps versus VTI (platform-dependent). Understand transport/underlay reachability first and routing return paths. Distinguish `tunnel vrf` (resolve **outer** source/destination/transport in a given VRF) from `vrf forwarding` on the tunnel interface (**inner** forwarded traffic's VRF).
- **Do in separate progressive labs:** (1) plain GRE over global-table underlay, (2) GRE whose **tunnel interface is in customer VRF** but underlay is global, (3) GRE whose **outer tunnel transport is in a front-door VRF** (`tunnel vrf`) while inside traffic uses a distinct VRF, (4) securely protect GRE or create an IPsec VTI when available; compare captures. Use static routes to carry VRF customer prefixes over the tunnel and perform both-way tests. Break underlay route, overlay route, source, destination, VRF placement and MTU one at a time. Correct interfaces/commands vary by platform and image.
- **Prove:** for any two-VRF tunnel sketch, label underlay RIB, overlay RIB, outer source/destination, inner customer prefixes, and every required static route. Capture an outer GRE packet and explain why inner traffic does not leak in the global table; for IPsec verify encrypted outer traffic and security associations.
- **Primary reference:** [Cisco GRE source/destination VRF membership guide](https://www.cisco.com/c/en/us/td/docs/switches/lan/c9000/lyr3-fwd/gre/gre-configuration-guide/m-gre-tunnel-ip-source-and-destination-vrf-membership.html). **Platform-specific restrictions apply.**

#### 2.3 Describe LISP and VXLAN

**2.3.a LISP; 2.3.b VXLAN**

- **Know LISP:** EID vs RLOC, overlay mapping vs underlay reachability, map-register/request/reply, ITR/ETR/xTR, MS/MR, proxy functions; encapsulation semantics; why identity/location separation improves scalable mobility. Be able to describe a failed map lookup and what data would be missing.
- **Know VXLAN:** VTEP, 24-bit VNI, UDP encapsulation (standard destination port 4789), outer IP/UDP/VXLAN/inner Ethernet, L2 overlay across L3 underlay, broadcast/multicast/unknown unicast at a high level, MTU impact. **Do not confuse a generic EVPN-VXLAN lab with the LISP-based Cisco SDA control plane.**
- **Do (recommended):** create a basic VXLAN Linux or FRR lab across routed underlay, Wireshark an encapsulated frame and identify VNI/outer/inner addresses. Diagram a LISP lookup sequence with synthetic registrations; use Cisco sandbox/docs for exact fabric control-plane behavior.
- **Prove:** compare VRF, VLAN, VXLAN, GRE, LISP, IPsec in a matrix: function, layer, encapsulation, security, control plane and use case.

### 3.0 Infrastructure — 30%

> This is the biggest official domain and the backbone of your configuration speed. These topics should be *practiced in integrated networks*, not only as one-protocol exercises. Always produce before-and-after `show` outputs, connectivity tests, and failure explanations.

#### 3.1 Layer 2

**3.1.a Troubleshoot static and dynamic IEEE 802.1Q trunking protocols**

- **Know:** access vs trunk, tagging, native VLAN handling and mismatch, allowed/active VLAN lists, VLAN database consistency, tagging on the wire, 802.1Q negotiation expectations, DTP `dynamic desirable` versus `dynamic auto` versus fixed trunk, `switchport nonegotiate`, platform restrictions, pruning versus allowed list, L2 security implications (native VLAN and spoofing). Distinguish administrative mode from operational mode.
- **Do:** 3 switches/3 VLANs, one intended trunk. Inject wrong native VLAN, `nonegotiate` mismatch, blocked/missing allowed VLAN, missing VLAN on a switch, erroneous access mode and shutdown member interface. Troubleshoot only via `show interfaces trunk`, `show interfaces switchport`, `show vlan brief`, MAC address tables, and pcap. Confirm that a successful L3 ping may not prove **all** VLANs pass.
- **Prove:** from two conflicting switch configurations, explain which VLANs reach which endpoints and why a specific VLAN has failed. Explain the operational implications of configuring a trunk to a device with DTP disabled.

**3.1.b Troubleshoot static and dynamic EtherChannels (priority: very high)**

- **Know:** LACP `active/passive` vs PAgP `desirable/auto` vs static `on`, port-channel interface and member settings, bundle criteria (speed, duplex, switchport mode, VLAN membership, allowed/native VLAN consistency), suspended/individual members, local vs remote mismatch, hashing/flows, convergence, minimum links, routing versus switching PortChannels. LACP standards-based; PAgP Cisco-specific.
- **Do:** 2 switches, 2–4 parallel links. Configure static, LACP, and PAgP where the image supports them. One side broken: wrong negotiation mode, `on` versus LACP, mismatched access/trunk, one VLAN mismatch, member shutdown or improper PortChannel placement. Inspect `show etherchannel summary`, `show lacp neighbor`, `show interfaces port-channel`, `show run interface ...`, `show interfaces status`, and traffic behavior. **Prevent loops** while practicing mismatched `on` members; enable STP and isolate test network.
- **Prove:** diagnose 10 randomized channel failures in ≤8–10 minutes each, with precise evidence. Explain why one flow doesn't saturate all physical links in a hashed bundle.

**3.1.c Configure and verify RSTP, MST, root guard and BPDU guard**

- **Know:** classic STP vocabulary as a foundation (root bridge, root/designated/alternate ports, priority, path cost, bridge/port IDs); rapid 802.1w roles/states, proposal/agreement, edge ports, link types; Cisco Rapid PVST+ versus MST; MST region name/revision/VLAN mapping and digest/region compatibility; CIST/IST and instances; PortFast/edge, BPDU Guard (err-disable on edge BPDU), Root Guard (root-inconsistent when a superior BPDU arrives), Loop Guard (optional extension, loop-inconsistent); root selection and determinism. Know why different VLAN-to-instance mappings may change forwarding.
- **Do:** 3–4 switches triangle plus dual-host access ports. Deliberately select root and secondary root; verify port roles and transitions. Change costs/priorities and watch blocked path move. Configure two MST instances mapping different VLANs; intentionally mismatch region parameters, introduce rogue root and BPDU on an edge port. Capture BPDUs where possible. Recover disabled/inconsistent ports safely.
- **Prove:** given priorities/MACs/port costs, identify root and port states; implement MST mapping from a written design; distinguish guard trigger and recovery behavior from CLI outputs.

#### 3.2 Layer 3

**3.2.a Compare EIGRP and OSPF concepts**

- **Know EIGRP:** advanced distance vector, DUAL, successor/feasible successor, feasible distance vs reported distance, feasibility condition, passive/active route states, metric components (bandwidth/delay and optional K values), equal/unequal-cost load balancing (`variance`), reliable transport, stuck-in-active at concept level. **Know OSPF:** link-state protocol, areas, LSDB, SPF/Dijkstra, interface cost, router ID, DR/BDR on broadcast, point-to-point behavior, area 0 and ABRs/ASBRs, LSAs at functional level (Type 1/2/3/4/5; Type 7 if studying NSSA), normal/stub/totally stub/NSSA differences as comparison, ECMP, convergence, passive-interface, maximum paths. The v1.2 objective emphasizes comparison; in-depth EIGRP configuration is an **extension**, not the required verb.
- **Do (selective):** create equivalent 4-router OSPF and EIGRP networks, introduce a link failure, examine convergence/state and compare metrics. Compute sample OSPF costs and EIGRP feasible successors by hand; explain unequal-cost multipath restrictions. Include IPv6 considerations.
- **Prove:** build comparison sheets for protocol type, update behavior, path calculation, neighbor/adjacency, area boundaries, metrics, load balancing and troubleshooting symptoms.

**3.2.b Configure simple OSPFv2/v3, multiple normal areas, summarization and filtering (priority: very high)**

- **Know:** OSPFv2 vs OSPFv3 (address families/IPv6 differences depending on Cisco implementation); area 0 backbone, multi-area rules, ABR vs ASBR, intra/inter/external routes, router ID, network statements versus per-interface enablement, authentication at a conceptual/config extension level, DR/BDR election, point-to-point vs broadcast, `passive-interface`, hello/dead timers, MTU, subnet/network-type and area matching, adjacency states (DOWN/INIT/2WAY/EXSTART/EXCHANGE/LOADING/FULL), `show ip ospf neighbor/interface/database/route`, IPv6 OSPF analogues. Understand **where** `area ... range` summarization is performed (ABR for inter-area) versus `summary-address` for redistributed external routes on an ASBR; platform/version differences apply.
- **Do:** at least 5 routers: one backbone, two non-backbone *normal* areas, two loopback networks per remote area; verify all routes and IPv4/IPv6 reachability. Add ABR summaries, then filtering with area range `not-advertise` or supported per-area prefix-list/filter methods, documenting what is filtered and which LSAs/routes remain visible. Build broadcast segment DR/BDR and a point-to-point adjacency. Test passive interfaces. Deliberately inject area mismatch, network-type mismatch, timer mismatch, duplicate router IDs, MTU problem, missing area-0 connectivity, incorrect wildcard, incorrect summary length, passive interface and wrong filter direction.
- **Prove:** starting from blank, establish all intended OSPFv2/v3 neighbors, summarize without blackholing, verify routing tables and LSDB, and explain why a route is missing. Repeat blind (ideally ≤20–30 min for a small topology after mastery).
- **Real-world extension:** BFD, OSPF authentication, route redistribution and stub/NSSA detailed operation, prefix-list and route-map policy; keep advanced redistribution within time budget.

**3.2.c Configure/verify eBGP between directly connected neighbors (priority: very high)**

- **Know:** AS numbers, TCP/179 session establishment, `neighbor remote-as`, directly connected eBGP TTL expectations, source/neighbor addressing, neighbor states Idle/Connect/Active/OpenSent/OpenConfirm/Established, BGP route selection (weight, local preference, locally originated, AS_PATH, origin, MED, eBGP over iBGP, IGP metric, subsequent tiebreakers; carefully note Cisco implementation details and conditions for comparison), `network` advertisement requires an **exact matching prefix in routing table**, RIB install vs BGP table, next-hop reachability, route withdrawal and policy, IPv4/IPv6 address families. Understand aggregation at a conceptual/optional configuration level; actual objective says **directly connected** neighbors, so multihop/iBGP/route reflection are useful extensions, not prerequisites.
- **Do:** 3–4 eBGP ASes in a chain/dual transit; 10–20 loopback prefixes with a carefully made addressing table; configure neighborings, advertise only intended networks, test end-to-end pings and return path, record `show ip bgp summary`, `show bgp ipv4 unicast`, `show ip route bgp`, `show bgp neighbors ... advertised-routes` where supported. Inject wrong AS, missing `network`, absent RIB prefix, wrong IP, disabled neighbor, missing next-hop reachability, filter mistake and duplicate address.
- **Prove:** given neighbor and route outputs, determine **why** a route is not advertised, received, selected or installed. Predict basic best-path outcomes and verify with a CLI experiment. Create a quick VLSM plan under a timer; check summarization and advertisements against the plan.
- **Real-world extension:** route maps, prefix lists, communities, maximum-prefix, BGP session protection, peer groups, path attribute policy, route leak avoidance and change-control risk.

**3.2.d Describe policy-based routing (PBR)**

- **Know:** route-map matching on source/destination, ACL classification, set next-hop/next-hop verify-availability, interface attachment inbound, policy order, PBR vs ordinary destination-based FIB lookup, control-plane versus local packet considerations, operational limitations/blackholing and QoS interaction. `set ip next-hop` semantics are image/version dependent in special cases.
- **Do (recommended):** two ISP paths, select traffic from one source subnet to the secondary ISP while default remains primary; disable secondary and inspect whether policy falls back as intended. Distinguish PBR from firewall policy and static routes.
- **Prove:** interpret a route-map + ACL + routing table to determine path of a given packet, including no-match cases.

#### 3.3 IP Services

**3.3.a Interpret NTP and PTP configurations**

- **Know NTP:** time source, stratum, server/peer/client, association state, clock synchronization versus time zone, authentication/access control, reachability, drift and syslog/AAA relevance. **PTP:** grandmaster, clock roles, boundary/transparent clocks, hardware timestamping, precision tradeoffs, when sub-millisecond accuracy matters; distinguish from NTP's general time-sync purpose. Know `show ntp associations/status` and how to read configured servers, reachability, and selection.
- **Do (recommended):** Linux NTP/chrony server + two routers/hosts, disable UDP/123 and diagnose drift/association; interpret sample PTP config and packet structure or observe a Linux `ptp4l` demo if hardware permits. Avoid assuming simulation accurately models nanosecond precision.
- **Prove:** identify upstream time source, whether time is synchronized, and which components require precise event order.

**3.3.b Configure NAT/PAT**

- **Know:** inside local/global and outside local/global terminology; static NAT, dynamic NAT with pool, PAT overload with interface or pool, `ip nat inside/outside`, matching ACL, NAT translation table and timeouts; source NAT vs destination NAT at a conceptual level, route/NAT processing and return reachability, order of operations at a high level; IPv4 exhaustion; NAT isn't a firewall. IPv6 typically uses routing rather than NAT66—do not overfocus on NAT66.
- **Do:** clients behind inside interface, external servers, PAT overload and static publication; clear/inspect NAT translations, confirm external source mapping. Break inside/outside interface assignment, ACL wildcard, pool/netmask, default route, port mapping and state exhaustion; prove with captures on both sides.
- **Prove:** interpret `show ip nat translations/statistics`; make all private hosts work outbound while allowing only the explicitly designed inbound service.

**3.3.c Configure FHRP: HSRP and VRRP**

- **Know:** virtual IP/MAC, priority, active/standby (HSRP) vs master/backup (VRRP), default preemption behavior **differs** across protocols and platform versions, timers, interface/object tracking and priority decrement, active-gateway selection, version distinctions where relevant, Layer 2 MAC movement, host ARP implications.
- **Do:** two redundant routed gateways, end-host VLAN, uplink track and different priorities. Compare HSRP with VRRP, force primary gateway and uplink failures, test forward and return connectivity and recovery. Look at `show standby brief` / `show vrrp brief` and packet loss with continuous ping.
- **Prove:** predict which router forwards after each 3-step sequence (interface down, priority change, preemption), support answer with state outputs, and document whether convergence meets your target.

**3.3.d Describe multicast: RPF, PIM SM, IGMPv2/v3, SSM, bidir, MSDP**

- **Know:** multicast group addresses and source; forwarding tree vs unicast routing, RPF lookup and wrong incoming-interface drop; IGMPv2 group membership vs IGMPv3 (source-specific INCLUDE/EXCLUDE); PIM sparse mode, RP, shared tree (*,G) and source tree (S,G); SSM (source,group) without traditional RP, usual IPv4 SSM 232/8 context; bidirectional PIM shared-tree use; MSDP historically shares source information between RPs in separate domains. Compare *purpose* and operational boundary, not obscure commands.
- **Do (recommended):** FRR/Linux multicast sender/receiver through two routers with PIM/IGMP support confirmed; join group, inspect state and capture reports. Deliberately break RPF; contrast ASM and SSM traffic at conceptual/mini-lab level. If platform lacks bidir/MSDP, diagram packet and control state rather than faking full implementations.
- **Prove:** from source, group, RP and unicast RIB, identify expected RPF interface and explain why multicast fails even while unicast ping works.

### 4.0 Network Assurance — 10%

> Treat assurance as daily practice throughout the entire roadmap. Every packet capture and every counter you collect reinforces this domain.

#### 4.1 Diagnose problems with debug, conditional debug, traceroute, ping, SNMP and syslog

- **Know:** systematic methodology (scope → physical/link → L3 route/VRF → control plane → policy/NAT → application); extended ping/traceroute with VRF/source; ICMP/TTL and asymmetry; TCP connectivity probes; conditional vs broad debug, risk of CPU/log overload, `terminal monitor`, `undebug all`; syslog severity 0–7, facility, timestamps, buffer/console/remote collector; SNMP polling vs traps/informs, v2c community weaknesses vs SNMPv3 authentication/privacy, OIDs/MIBs, counters and baselines; fault timestamps and evidence preservation.
- **Do:** configure collector and monitoring for multiple routers; capture false positives such as an ICMP-disabled intermediate device while destination is reachable. Restrict debug to a neighbor/flow when supported, and always stop it. Generate interface flap, ACL deny, neighbor flap and authentication failure, correlate log times and SNMP/flow counters.
- **Prove:** diagnose an incident using only read-only commands first, produce an incident timeline and smallest testable hypothesis. Explain the limits of ping, traceroute and a single debug line.

#### 4.2 Configure/verify Flexible NetFlow (priority: high)

- **Know:** `flow record` (keys/non-keys), `flow exporter` (collector destination, source interface, transport, protocol), `flow monitor` (joins record and exporters), interface application inbound/outbound, interface support, cache/active/inactive timeouts, sampling concept, IPFIX vs NetFlow, flow fields/byte and packet counters. Distinguish **monitor configuration** from actual **exporting**; NetFlow is metadata, not packet capture.
- **Do:** monitor branch uplink, create a custom record for 5-tuple/protocol/bytes/packets, export to collector container (supported software as appropriate), generate 3 distinguishable flows, inspect monitor cache and collector receipt. Break wrong `source`, collector address, template/port, monitor direction and missing interface attachment.
- **Prove:** given full FNF configuration, identify whether traffic is counted and where records go. Capture/export sample and demonstrate with timestamps and counters.

#### 4.3 Configure SPAN, RSPAN, ERSPAN (priority: high)

- **Know:** local SPAN session, source interface/VLAN, direction RX/TX/both, destination interface and its forwarding restrictions, oversubscription and loss; **RSPAN** uses an RSPAN VLAN across switches/trunks; **ERSPAN** encapsulates mirrored frames over an IP/routed network using GRE with session identifier and platform-specific support. Distinguish from NetFlow metadata and packet sampling.
- **Do:** copy traffic from a host port to a `tcpdump`/Wireshark analyzer; observe both directions. Extend with RSPAN across two switches and ERSPAN across a routed topology **when supported**. Inject incorrect monitor source, direction, VLAN, remote trunk and destination. Keep normal production forwarding isolated from analyzer ports.
- **Prove:** read a multi-session configuration and identify actual packet destinations. Demonstrate a pcap that proves your filter and span direction.

#### 4.4 Configure/verify IP SLA (priority: high)

- **Know:** IP SLA operations (ICMP echo essential; TCP connect/UDP jitter as extensions), schedule, frequency, timeout, threshold, source interface/VRF, return-path assumptions, response time and failure codes, object tracking, integration with floating static routes/FHRP; do not confuse `threshold` with automatic withdrawal—tracking/logic is needed.
- **Do:** monitor upstream next-hop and distant target, track reachability, use primary/backup static routes with distinct administrative distances; make a local link **stay up** while far target fails. Verify `show ip sla statistics`, `show track`, forwarding and recovery. Add an alert or EEM action as extension.
- **Prove:** differentiate physical-interface failover from end-to-end reachability failover; explain what happens on 4 simulated failure/recovery sequences.

#### 4.5 Describe Catalyst Center configuration, assurance and AI-powered workflows

- **Know:** Catalyst Center as central management/orchestration/assurance platform; discovery/inventory, site hierarchy and network settings, templates/automation and compliance, software image management (SWIM), PnP onboarding, telemetry/health, client/device analytics, path trace, event/incident insights, AI-powered issue correlation and suggested remediation, human approval/risk governance. **Do not equate a predictive insight with an autonomous safe config change.** Product capabilities vary by software release/licensing.
- **Do (recommended):** with an approved sandbox, navigate inventory, health/assurance dashboards, discovery, API docs and relevant workflows; create an incident runbook explaining how alarms, telemetry and AI-assisted insights would be corroborated by device-level evidence.
- **Prove:** distinguish Day-0/Day-1/Day-2 workflows and explain exactly what a controller knows and what evidence still needs human verification.

#### 4.6 Configure/verify NETCONF and RESTCONF (priority: high)

- **Know NETCONF:** SSH (commonly port 830), XML RPC, datastore semantics `running`/`candidate`/`startup` when available, `<get>`, `<get-config>`, `<edit-config>`, locking/commit support dependence, capabilities and YANG model paths. **RESTCONF:** HTTP(S), resources/URIs, GET/POST/PUT/PATCH/DELETE semantics, JSON and XML media types, authentication and TLS; differences between RESTCONF and arbitrary REST APIs; response/status and application errors. Understand RFC 8040 URI style such as `/restconf/data/...` and `application/yang-data+json` for RESTCONF. Device implementations and supported methods differ.
- **Do:** enable NETCONF and RESTCONF on a licensed/compatible device; connect with `ncclient` and curl/Postman; read interface state, make a safe configuration change, read it back, intentionally send invalid XML/JSON, bad YANG path, unauthorized request and stale credential; inspect error payload and logging. Test `:candidate` only on platforms advertising that capability. Capture request/response metadata without exposing secrets.
- **Prove:** from a YANG path/API request determine targeted resource, request purpose, expected HTTP behavior and why a failed request was rejected. Provide working requests in a reproducible script.

### 5.0 Security — 20%

> The blueprint is broad: combines **device configuration** with **security architecture/product understanding**. Do not study only access lists. Create practical hardening, AAA, API security and NGFW scenario exercises, and learn the Cisco-specific terminology alongside general principles.

#### 5.1 Configure/verify device access control

**5.1.a Line and local user authentication**

- **Know:** `username ... secret`, privilege levels and `enable secret`, console versus `line vty`, SSHv2, local login vs line password, `transport input ssh`, `login local`, access-class for SSH management, login timeouts, exec-timeout, `service password-encryption` limitations, key generation requirements, banners, source interfaces, secure secrets, management-plane restriction and operational console recovery. Never use Telnet in a production design.
- **Do:** create a hardened router/switch management baseline with named local account and correct privilege; confirm permitted SSH client connects and unauthorized client is denied. Break login authentication and line access; recover from console without restarting or erasing config.
- **Prove:** compare `login`, `login local` and `login authentication ...`; read a VTY configuration and determine who can connect, by what transport and via which credentials.

**5.1.b AAA authentication and authorization**

- **Know:** AAA = authentication (identity), authorization (permitted commands/services), accounting (activity records). `aaa new-model`, default versus named method lists; fallback order, **server unreachable vs explicit reject** behavior, local fallback and lockout prevention. TACACS+ (typically TCP/49, separates authentication/authorization/accounting, generally encrypts packet body) versus RADIUS (commonly UDP 1812/1813 for auth/accounting, designed primarily for network access, differing packet protection); local AAA, role/privilege concepts, command authorization when supported, accounting start/stop and time integrity. 802.1X is relevant at a conceptual endpoint-security level, but v1.2 no longer requires configuring the old standalone wireless security content.
- **Do:** one router, two clients, TACACS+ or FreeRADIUS container, local emergency account. Enforce different user roles; enable login/exec authentication; test server reachable, wrong password, server down, authz deny, fallback and accounting logs. **Always keep console access and explicit rollback** during AAA tests.
- **Prove:** given method-list configs and server reachability states, predict whether a user logs in and gets privileged commands, then support with logs. Explain why `group tacacs+ local` is not equivalent to "always try local if password rejected".

#### 5.2 Configure/verify infrastructure security

**5.2.a ACLs (priority: very high)**

- **Know:** standard vs extended, numeric vs named, wildcard inverse mask, sequence numbers, first-match processing, implicit deny, interfaces inbound/outbound, source/destination IP and ports, TCP/UDP/ICMP, **IP protocol number 89 for OSPF**, IPv6 ACL syntax/behavior where applicable, established keyword limitations and stateless ACL behavior, management ACL versus transit ACL. ACL effect on OSPF, NTP, SNMP, API access, GRE (IP protocol 47), IPsec (ESP protocol 50/IKE UDP ports depending on design) and other control-plane protocols. Know exact traffic directions and necessary reverse flows.
- **Do:** build deny-by-default segment policy permitting only defined application ports and routing control traffic. Inject an ACL that accidentally blocks OSPF; **correct it with the minimum edit and preserve existing policy lines**. Practice modifying named ACLs via sequence numbers, not clearing entire ACL. Verify hit counters, adjacency and packet traces. Design a *negative test matrix* of traffic that must remain blocked.
- **Prove:** for ten flows, identify first matching ACE and result from full ACL + applied interface/direction; troubleshoot OSPF neighbor failure caused by ACL while maintaining original security requirement. Recompute wildcard masks accurately at speed.

**5.2.b CoPP (Control Plane Policing; priority: high)**

- **Know:** what traffic is destined to the **device control plane** versus transit/data plane; control-plane protection from CPU exhaustion, classification through ACL/class maps, policy map police actions and class-default, CoPP application to `control-plane` (image-dependent), required exemptions/allowances for routing adjacencies and management, policing rates/bursts vs packet lengths, safe deployment and monitoring. CoPP is **not** an ordinary outbound interface policy and should not accidentally starve routing protocols.
- **Do:** build allow/classify policies for OSPF/BGP/management/ICMP while limiting unwanted traffic to the router CPU. Use low-rate benign test traffic, verify counters and adjacencies. Inject ACL class mismatch, policy not attached, too-aggressive police rate, missing management match, and recover via console or an out-of-band path. **Never overwhelm real network devices or third-party networks.**
- **Prove:** from ACL + class map + policy map + CoPP attachment, determine which traffic hits which policing action; explain why transit traffic is or is not affected and how to confirm via counters.

#### 5.3 Describe REST API security (priority: high)

- **Know:** HTTPS/TLS certificate trust, identity and hostname validation, authentication vs authorization; Basic Auth, bearer/API tokens, OAuth 2.0 at a conceptual level, JWT structure at a high level, token expiry/rotation, least privilege/RBAC, scopes, secure secret handling, request signing where applicable, sensitive logs, input validation, replay protection, rate limiting, service accounts, and HTTP 401 vs 403. Be able to diagnose 400/401/403/404/405/409/415/422/429/500/502/503 with context; codes have standard meanings but vendor-specific payloads matter. Recognize CORS/browser-only cases and that base64 encoding is **not encryption**.
- **Do:** use Postman/Bruno/curl against a sandbox or a locally hosted mock API; send good and bad requests: missing auth header, expired token, malformed JSON, wrong method, bad `Content-Type`/`Accept`, missing resource, insufficient permission and invalid certificate. Record method, URL, auth type, headers, body, status, response and the minimal fix. Use a test account; don't publish tokens or insecure production examples.
- **Prove:** receive a screenshot or raw HTTP exchange and diagnose the issue **without guessing**. Demonstrate HTTPS certificate validation and a secure token storage workflow, including automatic reauthentication when appropriate.

#### 5.4 Describe network security design components

**5.4.a Threat defense**

- **Know:** defense in depth, attack surface, least privilege, segmentation, zero trust concepts, detect/prevent/respond, IDS vs IPS, signature vs behavior/analytics, network detection and response (NDR), security analytics/telemetry, DNS and web security, secure management plane and control plane, common attack categories (DDoS, spoofing, credential theft, lateral movement), incident-response basics. Differentiate threat prevention from mere logging and describe false positive costs.
- **Do:** develop a threat model for a branch, campus and data center; mark management, data, and control plane protections on your topology. Run **authorized benign** detection tests with a local IDS/IPS and view logs. Identify 5 controls that reduce blast radius if one subnet is compromised.
- **Prove:** for each threat scenario, pick preventive/detective/response controls and justify operational costs.

**5.4.b Endpoint security**

- **Know:** EPP/NGAV vs EDR/XDR, endpoint posture, patching, isolation, device identity, NAC and Cisco ISE concepts, endpoint telemetry, BYOD/guest/managed endpoint distinctions, trust and policy enforcement, response workflows, phishing vs malware controls, north-south firewalls vs endpoint-local protection. Learn Cisco platform vocabulary (e.g., Secure Endpoint / identity services) without assuming a single product name fully describes all security layers.
- **Do:** design access rights for corporate managed, guest and IoT endpoints; compare what a switchport policy, SGT, NGFW and endpoint agent each can enforce. Optional sandbox UI tour for EDR alert/investigation.
- **Prove:** draw response to a compromised endpoint and explain network containment vs host isolation.

**5.4.c Next-generation firewall (NGFW; priority: high)**

- **Know:** basic stateful firewall vs NGFW; L3/L4 rules versus application identification/control, Layer 7 visibility, IPS/intrusion prevention, URL filtering, user/device identity-based rules, reputation/threat intelligence, malware/file inspection, TLS decryption inspection (benefits, privacy and limitations), security zones, NAT/policy interactions, logging and centralized policy. For Cisco-specific recognition: Cisco Secure Firewall, Secure Firewall Threat Defense (FTD) and common management concepts including Secure Firewall Management Center (FMC), licensing/deployment/version caveats; distinguish Cisco IOS ACL, zone-based firewall and dedicated NGFW capabilities.
- **Do (recommended):** in a mock policy or sandbox, define a rule permitting HTTPS to sanctioned apps but denying a disallowed app on the *same port*; annotate policy order and identity, TLS and inspection constraints. Optional local open-source firewall/IDS demo to observe L7 verdicts; it is **not** identical to Cisco FTD behavior.
- **Prove:** explain at least 15 vignettes: IPS vs IDS, reputation vs signature, application aware vs port based, SSL/TLS inspection risks, false positive tuning, passive TAP vs inline block, firewall HA, rule order and policy deployment.

**5.4.d Cisco TrustSec and MACsec**

- **Know TrustSec:** Security Group Tags (SGTs), identity-based segmentation, SGT classification (static or dynamic), propagation/inline tagging and enforcement via SGACL, policy matrix and ISE's policy coordination. Distinguish VRF/VN macrosegmentation from SGT group-based policy. **MACsec (IEEE 802.1AE):** hop-by-hop Layer 2 encryption/integrity, key agreement/MKA concepts, link/device prerequisites, switch-to-switch or host-to-switch use cases, what it does not protect across a routed end-to-end path; contrast **MACsec vs IPsec**.
- **Do (selective):** diagram source SGT 10 to destination SGT 20 and evaluate an SGACL matrix; model one switch uplink with MACsec and annotate plaintext/encrypted sections. If hardware/image supports TrustSec/MACsec, verify counters, tags and key/peer status; otherwise design/config interpretation rather than forcing unsupported commands.
- **Prove:** identify enforcement location, whether group tagging is required over a particular link, and choose MACsec vs IPsec for campus link versus site-to-site protection.

### 6.0 Automation and Artificial Intelligence — 15%

> **Study automation continuously, not as an end-only chapter.** Prioritize reading scripts quickly, predicting their output, correcting malformed requests and writing small working programs. Cisco labels this domain "Automation and Artificial Intelligence"; the explicit 6.x tasks are mainly Python, JSON, modeling, APIs, EEM and orchestration. AI-powered Catalyst Center workflows appear explicitly under **4.5**. Avoid adding an invented broad machine-learning syllabus.

#### 6.1 Interpret basic Python components and scripts (priority: very high)

- **Know language fundamentals:** indentation and blocks, variables and data types, truthiness, operator precedence, comparisons and boolean operators; strings/slicing, lists, tuples, dictionaries and sets; indexing and key access, membership; `if`/`elif`/`else`, `for`/`while`, `range`, `enumerate`, `zip`, `break`/`continue`; function definition, parameters, scope and return; `try`/`except`/`finally`; file read/write, context managers `with open(...)`, paths, common exceptions (`KeyError`, `ValueError`, `TypeError`, `FileNotFoundError`); `print`, string `format`, f-strings, conversion, iterating `list[dict]`, nested JSON payloads, `requests` basics. Include `.read()`, `.readlines()`, `.write()`, `join`, `split`, `strip`, comprehensions as useful extensions.
- **Formatting (especially important in the supplied reports):** Python format mini-language `[fill][align][sign][#][0][width][grouping][.precision][type]`; `:<width`, `:>width`, `:^width`, custom fill e.g. `{:#>15}`, integer and float formatting `.2f`, `.2%`, `.08%`, comma grouping, differences between numeric presentation types and strings. The `#` character is **a fill character** in `{:#>15}` because it is before `>`; elsewhere it can be an **alternate-form flag** (e.g. `#x`). Do not memorize plausible-looking but invalid placeholder syntax.
- **Do:** write 25 tiny 5–20-line scripts, starting with inventory list of dicts, loop/filter/pretty-print, CSV reading, JSON backups, exceptions, safe retry, output comparison. For every script, **predict exact stdout by hand before execution**, including padding and newline; then run and explain errors. Write simple unit tests, `ruff`/lint optional. Put a list of all missed output patterns into a scratchpad.
- **Prove:** accurately trace and complete 30 original scripts (especially loops + nested dicts + format specifiers); understand *why* code raises an exception or produces a certain type/value.

**Verified-style practice examples (these are independently authored study drills, not exam questions):**

```python
inventory = [{"item_id": "673624583672328", "item_code": "jbdhs"}]
for item in inventory:
    print("{:#>15}, {:#>7}".format(item["item_id"], item["item_code"]))
# The 15-character ID fills its field; the 5-character code is left-padded to 7 by two '#'.
# Output: 673624583672328, ##jbdhs

print(format(0.8, ".08%"))
# Output: 80.00000000%  (eight digits after the decimal point)
```

**Real-world extension:** convert a topology inventory to an expected-adjacency matrix, parse sanitized command outputs, generate a change summary and test with `pytest`. Do not send sensitive configuration or credentials to a public AI model.

#### 6.2 Construct valid JSON-encoded files (priority: very high)

- **Know:** strict JSON `object`, `array`, `string`, `number`, boolean `true/false`, `null`; quoted keys/strings, valid escapes, no comments/trailing commas, nested arrays and objects; Python JSON type mapping (`dict/list/str/int/float/bool/None`), serialization/deserialization. **`json.dump(obj, file)` writes to a file-like object; `json.dumps(obj)` returns a string; `json.load(file)` reads from a file-like object; `json.loads(string)` parses JSON text.** Class equivalents: `json.JSONEncoder().encode(obj)` produces JSON text; `json.JSONDecoder().decode(text)` parses JSON text.
- **Do:** build a JSON inventory schema with routers, VRF and interfaces; export it, load it back and compare values. Repair malformed JSON (single quotes, trailing comma, `True`, omitted quote, incorrect nesting). Practice matching code blocks to correct string/file operations and knowing when reading consumes the file cursor.
- **Prove:** construct valid JSON from a specification with **no YAML or Python literals accidentally mixed in**. Identify exact output and return type of each serialization function.

```python
import json
inventory = {"nodes": [{"name": "R1", "asn": 65001, "enabled": True}]}
with open("inventory.json", "w", encoding="utf-8") as f:
    json.dump(inventory, f, indent=2)  # object -> JSON FILE
with open("inventory.json", "r", encoding="utf-8") as f:
    recovered = json.load(f)          # JSON FILE -> object
wire_text = json.dumps(recovered)     # object -> JSON STRING
again = json.loads(wire_text)         # JSON STRING -> object
assert again == inventory
```

#### 6.3 Describe YANG principles and benefits

- **Know:** why human-friendly CLI differs from structured schema; modeled tree of containers/lists/leaves/leaf-lists, types/ranges, `config true/false` concept, constraints and validation, `augment`, namespaces and modules as recognition topics; industry-standard `ietf-*` vs vendor-specific models, OpenConfig at high level; operational/state vs configuration data; relationship of YANG to NETCONF/RESTCONF and XML/JSON encoding. **YANG is a data modeling language, not itself a transport protocol or API.**
- **Do (recommended):** inspect a Cisco/IETF YANG model, locate a leaf and its datatype, then map it to NETCONF XML or RESTCONF JSON path. Deliberately send an invalid value and inspect validation response.
- **Prove:** draw how a YANG modeled interface's name, enabled state and IP address become a structured request; distinguish JSON serialization from schema validation.

#### 6.4 Describe APIs for Catalyst Center and SD-WAN Manager

- **Know Catalyst Center auth flow:** `POST /dna/system/api/v1/auth/token` using Basic Auth over TLS (or optional platform-supported AES alternative), obtain token; then include `X-Auth-Token` on subsequent calls. Know inventory, health, topology, task and configuration API categories and pagination, asynchronous task workflows and privilege limitations. **Know SD-WAN Manager:** controller APIs for monitoring, configuration/templates, device inventory, alarms and policy at a high level; check specific release docs because endpoints/authentication can differ. Do not assume SD-WAN Manager reuses Catalyst Center's token endpoint. **API vs CLI:** authentication, data modeling, structured output, idempotency, change safety, error handling.
- **Do:** in a sandbox, perform token request, device list GET and valid/invalid API calls with Python and Postman/Bruno; for SD-WAN Manager use vendor docs/sandbox to locate applicable endpoint/auth mechanism. Build a request collection with variables (base URL, token), no secrets committed. Use published API docs rather than a memorized endpoint for every operation.
- **Prove:** on a blank REST client, demonstrate entire authenticated Catalyst Center workflow and explain why HTTP Basic on the **initial token request** is not equivalent to the later `X-Auth-Token` header.
- **Primary reading:** [Catalyst Center Authentication](https://developer.cisco.com/docs/catalyst-center/authentication/) and [Catalyst Center sandboxes](https://developer.cisco.com/docs/catalyst-center/sandboxes/).

#### 6.5 Interpret REST API codes and payload results using Catalyst Center and RESTCONF

- **Know:** HTTP verbs GET/read, POST/create/action, PUT/replace, PATCH/partial modify, DELETE/remove; idempotence by design (GET/PUT/DELETE are intended idempotent in HTTP semantics, POST generally not); common `200 OK`, `201 Created`, `202 Accepted` (async), `204 No Content`, `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, `405 Method Not Allowed`, `409 Conflict`, `415 Unsupported Media Type`, `429 Too Many Requests`, `500 Internal Server Error`, `503 Service Unavailable`; vendor task IDs and nested JSON keys; pagination, request bodies vs query parameters, content type vs accept, certificate and URL errors. Read status + headers + body together, not a status code alone.
- **Do:** 20 deliberate API mistakes including POST instead of GET, wrong authentication, missing `Content-Type`, invalid JSON, wrong URI, incorrect token, resource conflict, unsupported method, timeout and TLS verification error. For every failure: state hypothesis, isolate the layer, make the smallest change and retry; store sanitized request/response transcript.
- **Prove:** solve 15 screenshot/text-based debugging scenarios and write the correct HTTP method/path/header/body combination; explain when a `202` needs polling of a task and why `204` should not be parsed as JSON.

#### 6.6 Construct an EEM applet to automate config/troubleshooting/data collection (priority: high)

- **Know:** event managers and applet logic; event detectors (syslog, interface, timer, track, CLI, SNMP at capability level), `event manager applet`, `event`, ordered `action`, CLI execution, `enable`/privilege/user policy context, environment variables and pattern matching; syslog messages, rate-limiting/loop prevention, logging, scheduler and avoiding unsafe automatic config changes. EEM applet vs Tcl policy; `$_cli_result`/event variables where applicable; IOS feature/version syntax varies.
- **Do:** write applets that (a) react to a meaningful syslog event and collect `show` evidence, (b) poll periodically, (c) respond to tracked IP SLA state with a benign action, (d) log a limited interface reset test in an isolated environment only with explicit safety guard. Create an applet whose actions are **misnumbered**, another with a bad event regex and another without adequate privilege; repair. Verify history/logs and no repeated trigger loop.
- **Prove:** reconstruct an EEM applet from task requirements, predict action sequence when log arrives, identify event trigger and prove observable result. Practice 8–12 varied applets until syntax feels natural.

#### 6.7 Compare agent vs agentless orchestration tools

- **Know Ansible:** typically agentless over SSH/network APIs, YAML playbooks, inventory, modules, tasks, roles, push-style execution; Python is important to its implementation and module ecosystem. **Puppet:** generally agent-based master/agent pull, declarative manifests in Puppet DSL, catalogs, Ruby heritage. **Chef:** typically agent-based client/server with cookbooks and recipes in Ruby DSL, pull/convergent execution; also has variants. **SaltStack:** Python-based, typically master/minion, event bus, states often YAML+Jinja, can use push-style remote execution and pull/reconciliation patterns, supports agentless Salt-SSH. No tool is exclusively "declarative" or "procedural" in all uses.
- **Do:** build one real Ansible playbook to collect `show` commands or configure an NTP server on test equipment; practice idempotency by running twice and examining `changed`. **For the other tools, design/compare rather than install massive orchestrators unless you want deeper career skills.** Study basic Puppet manifest, Chef recipe and Salt state syntax from vendor documentation.
- **Prove:** construct a tool comparison table with agent model, controller/master, communication, language, config artifact, execution model, use case and caveats. Correctly associate **Ansible/playbooks**, **Puppet/manifests**, **Chef/cookbooks + recipes**, **Salt/minions + states** without treating model categories as absolutes.

#### Automation and AI engineering extension (not a separate v1.2 6.x objective)

- Use AI assistants for generating **original** practice questions, designing sample faults, explaining errors and suggesting test assertions—but independently validate every command and API call with Cisco docs and a working lab.
- In network operations, evaluate AI-generated anomaly detection or remediation suggestions against actual syslog, NetFlow, device counters and change windows. Produce a **human-reviewed, reversible** change plan; no unsupervised configuration pushed to production.
- Build one “network-intent → code → configuration diff → prechecks → staged change → postchecks → rollback” demonstration. This is for engineering development, not because the official blueprint promises an AI coding question.

---

## 5. Reproducible lab catalogue

> **Not topology files yet.** These are future lab *specifications*. Every lab should have a success case, a broken case, validation commands/pcaps, a reset procedure, and a link to its blueprint objective. A single multi-topic lab can satisfy several objectives, but it does **not** replace single-feature understanding.

### Tier A — Mandatory hands-on for blueprint config/troubleshoot/diagnose objectives

| ID | Blueprint | Lab spec and required result | Faults to practice | Target evidence |
|---|---|---|---|---|
| L01 | 3.1.a | 3-switch VLAN/trunk campus, all intended VLANs passed | Wrong native/allowed VLAN, DTP mismatch | Operational trunk status, MAC table, tagged pcap |
| L02 | 3.1.b | 2/4-link LACP/PAgP/static EtherChannel | Negotiation, VLAN/mode, member mismatch | Bundle flags, active member state, traffic tests |
| L03 | 3.1.c | RSTP triangle, root selection, path failover | Bad root priority, blocked expected uplink | STP roles and failover trace |
| L04 | 3.1.c | MST 2-instance region and guard protection | Region mismatch, rogue root, edge BPDU | Region/instance state, guard and recovery proof |
| L05 | 3.2.b | OSPFv2 backbone + 2 normal areas | Area/MTU/timer/network type/passive errors | Neighbor FULL, routes, LSDB, pcap |
| L06 | 3.2.b | OSPF inter-area summarization and filtering | Bad summary, wrong ABR, missing specific | Exact route visibility and data-plane reachability |
| L07 | 3.2.b | OSPFv3 IPv6 version of a small multi-area lab | Wrong IPv6 neighbor/interface/area | IPv6 adjacency and prefix verification |
| L08 | 3.2.c | Directly connected eBGP 3–4 AS; 10+ prefixes | Wrong AS, no exact RIB entry, next-hop | Established sessions + route and ping table |
| L09 | 3.3.b | NAT/PAT with inside hosts + external services | Interface direction, ACL, return route | Translation table + pcap before/after NAT |
| L10 | 3.3.c | HSRP / VRRP redundant gateways | Priority, tracking, preemption, uplink loss | Gateway active/master state and packet loss |
| L11 | 2.2.a | Two simultaneous VRFs with overlapping addresses | VRF mismatch, wrong per-VRF static route | Route tables and allowed/denied reachability |
| L12 | 2.2.b | GRE with global underlay and routed overlay | Underlay reachability, recursive route, MTU | Tunnel state + outer/inner pcap |
| L13 | 2.2.a,b | GRE in a customer VRF, global underlay | Tunnel `vrf forwarding`, overlay routes | End host traffic over tunnel in VRF |
| L14 | 2.2.a,b | Front-door transport VRF + separate overlay VRF | Missing/wrong `tunnel vrf`, transport route | Correct underlay and overlay lookup proof |
| L15 | 2.2.b | IPsec VTI or GRE protected by IPsec | Wrong peer/keys/proposals, bad route | SAs/counters + encrypted pcap |
| L16 | 4.1 | Syslog/SNMP/diagnostics and safe conditional debug | Missing collector, SNMP ACL, bad debug | Timeline, selected SNMP OID, safe debug stop |
| L17 | 4.2 | Custom FNF with a collector and 3 flows | Record vs monitor vs exporter mix-up | Cache entries, exported flow receipt |
| L18 | 4.3 | Local SPAN to analyzer container | Wrong source/direction/destination | Captured expected frames, no unintended traffic |
| L19 | 4.3 | RSPAN over trunk, ERSPAN over L3 if available | Missing VLAN/route/session, oversubscription | Remote pcap, session verification |
| L20 | 4.4 | IP SLA with tracking and static-route failover | Wrong operation/schedule/track/frequency | SLA state, route switch, recovered service |
| L21 | 4.6 | NETCONF edit/read, feature discovery, failure | Wrong datastore/path/XML/capability | RPC request/response and config diff |
| L22 | 4.6 | RESTCONF data GET/PUT/PATCH where supported | Wrong media type/path/permissions | HTTP exchange, config before/after |
| L23 | 5.1.a | Safe SSH local access hardening | VTY/line auth, locked-out test account | Authorized/unauthorized SSH tests |
| L24 | 5.1.b | AAA with TACACS+ or RADIUS + local fallback | Server down, reject, authz deny | AAA debug/accounting evidence, recovery |
| L25 | 5.2.a | Named ACL policy with routing-protocol exception | OSPF blocked, bad order/direction/wildcard | ACE hits + routing neighbor recovers |
| L26 | 5.2.b | CoPP class/policy/attach, protect control plane | Class mismatch, too restrictive police | CPU-plane classification, policy counters |
| L27 | 6.6 | EEM event → safe evidence capture + log | Wrong detector, regex, permissions, action order | Event/action output, syslog, loop prevention |

**Platform caveat:** A few Tier A items can require CML, Cisco DevNet, or an appropriately licensed device rather than Containerlab if the selected node image lacks support. The requirement is **working, correctly verified behavior**, not using one orchestrator at any cost.

### Tier B — Selective concept labs with exceptional learning value

| ID | Blueprint | Small activity | Engineering insight |
|---|---|---|---|
| B01 | 1.1 | 2-tier vs 3-tier routed campus failure | Blast radius and design tradeoffs |
| B02 | 1.2 | SD-WAN onboarding/policy packet-flow diagram + UI tour | Controller ownership, underlay vs overlay |
| B03 | 1.3 | SDA LISP/VXLAN/fabric/WLC flow walkthrough | Role mapping, legacy border and SGT policy |
| B04 | 1.4 | Full QoS classification exercise; traffic bursts | Queue vs shaping vs policing conditions |
| B05 | 2.1 | VM vs container and virtual L2 bridge | vNICs, virtual uplinks, VLAN tags |
| B06 | 2.3.b | Linux VXLAN with VNI capture | Inner/outer headers and MTU overhead |
| B07 | 3.2.a | Compare 4-router EIGRP vs OSPF states | Successor/feasibility vs LSDB/SPF |
| B08 | 3.2.d | PBR split egress by source | Policy vs destination routing |
| B09 | 3.3.a | NTP client/server and timestamp failure | Operational integrity |
| B10 | 3.3.d | Multicast join, RPF fail, SSM walkthrough | Why multicast differs from unicast |
| B11 | 4.5 | Catalyst Center health, inventory and path trace | Controller assurance vs device evidence |
| B12 | 5.3,6.4,6.5 | REST client deliberately broken in 15 ways | HTTP method/auth/header/body triage |
| B13 | 5.4.c | NGFW app-aware policy walkthrough | L7 vs port-based blocking |
| B14 | 5.4.d | SGT matrix + MACsec vs IPsec trust map | Segmentation vs encryption |
| B15 | 6.1,6.2 | Inventory parse/format/backup with pytest | Python correctness and file vs string JSON |
| B16 | 6.3 | YANG model → NETCONF/RESTCONF request | Schema/path/encoding separation |
| B17 | 6.7 | Ansible collect-state + idempotent NTP change | Agentless automation and drift checks |

### Tier C — Exam-length integrated challenges

**C01. Branch routing and switching restoration (L01–L08).** Three switches, four routers, two OSPF normal areas, eBGP edge, redundant gateway. Fix port channel that won't form, move wrong STP root, restore OSPF summarization and get BGP loopback reachability. Each starting state has a known-good golden validation target. Do this with read-only commands before touching configuration.

**C02. Dual customer VRF overlay restoration (L11–L15).** Two site routers, transit/underlay, two overlapping customer prefixes, GRE + customer VRF, static routes, optional transport VRF and IPsec; only required customer traffic must traverse tunnel. Record all four packet path perspectives (source VRF, tunnel inner, outer transport, remote VRF). Break one tunnel/VRF/route fault at a time, then a hidden combination.

**C03. Observe and defend (L16–L27).** Router + switch with local SPAN, exporter to NetFlow collector, IP SLA tracking, SSH/AAA, OSPF-permitting ACL, safe CoPP, EEM applet and an API-based verification script. A single maintenance change should show logs, captures, flow records and failure recovery. Protect against accidentally locking yourself out.

**C04. Network engineering capstone.** Start with a business brief: headquarters, 2 branches, redundant ISPs, sensitive/guest/IoT users, app SLA, support constraints, segmentation. Design and configure the suitable ENCOR-scope environment; include a migration plan, monitoring, access controls, automated tests, and runbooks. This is *not* a simulation of a specific live exam lablet.

### Random fault-injection library (make these independent scenarios)

1. L2 allowed VLAN removed from exactly one trunk.
2. Native VLAN mismatch on one member while others work.
3. LACP active/passive replaced with passive/passive.
4. Port-channel member inconsistent speed/operational setting (where platform allows).
5. Rogue STP root and unexpected root-inconsistent port.
6. BPDU Guard err-disable on a host-facing edge port.
7. OSPF interface placed in wrong area or accidentally passive.
8. OSPF point-to-point vs broadcast disagreement and unexpected adjacency behavior.
9. OSPF timer/MTU mismatch with characteristic state.
10. OSPF ABR summary covers an unreachable prefix (potential blackhole).
11. BGP neighbor wrong AS / no establishment.
12. BGP prefix missing from RIB while `network` exists.
13. VRF static route written in global RIB.
14. GRE underlay has no route to remote tunnel destination.
15. GRE outer `tunnel vrf` misassigned.
16. ACL denies routing IP protocol or return traffic.
17. CoPP policy unintentionally rate-limits routing adjacency traffic.
18. NetFlow monitor created but not applied to any interface.
19. SPAN session with incorrect source or wrong direction.
20. IP SLA operation present but never scheduled.
21. AAA server unreachable, local fallback method misconfigured.
22. RESTCONF authentication succeeds but YANG path is invalid.
23. Catalyst Center token requested with GET rather than POST.
24. JSON script attempts `json.load()` on a string instead of a file-like object.
25. EEM event fires repeatedly and amplifies the problem due to missing guard.

**Core rule:** never inject several faults while learning a feature; inject single faults first. **Only** advance to hidden multi-fault challenges after you know the healthy baseline.

---

## 6. Troubleshooting, automation and capstone projects

### 6.1 The engineering troubleshooting method

Use this on every lab and in real work:

1. **Define impact and scope:** affected hosts, VRF, VLAN, application, direction, timestamp. Write observed vs expected behavior.
2. **Model the path:** source host/gateway → ingress ACL → routing/VRF → tunnels/NAT/policy → destination; include return path and controller dependencies.
3. **Check lower layers/transport first:** port states, trunk/VLAN/aggregation, IP addresses, ARP/NDP, link protocol, underlay reachability.
4. **Check control-plane state:** STP state, OSPF FULL/LSDB, BGP Established/routes, FHRP active, tunnel status, API and AAA logs.
5. **Check forwarding/policy:** RIB and FIB, VRF, ACL hit order, NAT/PBR, QoS counters, CoPP, endpoint firewall, route asymmetry.
6. **Choose lowest-risk, smallest change:** exact command and expected outcome; do not wipe the whole config unless rebuilding from a clean state is the explicit objective.
7. **Verify positive and negative tests:** not only “desired ping works,” but “forbidden subnet still blocked,” “correct path,” “correct counters.”
8. **Document prevention and rollback:** root cause, trigger, contributing factors, blast radius, config diff, monitoring improvement.

**Troubleshooting worksheet:**

```text
Incident ID / start time:
Expected flow and source/destination/VRF:
Actual symptom / exact error:
Observed device state and timestamp:
Top three hypotheses:
Safe command or probe to distinguish hypotheses:
Root cause and evidence:
Minimal change / approval / rollback:
After state (positive + negative tests):
What alert or automated test would catch this earlier?:
```

### 6.2 Projects that belong in a network engineer's portfolio

**Project P1 — Campus resilience and segmentation:** choose 2-tier/3-tier, configure VLAN/trunks/EtherChannel/RSTP/MST/FHRP, demonstrate intended gateway and link failure recovery. Deliver diagrams, IP/VLAN table, sanitized configs, validation/rollback and incident timeline.

**Project P2 — Multi-area enterprise routing:** 5–7 routers across area 0 and branch normal areas with OSPFv2/v3, ABR aggregation, permitted prefix lists; direct eBGP edge, IPv4 and IPv6 (where supported), NAT/PAT and PBR extension. Deliver LSDB/RIB explainers, route tables and four failures with a repair explanation.

**Project P3 — Multi-tenant WAN overlay:** customer VRFs and overlapping subnet addresses, GRE variants, optional IPsec, underlay/overlay reachability and MTU measurements. Deliver an **inner-versus-outer packet anatomy diagram**, no-leak test and route-repair runbook.

**Project P4 — Monitoring, SLO and incident response:** deploy syslog, SNMPv3 where supported, FNF/IPFIX, SPAN/pcaps, SLA probes and dashboards; inject network impairment, detect, isolate and report. Deliver a 2-page incident report with evidence timestamps, cause, remediation and prevention.

**Project P5 — Access control and security design:** SSH AAA with emergency access, named ACL, CoPP, NGFW/TrustSec/MACsec architecture and controlled management access; create a change request, test plan and roll back intentional misconfiguration. Deliver a threat model and a negative/positive traffic matrix.

**Project P6 — Programmable operations:** Python pulls device inventory/config via allowed transport, writes structured JSON, validates state, logs decisions, generates an HTML/Markdown network health report; separate Ansible playbook enforces one safe item, and EEM captures relevant evidence. Add CI/unit tests and idempotency checks. **Do not embed secrets or write uncontrolled config changes**.

### 6.3 Capstone acceptance test

Your integrated project must pass all of these:

- [ ] Diagram maps physical/logical topology, VLANs, prefixes, VRFs, routing areas/ASes and management path.
- [ ] **Positive tests:** required connectivity, OSPF/eBGP reachability, accurate NAT, tunnel, and gateway redundancy.
- [ ] **Negative tests:** forbidden source/destination, default VRF leakage, unintended management access and IP protocol not permitted.
- [ ] **Resilience:** link down, primary gateway down, neighbor down and controller/API unreachable are characterized with measured impact.
- [ ] **Visibility:** logs, flow/capture and SLA measurements let another engineer find an injected fault.
- [ ] **Security:** no plaintext shared passwords in Git; SSH/API TLS verification; AAA fallback/recovery; no excessive CoPP blocks.
- [ ] **Automation:** tests are rerunnable and can reliably distinguish a known-good state from a broken state.
- [ ] **Documentation:** runbook supports rebuild from blank, clear rollback, and a postmortem explaining an actual fault.

---

## 7. Flashcards and knowledge retention

Flashcards should support **retrieval**, not replace reasoning or experimentation. A candidate can make thousands of cards and still be underprepared for output interpretation; your deck should contain conceptual, diagnostic and scenario cards, rather than one-liners only.

### 7.1 Deck architecture and card types

**Tag every card** with blueprint ID + resource + type + difficulty, for example `3.2.b::ospf::symptom::hard`.

| Card type | Example prompt | Strong answer criterion |
|---|---|---|
| Fact / term | “What is SD-WAN Validator's old name and job?” | Name + exact orchestration responsibility |
| Why / compare | “Why is GRE not a substitute for IPsec?” | Encapsulation vs encryption, integrity, use case |
| Packet-flow | “Which VRF resolves the GRE outer destination?” | Distinguish `tunnel vrf` from tunnel interface's VRF |
| CLI interpretation | “Port-channel says `suspended`: which checks next?” | Methodical checks with observation, not command guessing |
| Fault → diagnosis | “OSPF stuck EXSTART: list plausible causes.” | Evidence-based possibilities (e.g. MTU) + verification |
| Output prediction | “What is printed by this Python format loop?” | Exact output incl. pad chars |
| API troubleshooting | “401 vs 403 after token exchange?” | Authn vs authz and context |
| Design scenario | “When prefer 3-tier over collapsed core?” | Scale/failure/operations tradeoff |

**Quality rules:** one testable idea per card; always include a causal reason, not just a word; use screenshots/config snippets you created yourself; avoid ambiguous “always/never” language for platform-dependent behavior; retire or rewrite cards you repeatedly misunderstand.

### 7.2 Initial card targets (suggested, not quota)

| Domain | Initial useful cards | Main format |
|---|---:|---|
| 1 Architecture | 80–120 | Architecture + vendor terminology + QoS scenarios |
| 2 Virtualization | 50–90 | Underlay/overlay and encapsulation diagrams |
| 3 Infrastructure | 150–240 | CLI outputs, route/path selection, fault trees |
| 4 Assurance | 60–100 | Collector / monitor / SPAN / IP SLA structure |
| 5 Security | 100–160 | AAA state and access decisions, API errors, NGFW |
| 6 Automation | 120–200 | Python/JSON output, HTTP, YANG, EEM, tool matching |

Total initial range: ~560–910 **high-quality cards**, grown only when a genuine knowledge gap recurs. Use Anki or similar spaced-repetition system; the exact app matters less than recall discipline. Review every day for ~15–25 minutes, with 1-, 7-, 21- and 45-day mixed checks. Include cards drawn from **your own postmortems** and wrong practice questions (without reproducing copyrighted or live exam questions).

### 7.3 An example weekly learning loop

- **Day A:** study theory, draw model, create ≤10 new cards.
- **Day B:** build from blank; add 5 command/verification cards.
- **Day C:** troubleshoot deliberately broken lab; make 5 fault-to-evidence cards.
- **Day D:** complete original questions; write failure explanation and add 3–5 correction cards.
- **Day E:** perform 10–20 minute closed-notes rebuild or code tracing; use spaced review to retain it.
- **End of week:** 60–90 minute cumulative mini-lab using a prior topic plus the new one; prune low-quality cards.

**How to use LLMs/NotebookLM responsibly:** upload **legally obtained** material or your own notes, ask for novel scenarios (not purported exam items), request answer explanations with source references, and independently verify generated technical details in a working lab. Ask for hard distractors based on misconceptions, not buzzword trivia only.

*(Added)* The full NotebookLM + Gemini set-up, the eight prompt templates (T1–T8) used in the daily schedule, and the verification rules are in [§11.3](#113-notebooklm--gemini-active-recall-system). The day-by-day schedule gives a daily card target ("🃏 +N") with seed ideas; the 560–910 range in §7.2 is the floor, and the schedule's daily seeds total about 1,050 over 36 weeks, plus cards from your error log — prune hard as §7.1 says.

---

## 8. Practice exam strategy and exam-day skills

### 8.1 Resource priority

**Primary:** current Cisco blueprint and official configuration/design guides, one coherent video course or a suitable updated book, real repeatable labs, and original retrieval practice.

**Practice sources:** Boson ExSim for reasoning and lablets; Cisco U / Cisco practice materials where confirmed aligned with **v1.2**; Pearson Test Prep if included with a licensed book; custom independently authored tests generated from the blueprint. The Reddit reports include a negative experience with Cisco practice material retaining out-of-scope Wi-Fi content soon after v1.2 released, so **check current version and sample scope before paying**; do not assume that older review still applies today. Verify Boson version before purchasing or upgrading.

**About Examice:** its own website says that its questions are sourced from real exam experiences, rather than exclusively independently written practice material. For Cisco certification integrity and lasting engineering skills, **do not use recalled/leaked live question banks**. Cisco's confidentiality agreement restricts disclosure/reproduction of exam content. Prefer authorized, original practice questions and lab simulations instead. This advice applies to any other “real exam question” vendor, regardless of name.

### 8.2 Four-stage practice exam progression

1. **First month — diagnostic only:** one untimed, closed-notes baseline from an authorized original practice source. Record weakest blueprint IDs and rationale. Don't repeatedly test material you haven't learned.
2. **Middle months — targeted:** 10–25 original questions after each subtopic; read the explanation of **every** answer; reconstruct the network or Python script when wrong. For code, test your prediction; for routing, draw path and RIB.
3. **Final 6–8 weeks — timed and mixed:** alternate independently written exams, random fault labs and timed Python/JSON interpretation. Treat vendor scores as **signals**, not predictors; avoid exact repeats inflating apparent readiness.
4. **Final 2–3 weeks — readiness:** 2+ unseen mixed timed exams separated by review and ≥3 integrated blind labs. Build the entire blueprint audit; address remaining weaknesses, rest appropriately and review exam logistics.

**Suggested personal benchmark** (not a Cisco pass threshold): ≥85% on **fresh** original practice questions overall, no domain below 75–80%; two independent timed practices with stable results; near-perfect performance on critical hands-on tasks; 20–30 original Python/API and QoS interpretation scenarios with clear explanations. Repeating memorized bank questions does *not* count.

### 8.3 Practice question error log

```text
Date / resource / domain / blueprint ID:
Concept tested (paraphrase; do not copy exam or copyrighted questions):
My answer and confidence (high/medium/low):
Why I missed it: knowledge gap / misread / math / wrong inference / timing
Evidence from Cisco docs or my lab:
Correct reasoning in 3 sentences:
One related 'what if' scenario I invented:
Follow-up date / independent retest result:
```

Review **confidently wrong** items as top priority; they're signs of faulty mental models. Reproduce configuration snippets in a sandbox wherever practical rather than trusting explanation keys blindly.

### 8.4 Exam simulation (time-management practice, not a claim about Cisco's exact item layout)

- **120 minutes officially.** The exact number and order of questions/lablets can vary; plan for the full session. Learn the exam UI rules from Cisco/Pearson before arrival, including whether particular items can be revisited and how simulations commit changes.
- **Timed CLI drill:** begin with tasks + target state; inspect device state and IP tables immediately. Budget time for `show` verification, **save configuration** when expected, and avoid rebuilding unrelated portions.
- **BGP/OSPF lab checklist:** neighbor state, interface/IP/mask, advertised networks, exact RIB presence, summaries, VRFs and return path.
- **Routing/switching lab checklist:** trunk allowed VLANs, PortChannel bundle state, STP root/roles, protocol interface/VRF and endpoint connectivity.
- **API/Python drill:** read method → URL → authentication → headers → payload → status/body; trace code exactly, paying attention to types, format widths, strings vs files.
- **Interpretation questions:** read the prompt for *what is being asked* (current behavior vs best correction); eliminate only with evidence. Avoid speculative changes or overfitting to Reddit's reported scenarios.
- **On-screen time checks:** practice keeping time for all question types; do not allow one confusing simulation to consume the remaining exam.

### 8.5 Short daily exam reasoning circuits

**Circuit R (10 min):** 3 OSPF or BGP configuration fragments; determine neighbor and route outcomes.

**Circuit S (10 min):** QoS policy/ACL/CoPP; trace four packets in specified direction and congestion state.

**Circuit P (10 min):** read one Python loop/list-of-dicts, one JSON file/string operation and one format specifier; predict stdout before executing.

**Circuit A (10 min):** analyze one broken REST API request and one EEM applet; explain fix and verification.

Run these in rotating order, increasing speed only after you consistently get the reasoning right.

---

## 9. Study tracking and graduation criteria

### 9.1 The blueprint matrix — tick every leaf objective

**Status key:** ⬜ Not started → 🟨 Learning → 🟦 Labbed / demonstrated → ✅ Mastered (passed independent delayed test).

| ID | Official v1.2 objective | Status | Evidence to save |
|---|---|---|---|
| 1.1.a | 2-tier, 3-tier, fabric, cloud design | ⬜ | Comparative diagrams |
| 1.1.b | Redundancy, FHRP, SSO | ⬜ | Failure and convergence plan |
| 1.2.a | Catalyst SD-WAN control/data planes | ⬜ | Component/packet flow diagram |
| 1.2.b | Catalyst SD-WAN benefits/limitations | ⬜ | Design decision memo |
| 1.3.a | SDA control/data planes | ⬜ | LISP/VXLAN/role flow |
| 1.3.b | Traditional campus interoperation | ⬜ | Border design and migration |
| 1.4 | Interpret QoS config | ⬜ | 20 traffic trace answers |
| 2.1.a | Type-1/type-2 hypervisors | ⬜ | Comparison |
| 2.1.b | Virtual machines | ⬜ | VM/container operations |
| 2.1.c | Virtual switching | ⬜ | tagged-frame pcap |
| 2.2.a | Configure/verify VRF | ⬜ | L11, L13, L14 |
| 2.2.b | Configure/verify GRE/IPsec tunnels | ⬜ | L12–L15 |
| 2.3.a | LISP | ⬜ | EID/RLOC lookup diagram |
| 2.3.b | VXLAN | ⬜ | VNI capture |
| 3.1.a | Troubleshoot 802.1Q trunks | ⬜ | L01 |
| 3.1.b | Troubleshoot EtherChannel | ⬜ | L02 |
| 3.1.c | RSTP/MST/root guard/BPDU guard | ⬜ | L03, L04 |
| 3.2.a | EIGRP vs OSPF routing concepts | ⬜ | Comparison and RIB example |
| 3.2.b | OSPFv2/v3 multi-area, summarize/filter | ⬜ | L05–L07 |
| 3.2.c | Directly connected eBGP | ⬜ | L08 |
| 3.2.d | PBR concepts | ⬜ | B08 |
| 3.3.a | NTP/PTP config interpretation | ⬜ | B09 + annotated samples |
| 3.3.b | NAT/PAT configuration | ⬜ | L09 |
| 3.3.c | HSRP/VRRP configuration | ⬜ | L10 |
| 3.3.d | Multicast: RPF/PIM/IGMP/SSM/bidir/MSDP | ⬜ | B10 + comparison chart |
| 4.1 | Diagnose via debug/ping/traceroute/SNMP/syslog | ⬜ | L16 + 5 incident reports |
| 4.2 | Flexible NetFlow | ⬜ | L17 |
| 4.3 | SPAN/RSPAN/ERSPAN | ⬜ | L18, L19 |
| 4.4 | IP SLA | ⬜ | L20 |
| 4.5 | Catalyst Center traditional/AI workflows | ⬜ | B11 + architecture runbook |
| 4.6 | NETCONF/RESTCONF | ⬜ | L21, L22 |
| 5.1.a | Device lines/local authentication | ⬜ | L23 |
| 5.1.b | AAA authentication/authorization | ⬜ | L24 |
| 5.2.a | ACL configuration | ⬜ | L25 |
| 5.2.b | CoPP configuration | ⬜ | L26 |
| 5.3 | REST API security | ⬜ | B12 + API threat model |
| 5.4.a | Threat defense | ⬜ | Threat-defense decision matrix |
| 5.4.b | Endpoint security | ⬜ | Identity & containment design |
| 5.4.c | Next-generation firewall | ⬜ | L7 policy scenarios |
| 5.4.d | TrustSec/MACsec | ⬜ | SGT matrix & MACsec mapping |
| 6.1 | Python script interpretation | ⬜ | 30 successful trace exercises |
| 6.2 | Construct valid JSON files | ⬜ | JSON validator and backup script |
| 6.3 | YANG principles | ⬜ | YANG tree/path example |
| 6.4 | Catalyst Center/SD-WAN Manager APIs | ⬜ | Auth/API runbook |
| 6.5 | REST API response status and payloads | ⬜ | 15 broken requests fixed |
| 6.6 | Construct EEM applets | ⬜ | L27, 8–12 applets |
| 6.7 | Agent vs agentless orchestration | ⬜ | Comparison + Ansible lab |

**Note:** This is the leaf-objective checklist, not just the six section percentages. Overlap (e.g. 1.1.b and 3.3.c) should be exploited: one well-designed experiment can supply evidence to both.

### 9.2 Competency scoring rubric

Score each blueprint objective from 0 to 4:

- **0:** unfamiliar; cannot explain vocabulary.
- **1:** can identify terms but not apply or interpret a scenario.
- **2:** can explain and answer guided questions; labs require notes/copying.
- **3:** can solve new scenarios and configure/diagnose independently with supporting evidence.
- **4:** can transfer knowledge to a novel design, reproduce from clean baseline, handle hidden faults, and explain both correct and incorrect alternatives after a delayed retest.

**Mastered = 3 minimum; critical implementation topics (VRF/GRE, trunk/EtherChannel/STP, OSPF, eBGP, AAA/ACL/CoPP, FNF/SPAN/IP SLA, API/JSON/Python) should reach 4.** Maintain a 0–4 score by each ID, not only an aggregate domain mark.

### 9.3 Progress log template

```markdown
## Weekly review — YYYY-MM-DD
- Focus objectives and time logged (theory / lab / troubleshoot / code):
- Newly mastered blueprint IDs with evidence links:
- Top three misunderstandings and proof that they are fixed:
- Faults I diagnosed without hints:
- Commands or APIs I had to look up:
- Flashcard retrieval accuracy / cards due:
- Practice exam by domain (fresh questions only):
- Old lab rebuilt from blank and validated:
- Next week's single highest-impact change:
```

### 9.4 Graduation test before scheduling the exam

- [ ] Every v1.2 leaf objective is at least **3/4** and every high-risk configure/troubleshoot objective is at **4/4**.
- [ ] Have built and saved **all supported Tier A labs** and logged legitimate platform-related substitutes.
- [ ] Complete **C01, C02 and C03** from a hidden broken starting state without external help; document independent test results.
- [ ] Build at least two portfolio projects with clean designs, failure injection, security/negative tests, rollback and automation.
- [ ] Understand **both** modern/legacy SD-WAN naming and Cisco-specific NGFW, Catalyst Center, TrustSec and SD-Access terminology.
- [ ] Confidently solve novel Python/JSON format/loop/exception, QoS/ACL/CoPP packet reasoning, and API request debugging tasks.
- [ ] Score consistently on multiple **unseen**, independent and legitimate timed practice exams; no unremediated weak domain.
- [ ] Recheck Cisco blueprint for a newer revision; verify test center requirements and rules; book only when readiness indicators are reliable.

---

## 10. Resources and reference links

> **Source hierarchy:** (1) current Cisco blueprint and release notes, (2) Cisco configuration guides and Design Zone documents, (3) structured courses/books and official training, (4) lab evidence and independent practice tests, (5) Reddit anecdotes as *ideas*, not exam guarantees. Cisco documentation and sandbox availability change; check device/OS/API software release every time.

### Official exam and primary documentation

- [ENCOR exam page](https://www.cisco.com/site/us/en/learn/training-certifications/exams/encor.html) — scope, duration and scheduling.
- [ENCOR v1.2 exam topics (PDF)](https://learningcontent.cisco.com/documents/marketing/exam-topics/350-401-ENCORE-v1.2.pdf) — **single canonical checklist**.
- [CCNP v1.1-to-v1.2 release notes](https://learningcontent.cisco.com/documents/marketing/exam-topics/CCNP_Enterprise_v1.1_and_1.2_Release_Notes.pdf) — removal of standalone wireless topics and terminology updates (effective 2026-03-19).
- [Cisco ENCOR official training](https://www.cisco.com/site/us/en/learn/training-certifications/training/courses/encor.html) — explicitly notes that some course materials still have earlier-version wireless content to skip for v1.2.
- [Cisco Catalyst SD-WAN Design Guide](https://www.cisco.com/c/en/us/td/docs/solutions/CVD/SDWAN/cisco-sdwan-design-guide.html) — planes, controller roles and design limits.
- [Cisco SD-Access Design Guide](https://www.cisco.com/c/en/us/td/docs/solutions/CVD/Campus/cisco-sda-design-guide.html) — fabric edge/border/control, LISP, VXLAN, wireless and legacy interoperation.
- [Cisco GRE source/destination VRF guide](https://www.cisco.com/c/en/us/td/docs/switches/lan/c9000/lyr3-fwd/gre/gre-configuration-guide/m-gre-tunnel-ip-source-and-destination-vrf-membership.html) — **platform-specific** outer/inner VRF distinction.
- [Catalyst Center authentication](https://developer.cisco.com/docs/catalyst-center/authentication/) — POST token endpoint, initial Basic Auth, X-Auth-Token.
- [Catalyst Center API sandboxes](https://developer.cisco.com/docs/catalyst-center/sandboxes/) and [DevNet Sandbox portal](https://developer.cisco.com/docs/sandbox/) — safe real-world API practice.
- [Cisco exam confidentiality/policies](https://www.cisco.com/site/us/en/learn/training-certifications/exams/policies.html).

### Labs, tools, programming and practice

- [Containerlab official documentation](https://containerlab.dev/) and [supported NOS kinds](https://containerlab.dev/manual/kinds/) — Docker/VM lab orchestration.
- [Containerlab Cisco IOL kind](https://containerlab.dev/manual/kinds/cisco_iol/) and [Cisco 8000V kind](https://containerlab.dev/manual/kinds/vr-c8000v/) — node resources, config and limitations; **check licensing**.
- [Cisco Modeling Labs image license note](https://developer.cisco.com/docs/modeling-labs/vm-images-for-cml-labs/) — CML reference images not generally licensed for use outside CML.
- [Cisco Modeling Labs free tier](https://developer.cisco.com/docs/modeling-labs/cml-free/) — useful fallback for Cisco image/license constraints; check current node and image limitations.
- [Boson ENCOR ExSim](https://boson.com/product/exsim-max-for-cisco-350-401-encor/) — practice tests and explanations; confirm current v1.2 coverage.
- [Python tutorial](https://docs.python.org/3/tutorial/), [Python format mini-language](https://docs.python.org/3/library/string.html#format-specification-mini-language) and [Python JSON module](https://docs.python.org/3/library/json.html).
- [IETF RESTCONF RFC 8040](https://www.rfc-editor.org/rfc/rfc8040) and [YANG RFC 7950](https://www.rfc-editor.org/rfc/rfc7950) — protocol/schema grounding.
- [Ansible documentation](https://docs.ansible.com/), [Puppet documentation](https://www.puppet.com/docs/), [Chef documentation](https://docs.chef.io/) and [Salt documentation](https://docs.saltproject.io/).
- [Wireshark](https://www.wireshark.org/docs/) and [FRRouting](https://docs.frrouting.org/) — captures, Linux routing/standard behavior demos.

### Reddit posts you supplied — reviewed and useful, with boundaries

- [CCNP 350-401 whitepaper/resource compilation](https://www.reddit.com/r/ccnp/comments/1hojdw5/ccnp_350401_resources/) — large collection of Cisco references. **Caution:** post began before v1.2 and still contains wireless links that are now out of scope as standalone objectives; filter by current blueprint.
- [VRF in GRE tunnel discussion](https://www.reddit.com/r/ccnp/comments/1hmd025/vrf_in_gre_tunnel_question/) — useful distinction between underlay transport VRF and customer forwarding VRF; check actual IOS platform syntax against Cisco documentation.
- [GRE over VRF discussion](https://www.reddit.com/r/ccnp/comments/1lk9byn/gre_over_vrf/) — hands-on suggestions and explanation of tunnel endpoint reachability.
- [Pass/fail megathread with hochgebildet account](https://www.reddit.com/r/ccnp/comments/1sopcy4/comment/oguxrh1/) — anecdote about extensive study, Cisco-specific terminology and uneven practice test experience. **Not** evidence of a guaranteed number or type of your future exam items.
- The additional first-hand advice copied into the conversation highlights Python formatting, files/JSON, Postman API errors, EEM applets, NGFW, and security/AAA alongside classic route/switch lablets. Those are incorporated as **extra practice emphasis**, never represented as official weight changes.

### Recommendations on courses/books

Choose **one main teaching resource** (Cisco U, Jeremy's IT Lab CCNP material if aligned, Arash Deljoo, a Cisco Press OCG, INE or another reputable source), then use the Cisco blueprint as your audit. An older OCG is still useful for fundamentals but can overrepresent old wireless scope or omit recent terminology; explicitly map chapters against v1.2. Use vendor design/configuration guides as the final arbiter when courses disagree. Favor legal access to books/PDFs. Do not buy multiple subscriptions until a diagnostic reveals the specific benefit.

### A note on ethics and quality

Do **not** use questions claimed to be copied from the live Cisco exam, whether called "exam experiences", "verified questions", "braindumps", "recent test-taker reports" or any other label. The plan uses ordinary skills and subject-matter descriptions, not reconstructed confidential exam items. A real engineer should be able to diagnose unfamiliar networks without having previously seen the exact question.

---

## 11. Study resource stack, NotebookLM, Boson ExSim and the daily template

### 11.1 What each resource is for

| Resource | Role in this plan | How it's used day to day | Cost / caution |
|---|---|---|---|
| **Arash Deljoo CCNP ENCOR v1.2 course** (~155 h, 30 sections; ~140 h without wireless) | **Primary teacher** (the passer's main course) | One section (or part of one) most weekdays, followed by that section's built-in quiz. Wireless sections skipped — see §12. | Paid course; often discounted. Watch at 1.0× first time, 1.25–1.5× on rewatch. |
| **Cisco Press ENCOR OCG** (legally purchased e-book/print) | Reference + **NotebookLM source** | Look up anything the video glossed over; upload the PDF to NotebookLM to generate quizzes. | The passer used a free PDF; use a copy you bought (the e-book also unlocks the Pearson practice exams). Skip its wireless chapters. |
| **Pearson Test Prep exams** (come with the OCG) | Low-stakes topic quizzes + checkpoint | Chapter-filtered sets after a topic; checkpoint D118. | Included with the book. |
| **Cisco docs** (config guides, CVDs, product pages) | Final arbiter when sources disagree; whitepaper notebook | Friday reading blocks; links in §10. | Free. |
| **Your own labs** (Containerlab with properly licensed images, or CML) | Build → observe → break → fix (§3) | Wed build, Thu break/fix, Sat timed rebuilds, using the L/B/C IDs from §5. | Respect the CML licensing note in §3.2. |
| **Boson ExSim-Max for ENCOR** | **Exam-style lablets, repeated "over and over"** + 4 full practice exams | Simulation-filtered labs every Thursday and Saturday from W3; full exams A–D at the checkpoints in §11.4. | Paid; confirm v1.2 coverage. |
| **NotebookLM + Gemini** | **Endless active-recall quizzes** from the OCG and the whitepapers (the passer's method) | 10–15 min quiz most days using prompt templates T1–T8 (§11.3). | Free tiers work; verify every answer (rules below). |
| **Anki** (or another SRS) | Long-term retention | 15–20 min of due reviews **every day**, before new material. | Free (desktop/Android). |
| **Python learning** | Fills the gap: Arash's course has API/NETCONF/EEM sections but **no dedicated Python section** | Daily 15–20 min track (§11.6) + Appendix B. Sources: [Python tutorial](https://docs.python.org/3/tutorial/), Corey Schafer's Python videos (incl. file objects and JSON), *Automate the Boring Stuff with Python* (free online). | Free. |
| **Postman (or Bruno)** + **Cisco DevNet sandboxes** | Break REST requests on purpose; Catalyst Center + SD-WAN Manager APIs | From W20; then 1–2 times a week in the daily track. | Free. |
| **Cisco U practice exam** | Optional late check, mostly for its (harder) labs | D242. | Reported to have kept Wi-Fi questions after v1.2 launched and to stop the attempt once a pass is impossible; check current version first. |
| **"CCNP ENCOR Safeguard Plus"** (recommended by one passer) | **Not scheduled** | — | I couldn't verify what this product is. The passer said its questions "seem very similar to real exam" — that's a warning sign of recalled exam content. If it advertises real/actual exam questions, skip it for the same reason §8.1 gives for Examice. If it's original labs and questions, it can replace some Boson sessions. |
| **Examice** | **Not scheduled** | — | See §8.1. |

### 11.2 Automation emphasis — what the first-hand reports mean for the schedule

The passer stressed that a large share of the 53 non-lab questions were automation: **drag-and-drops for Python, JSON, EEM and Ansible/Puppet/Chef/SaltStack; cut-off scripts where you choose the missing block; Python `format()` puzzles; a broken Postman POST to fix; Catalyst Center API steps (token = `POST` with Basic Auth, then `X-Auth-Token`).** This plan responds by:

1. **Daily Python from Day 1** (15–20 min, 252 days) instead of a late automation chapter.
2. **Moving the automation videos to W20–W21**, then revisiting them weekly with Circuit P and Circuit A (§8.5) every Saturday until the exam.
3. **Postman break-it sessions** (B12) with the exact failure types reported: missing/expired token, wrong method, wrong `Content-Type`, malformed JSON, wrong URI.
4. **EEM written from blank** 8–12 times (6.6 says *construct*), plus action-order drag-drill practice.
5. **A tool-comparison drill** (Ansible/Puppet/Chef/SaltStack: agent model, push/pull, language, artifacts, master/minion, multi-master) as a weekly drag-and-drop with NotebookLM T6.
6. **Two "very hard" generic Python snippets** were reported, so the track includes non-networking Python (mutability, scope, loops with `break/continue`, string slicing, integer division, exceptions).

### 11.3 NotebookLM + Gemini active-recall system

**Set up once (D1):** create four notebooks.

| Notebook | Sources to add | Used for |
|---|---|---|
| **N1 · ENCOR-OCG** | Your OCG PDF (split into chapter PDFs if it's too large for one source), the v1.2 blueprint PDF, the v1.2 release notes | Concept quizzes for every topic (the passer's main notebook) |
| **N2 · ENCOR-Whitepapers** | Cisco SD-Access and SD-WAN design guides, GRE VRF guide, the two NGFW must-read pages, Catalyst Center API auth docs, threat-defense/TrustSec/MACsec product pages, configuration-guide chapters you read on Fridays (the whitepaper list from the r/ccnp resources thread, filtered to v1.2 scope) | Cisco-terminology/buzzword quizzes — the area a 500-hour candidate said blindsided him |
| **N3 · ENCOR-MyNotes** | Your one-page summaries, lab `lessons.md` files, postmortems, error log | Quizzes on *your* weak spots; teach-back grading |
| **N4 · Automation** | Python docs pages for `json`, the format mini-language and file I/O; your own scripts; RESTCONF/NETCONF RFC excerpts; EEM config guide chapter; Ansible/Puppet/Chef/Salt docs overview pages | Python/JSON fill-in-the-blank, cut-off scripts, EEM ordering, tool matching |

NotebookLM's Studio panel may offer built-in **Quiz** and **Flashcards** generators — use them when present; otherwise use the chat prompts below. The passer also used **Gemini with a notebook referenced** to "keep generating more and more quizzes" interactively; if your Gemini plan can't reference a NotebookLM notebook, upload the same PDFs to a Gemini chat instead.

**Prompt templates used in §13 (copy into the notebook chat; replace `<topic>`):**

- **T1 — Topic quiz:** "Using only my sources, quiz me with 10 original multiple-choice questions on `<topic>`, one at a time. Wait for my answer. After each answer, explain why the correct option is right and why each distractor is wrong, and cite the source passage. At the end, list the concepts I missed."
- **T2 — Find the fault:** "Write an original Cisco IOS XE configuration snippet for `<topic>` that contains exactly one realistic mistake. Show it, ask me to find and fix the mistake, then grade me and explain which `show` command would reveal the problem."
- **T3 — Read the output:** "Create an original `<show command>` output for a scenario involving `<topic>`. Ask me 3 questions about what it means (state, cause, next step). Grade and explain."
- **T4 — Code blank:** "Write an original short Python script about `<topic>` with one blank (`____`) and 4 options. Ask me which option fills it and what the script prints. Show the exact output, including spaces and padding." → **Always run the script yourself before trusting the answer.**
- **T5 — Cumulative mix:** "Give me 20 mixed questions across `<list of covered topics>`, weighted towards these weak areas: `<from error log>`. One at a time, explain after each."
- **T6 — Drag-and-drop:** "Give me 6–8 items and 3–4 categories about `<topic>` (for example SD-WAN components → planes, or tools → agent/agentless, push/pull, language). Ask me to match them, then grade."
- **T7 — Draft cards:** "Draft 10 Anki cards as `front;back` lines from the source section on `<topic>`. One testable idea per card, include the *why* in the back, cite the page." → **Edit them, verify them, then import.** Don't import unedited.
- **T8 — Teach-back:** "I will explain `<topic>` in my own words. Grade my explanation against the sources and list any misconceptions or missing points." (Use the audio overview feature for extra listening on commutes if you like.)

**Verification rules (non-negotiable):**
1. If an AI answer disagrees with a Cisco doc, your lab, or the Python interpreter, **the doc/lab/interpreter wins** — and that disagreement becomes a card.
2. Never card a "fact" you haven't confirmed in a source or lab.
3. Run every AI-generated Python snippet before memorising its output.
4. Don't ask the AI for "real exam questions"; ask for original scenarios (§7.3).

### 11.4 Boson ExSim plan

- **Simulation-only sessions ("labs over and over"):** in a new practice session, filter by question type **Simulation** (and by the objective you've covered). Do these every **Thursday (1–2 labs)** and **Saturday (2–4 labs)** from W3. Repeating a lab is fine — the skill is the point. Time yourself and log times.
- **Mark the Boson OSPF/ACL lab** the passer mentioned (fix an ACL so OSPF works) and repeat it in W32–W33 and the final weeks.
- **Keep full exams fresh** (§8.2): don't run multiple-choice topic quizzes from Boson during the learning months — use Pearson and NotebookLM for those. Full exams are scheduled:
  - **Exam A — D181 (W26), study mode:** mid-plan diagnostic (security/assurance not yet covered — mark those as "not yet studied").
  - **Exam B — D232 (W34), simulation mode, timed.**
  - **Exam C — D239 (W35), simulation mode, timed.**
  - **Exam D — D246 (W36), simulation mode, timed.**
  - After each: review every item (right or wrong) the next day; log misses with the §8.3 template; re-lab the concept in your own environment.
- **Readiness signal:** the §8.2 benchmark (≥ 85% on fresh questions, no domain below 75–80%) on Exams C and D, plus the §9.4 graduation test.

### 11.5 The daily session template, weekly rhythm and how to read a day

**Daily constants (every day, ~30–35 min, before anything else):**
1. **Anki** — all due reviews (~15–20 min).
2. **🐍 Automation track** — the day's Python/JSON/API drill (~15 min, §11.6). Predict output first, then run it.

**Then the day's main block (the line in §13):**

| Symbol | Meaning |
|---|---|
| 🎥 | **Learn**: Arash section (with its quiz) and/or the OCG/Cisco doc reading named |
| 🧪 | **Lab**: your own lab (IDs from §5: L = Tier A, B = Tier B, C = Tier C, P = §6.2 projects) and/or **Boson ExSim** simulations |
| 🃏 | **Flashcards**: write ~N cards *the same day*, from what you just learned/labbed (seed ideas given; tag `blueprint::topic::type`) |
| 🧠 | **NotebookLM/Gemini**: which notebook (N1–N4) and prompt (T1–T8) |
| 🐍 | **Automation drill** for the day |
| 📝 | Notes, summaries, logs |

**Weekly rhythm (~14 h):** Mon/Tue learn (1.5–2 h) · Wed build lab (1.5–2 h) · Thu learn or break/fix + Boson (1.5–2 h) · Fri lighter learn/read (1–1.5 h) · **Sat long session** (3–4 h: lab + Boson sims + Circuits P/A) · **Sun review** (1.5 h). If a day runs over, finish it the next day — don't skip the cards or Anki.

**Sunday review routine (every week, referred to as "Weekly review" in §13):**
1. Anki due reviews; rewrite or delete leech cards.
2. 🧠 **T5 cumulative quiz** (20 Q) in N1 + N2 on everything covered so far, weighted to weak areas.
3. Fill in the §9.3 progress log; score every blueprint ID touched this week 0–4 (§9.2); update the §9.1 matrix.
4. Update the error log (§8.3); turn each confidently-wrong item into a card.
5. Preview next week; ask for any topology files you need (e.g. "give me the Containerlab topology for L05").

**Lab session protocol (Wed/Thu/Sat):** follow the golden workflow in §3.4 — deploy → baseline → configure from blank → verify (tiers A–C) → inject single fault from §5's library → diagnose with `show` first → minimal fix → save (`copy running-config startup-config`) → destroy/redeploy (tier E) → commit. Harvest `show` outputs into cards.

### 11.6 Daily automation track (Python · JSON · APIs)

| Weeks | Focus | Example drill |
|---|---|---|
| W1–W2 | Setup, `print`, variables, types, strings, f-strings | `type(3/2)`, `"Gi0/1".split("/")` |
| W3–W4 | Lists, slicing, dicts, nested data | `inventory[0]["hostname"]` |
| W5–W6 | `if/elif/else`, comparisons, truthiness, `for`, `range`, `enumerate`, `zip` | Loop a list of interface dicts and print the down ones |
| W7–W8 | (holiday-light) `while`, `break/continue` | Predict-the-output only |
| W9 | Functions, `return`, scope, default arguments | Write `is_up(intf)` and predict 3 calls |
| W10–W11 | **`format()` mini-language**: fill/align/width, precision, `%`, `#`, `,`, types | Appendix B table rebuilt from memory |
| W12 | Files: `open` modes, `read/readline/readlines/write`, `with` | Write and read back `backup.txt` |
| W13 | **JSON**: `dump/dumps/load/loads`, `JSONEncoder().encode`, `JSONDecoder().decode`, `indent`, `sort_keys`, invalid JSON | Fill-the-blank `json.____` |
| W14 | `try/except/else/finally`, common exceptions | Predict which block runs |
| W15 | Comprehensions, `sorted`, sets, `.get()` | Parse a RESTCONF-style payload |
| W16 | Modules, `ipaddress`, classes basics, `is` vs `==`, mutability | "Weird Python" day |
| W17 | Netmiko: run `show` commands against your lab, save JSON | P6 seed |
| W18–W19 | XML basics (`xml.etree.ElementTree`), NETCONF-style payloads; YAML basics | Read an XML interface list |
| W20–W21 | **`requests`**, Postman, Catalyst Center token flow, RESTCONF, ncclient, EEM | Break requests on purpose; write the fix |
| W22–W26 | Cut-off scripts (choose the missing block), exam-style drag-and-drops, pytest for your scripts | 5 items/day |
| W27–W33 | Rotating Circuit P / Circuit A (§8.5) + one Ansible/EEM/API item per week | 10 min/day |
| W34–W36 | Timed mixed sets (15–30 items) | Exam pace |

## 12. Arash Deljoo course map (non-wireless)

Every non-wireless section of the course, the blueprint ID it serves, and the day it's scheduled. Each section's own quiz is taken straight after watching it. **Ext** = beyond the v1.2 blueprint wording but taught in the course and useful in real networks (kept, as you asked, at lower priority for cards).

| Arash section | Length | Blueprint | Day(s) |
|---|---:|---|---|
| Course Introduction | 0:09 | — | D1 |
| Fundamentals of Data Communication and Network Architecture | 0:57 | prereq, 1.1 | D2 |
| Layer 3 Switching and IP Forwarding Fundamentals | 1:04 | 3.2 prereq | D8 |
| Network Forwarding Architectures and CEF | 1:14 | 3.2 prereq | D9 |
| High Availability and SDM in Network Switching | 0:32 | 1.1.b | D11 |
| IPv4 Addressing, CIDR & NAT — *addressing/CIDR part* | ~1:15 | prereq | D12 |
| VLANs and Trunking Fundamentals | 1:17 | 3.1.a | D15 |
| Advanced VLAN Configuration and Layer 2 Diagnostics | 1:02 | 3.1.a | D16 |
| Dynamic Trunking Protocol (DTP) Fundamentals | 1:24 | 3.1.a | D18 |
| VLAN Trunking Protocol (VTP) Fundamentals | 1:22 | 3.1.a (ext) | D19 |
| Etherchannel Bundle or Aggregation Fundamentals | 2:00 | 3.1.b | D22 |
| EtherChannel Modes, Load Balancing, and L3 Aggregation (+ EtherChannel Quiz) | 1:10 | 3.1.b | D23 |
| Spanning Tree Protocol (STP) Fundamentals | 1:35 | 3.1.c | D29 |
| Advanced Spanning Tree and PVST+ | 1:49 | 3.1.c | D30 |
| STP Root Bridge and Real-World Implementation | 1:25 | 3.1.c | D32 |
| STP Convergence and Optimization Techniques | 2:34 | 3.1.c | D36–D37 |
| STP Topology Tuning and Optimization | 0:39 | 3.1.c | D38 |
| STP Protection and Loop Prevention Mechanisms | 1:16 | 3.1.c | D39 |
| Rapid Spanning Tree Protocol (RSTP) Fundamentals | 1:14 | 3.1.c | D43 |
| Multiple Spanning Tree Protocol (MSTP) Operation | 2:05 | 3.1.c | D50–D51 |
| Static Routing and Routing Table Fundamentals | 1:44 | 3.2 | D57 |
| Advanced Static Routing and Default Route Operation | 2:03 | 3.2 | D58 |
| IPv6 Static and Default Routing Fundamentals | 1:07 | 3.2 (dual stack) | D60 |
| Dynamic Routing Protocols and Routing Algorithm | 2:26 | 3.2.a | D61–D62 |
| EIGRP Fundamentals and Core Concepts | 1:30 | 3.2.a | D64 |
| EIGRP Operations and Neighbor Relationship | 1:29 | 3.2.a | D65 |
| EIGRP Metrics and Path Calculation | 1:53 | 3.2.a | D67 |
| EIGRP Route Selection and Convergence Process | 1:45 | 3.2.a | D69 |
| EIGRP Equal and Unequal Cost Paths Load Balancing | 0:53 | 3.2.a | D71 |
| EIGRP Route Summarization and Optimization | 1:27 | 3.2.a | D72 |
| OSPF Routing Fundamentals and Area Concepts | 1:15 | 3.2.a/b | D74 |
| OSPF Configuration Methods and Router ID Fundamentals | 1:22 | 3.2.b | D75 |
| OSPF Neighbor Adjacency and Authentication | 1:13 | 3.2.b | D76 |
| OSPF Neighbor States and Database Exchange Process | 1:03 | 3.2.b | D78 |
| OSPF DR and BDR Election Process | 0:46 | 3.2.b | D78 |
| OSPF LSA Type-1 and Link-State Fundamentals | 0:49 | 3.2.b | D80 |
| OSPF LSA Type-2 and Transit Network Operation | 0:37 | 3.2.b | D80 |
| OSPF LSA Type-3 and Inter-Area Route Summarization | 0:33 | 3.2.b | D81 |
| OSPF Route Types and Path Selection Rules | 0:15 | 3.2.b | D81 |
| OSPF Default Route Advertisement and Control | 0:33 | 3.2.b | D81 |
| OSPF Cost and Path Selection Rules | 0:54 | 3.2.b | D82 |
| OSPF Inter-Area Route Summarization | 0:26 | 3.2.b | D85 |
| OSPF Network Types and Operations | 0:47 | 3.2.b | D85 |
| OSPF Route Filtering Techniques | 0:34 | 3.2.b | D87 |
| OSPFv3 Operation and Implementation | 1:15 | 3.2.b | D88 |
| OSPFv3 LSA Types and Flooding Scope | 1:36 | 3.2.b | D89 |
| OSPFv3 Address Family Operation | 0:15 | 3.2.b | D90 |
| Access Control Lists (ACLs) Types and Applications | 0:41 | 5.2.a, 3.2.d | D92 |
| IP and IPv6 Prefix Lists Fundamentals | 1:17 | 3.2.b/c (filtering) | D93 |
| Route-Map Fundamentals and Match Logic | 1:33 | 3.2.d, 3.2.c | D94 |
| Policy-Based Routing (PBR) with ACL Implementation | 0:46 | 3.2.d | D95 |
| Policy-Based Routing (PBR) with Packet Length Implementation | 0:13 | 3.2.d | D95 |
| BGP Fundamentals and Path Vector Operation | 1:38 | 3.2.c | D99 |
| BGP Timers, Neighbor Relationships, and State Machine | 2:00 | 3.2.c | D100 |
| Injecting Routes into the BGP Table | 0:53 | 3.2.c | D102 |
| BGP Route Summarization and Aggregation | 1:01 | 3.2.c | D103 |
| Multiprotocol BGP (MP-BGP) for IPv6 Routing | 1:03 | 3.2.c (dual stack) | D104 |
| BGP Route Filtering and Policy Control | 2:27 | 3.2.c (ext) | D106–D107 |
| BGP Session Clearing and Soft Reset Mechanisms | 0:44 | 3.2.c | D108 |
| BGP Communities and Route Control | 1:33 | ext | D109 |
| BGP Path Selection with Longest Prefix Match | 0:19 | 3.2.c | D110 |
| BGP Best Path Selection and Weight Attribute | 0:48 | 3.2.c | D110 |
| BGP Best Path Selection and Local Preference Attribute | 0:52 | 3.2.c | D111 |
| BGP Path Preference for Locally Injected Routes | 0:11 | 3.2.c | D111 |
| BGP Best Path Selection with AIGP Metric | 0:50 | ext | D113 |
| BGP Best Path Selection and AS-Path Attribute | 0:29 | 3.2.c | D113 |
| BGP Best Path Selection and Origin Code Attribute | 0:25 | 3.2.c | D114 |
| BGP Best Path Selection and MED Attribute | 0:31 | 3.2.c | D114 |
| BGP Best Path Selection eBGP over iBGP Preference | 0:19 | 3.2.c | D114 |
| BGP Best Path Selection Based on IGP Metric | 0:11 | 3.2.c | D115 |
| BGP Best Path Selection Oldest eBGP Path Preference | 0:15 | 3.2.c | D115 |
| BGP Best Path Selection Using Router ID | 0:07 | 3.2.c | D115 |
| BGP Best Path Selection by Neighbor IP Address | 0:10 | 3.2.c | D115 |
| BGP Path Attribute Types and Categories | 0:10 | 3.2.c | D115 |
| BGP Autonomous System (AS) Numbers and Removal | 0:19 | 3.2.c | D116 |
| BGP Multihoming and Failover Routing | 0:14 | 3.2.c (ext) | D116 |
| Virtual Routing and Forwarding (VRF) Lite Fundamentals | 1:38 | 2.2.a | D120 |
| Generic Routing Encapsulation (GRE) Fundamentals | 1:28 | 2.2.b | D122 |
| IPsec & IKE Fundamentals | 0:26 | 2.2.b | D127 |
| IPsec AH & ESP Protocols | 0:19 | 2.2.b | D127 |
| IPsec & IKE Deep Dive | 0:28 | 2.2.b | D127 |
| Site-to-Site IPsec GRE Tunneling | 0:25 | 2.2.b | D128 |
| IPsec VTI and IKE Fundamentals | 0:36 | 2.2.b | D128 |
| APIs and Network Programmability | 1:16 | 6.4, 6.x | D134 |
| RESTful APIs and Data Serialization | 1:03 | 6.2, 6.5 | D135 |
| REST API Response Codes and Payload Interpretation | 0:23 | 6.5 | D137 |
| REST API Security Fundamentals | 0:23 | 5.3 | D137 |
| NETCONF and RESTCONF Configuration and Verification | 0:35 | 4.6, 6.3 | D142 |
| Network Automation and Embedded Event Manager (EEM) | 1:07 | 6.6 | D145 |
| Configuration Management and Automation Tools | 0:38 | 6.7 | D146 |
| IP Multicast Essentials | 1:40 | 3.3.d | D148 |
| IGMP and IGMP Snooping Fundamentals | 1:53 | 3.3.d | D149 |
| PIM Dense Mode Fundamentals | 1:04 | 3.3.d (contrast) | D151 |
| PIM Sparse Mode Fundamentals | 1:09 | 3.3.d | D152 |
| PIM Designated Router (DR) and PIM Forwarder | 0:50 | 3.3.d | D155 |
| PIM Rendezvous Point (RP) Mechanisms Static RP, Auto-RP & BSR | 0:54 | 3.3.d | D155 |
| Advanced Multicast Concepts - SSM, Bidir-PIM, and MSDP | 0:23 | 3.3.d | D156 |
| Cisco Device Time Management & NTP Fundamentals | 1:40 | 3.3.a | D158 |
| Precision Time Protocol (PTP) Fundamentals | 0:25 | 3.3.a | D159 |
| Hot Standby Router Protocol (HSRP) Fundamentals | 1:12 | 3.3.c, 1.1.b | D162 |
| Virtual Router Redundancy Protocol (VRRP) Fundamentals | 0:43 | 3.3.c | D163 |
| Gateway Load Balancing Protocol (GLBP) Fundamentals | 0:41 | ext (contrast) | D163 |
| IPv4 Addressing, CIDR & NAT — *NAT part* | ~1:12 | 3.3.b | D165 |
| QoS Fundamentals Delay, Jitter & Packet Loss | 1:21 | 1.4 | D169 |
| QoS Models Best Effort, IntServ & DiffServ | 0:32 | 1.4 | D170 |
| QoS Classification & L3 Marking | 1:41 | 1.4 | D171 |
| QoS Classification & L2 Marking | 1:00 | 1.4 | D172 |
| QoS Classification & Marking Across All Layers | 0:55 | 1.4 | D173 |
| Modular QoS CLI (MQC) Foundations / Classification / Marking | 0:41 | 1.4 | D176 |
| QoS Traffic Policing & Shaping Fundamentals | 0:18 | 1.4 | D176 |
| QoS Policing Single-Rate Two-Color / srTCM / MQC Policing / trTCM | 0:52 | 1.4 | D177 |
| QoS Congestion Management / CBWFQ & LLQ / Congestion Avoidance / Advanced CBWFQ & HQoS | 1:12 | 1.4 | D178 |
| LISP Architecture and IP Mobility | 0:49 | 2.3.a | D183 |
| LISP Control Plane Operations | 1:21 | 2.3.a | D184 |
| LISP Packet Encapsulation | 0:39 | 2.3.a | D185 |
| LISP Interworking with Non-LISP Sites | 1:38 | 2.3.a | D186 |
| VXLAN and Traditional Layer 2 / VXLAN Architecture / VXLAN Control Planes and SD-Access | 0:30 | 2.3.b, 1.3 | D187 |
| Server Virtualization and Data Center Networking | 0:24 | 2.1 | D188 |
| Server Virtualization and Virtual Networking | 0:25 | 2.1 | D188 |
| Network Functions Virtualization (NFV) Architecture | 0:47 | 2.1 | D188 |
| Hierarchical LAN Design Model | 0:17 | 1.1.a | D190 |
| High Availability in Network Design | 0:23 | 1.1.b | D190 |
| Enterprise Network Architecture Designs | 0:42 | 1.1.a | D191 |
| Cloud Network Design | 0:39 | 1.1.a | D191 |
| Software-Defined Access (SD-Access) Architecture and DNA Center | 0:57 | 1.3, 4.5 | D193 |
| Cisco SD-Access Architecture | 1:09 | 1.3 | D194 |
| Cisco SD-WAN Architecture and Solutions | 2:44 | 1.2 | D197–D198 |
| Updates for Cisco SD-Access and SD-WAN | 0:16 | 1.2, 1.3 | D199 |
| ICMP and Network Connectivity Troubleshooting | 1:38 | 4.1 | D201 |
| IPv4 Header and Traceroute Analysis | 0:55 | 4.1 | D202 |
| SNMP Architecture and Operations | 0:57 | 4.1 | D204 |
| Syslog and System Message Logging | 1:07 | 4.1 | D205 |
| NetFlow Monitoring and Analysis | 0:21 | 4.2 | D207 |
| Flexible NetFlow Architecture and Operation | 0:30 | 4.2 | D207 |
| SPAN and Traffic Monitoring Fundamentals | 0:38 | 4.3 | D208 |
| RSPAN Implementation and Operation | 0:18 | 4.3 | D208 |
| Encapsulated Remote SPAN (ERSPAN) | 0:18 | 4.3 | D208 |
| IP SLA and Object Tracking Operations | 0:58 | 4.4 | D211 |
| Cisco DNA Center Assurance and Client Insights | 0:13 | 4.5 | D213 |
| Network Assurance Updates | 0:24 | 4.5 | D213 |
| Cisco Threat Defense and Security Solutions | 1:12 | 5.4.a, 5.4.c | D214 |
| Network Access Control and Authentication Technologies | 0:55 | 5.4.b, 5.4.d | D215 |
| Standard IPv4 Access Control Lists (ACLs) | 1:25 | 5.2.a | D218 |
| Extended IPv4 Access Control Lists (ACLs) | 2:04 | 5.2.a | D219 |
| Port ACLs (PACLs) / VLAN ACLs (VACLs) / ACL Processing and dACLs | 0:52 | 5.2.a (ext) | D221 |
| Securing User Access and Password Encryption | 1:29 | 5.1.a | D222 |
| Privilege Levels and Role-Based Access Control (RBAC) | 0:19 | 5.1.a | D223 |
| Remote Access with Telnet and SSH | 1:53 | 5.1.a | D225 |
| Authentication, Authorization, and Accounting (AAA) | 1:07 | 5.1.b | D226 |
| Zone Based Firewall (ZBFW) | 0:58 | ext (contrast with 5.4.c) | D228 |
| Control Plane Policing (CoPP) | 0:55 | 5.2.b | D229 |

**Skipped (wireless, out of v1.2 scope):** Fundamentals of Wireless and RF Power · Wireless Data Transmission Techniques · Evolution of IEEE 802.11 Wi-Fi Standards · Free Space Path Loss and Signal Optimization · Wireless Network Architecture Models · Wireless LAN Controller Discovery and Redundancy · Segmenting Wireless with AP Tagging · Antenna Properties and Radiation Patterns · Antenna Types and Applications · Wireless Roaming Mechanisms · Wireless Mobility Architecture · Wireless Device Location · Open Authentication · WPA Security · EAP Authentication and the Four-Way Handshake · Web Authentication · Wireless Client Connectivity Troubleshooting · Wireless Access Point Connectivity Troubleshooting (and their quizzes).
*Optional exceptions:* the first part of **Wireless Network Architecture Models** helps with the **fabric WLC/fabric AP** idea in SD-Access (D195), and the EAP part of **EAP Authentication and the Four-Way Handshake** helps with 802.1X/EAP for 5.4.b (D215). Skip the RF/802.11 detail.

**Blueprint gaps the course doesn't teach as its own section — filled elsewhere in §13:** Python (6.1, daily track + W20 deep work), constructing JSON files (6.2, W13 track + D135–D139), YANG depth (6.3, D141–D143), SD-WAN Manager API (6.4, D200), Catalyst Center AI-powered workflows (4.5, D213 with current Cisco product pages), TrustSec/MACsec depth (5.4.d, D215–D216 with design guides), NGFW product framing (5.4.c, D214 must-reads).

## 13. Day-by-day schedule: D1 → D250 (exam day)

> Read §11.5 once for the symbols. Every day also starts with the **daily constants** (Anki + the 🐍 drill). Times are for the main block. Norwegian public holidays are marked 🎄/🐣/🇳🇴 and kept light. If you fall behind, slide the whole schedule — the order matters, the dates don't (§2: gates, not weeks).

### Phase 0 — Foundation and infrastructure

#### Week 1 · 9–15 Nov 2026 · Set up everything, take a baseline
*Goal: lab platform works, study system exists, baseline score recorded.*

- **D1 · Mon 9 Nov · 2 h**
  - 📝 Download the v1.2 blueprint + release notes (§10). Read §1–§3 of this README. Create the Git repo (§3.3 layout) and the error log (§8.3) and progress log (§9.3) files. Score every blueprint ID 0–4 (§9.2) honestly.
  - 🎥 Arash: *Course Introduction*.
  - 🧠 Create notebooks N1–N4 (§11.3); add the blueprint PDF to each, the OCG to N1.
  - 🃏 Install Anki; create deck `ENCOR` with tag scheme `blueprint::topic::type::difficulty` (§7.1). No cards yet.
  - 🐍 Install Python 3 + VS Code; make a venv; run `print("hello, ENCOR")`.
- **D2 · Tue 10 Nov · 2 h**
  - 📝 **Baseline diagnostic:** one Pearson OCG practice exam, untimed, closed notes. Record scores by domain; log the five most surprising misses.
  - 🎥 Arash: *Fundamentals of Data Communication and Network Architecture* + quiz.
  - 🃏 +8: OSI vs TCP/IP layers, encapsulation names (frame/packet/segment), unicast/multicast/broadcast, what a "plane" is (data/control/management).
  - 🐍 Variables and types: predict `type(3/2)`, `type(3//2)`, `type("10")`, `int("10") + 5`, then run.
- **D3 · Wed 11 Nov · 2 h**
  - 🧪 Platform decision (§3.2): fill the feature-support matrix for each candidate (Containerlab + licensed IOL/IOL-L2/Catalyst 8000V, or CML Free/Personal, or FRR for standards demos). Install Docker + Containerlab; deploy two Linux/FRR nodes; ping IPv4/IPv6; `tcpdump` the pings.
  - 🃏 +4: container vs VM, Linux bridge, veth pair, management network vs data links.
  - 🐍 Strings: `"GigabitEthernet0/1".upper()`, `.lower()`, `.split("t")`, `" R1 \n".strip()` — predict, run.
- **D4 · Thu 12 Nov · 2 h**
  - 🧪 Bring up your first Cisco node on your chosen platform; SSH in; `show version`; configure a hostname; `copy run start`; destroy and redeploy; confirm the config came back (validation tier E).
  - 🧪 **Boson ExSim:** install, start a practice session filtered to **Simulation**, open one lab just to learn the interface (don't score it).
  - 🐍 Lists: `vlans = [10, 20, 30, 99]` — predict `vlans[0]`, `vlans[-1]`, `vlans[1:3]`, `len(vlans)`, `99 in vlans`.
- **D5 · Fri 13 Nov · 1.5 h**
  - 📝 Prerequisite refresh (§1.3): 30 min subnetting/VLSM speed drill; IPv6 address types (GUA, ULA, link-local, multicast), EUI-64, NDP/RA.
  - 🧠 N1·T1 "IPv4 subnetting and IPv6 addressing fundamentals".
  - 🃏 +10 from today's gaps only (e.g. /27 block size, FE80::/10, FF02::1).
  - 🐍 Dicts: `r1 = {"hostname": "R1", "mgmt": "10.0.0.1"}` — read, add `"os": "iosxe"`, loop `.items()`.
- **D6 · Sat 14 Nov · 3.5 h**
  - 🧪 Build a 3-router static-routing topology; collect `show ip route`; inject a wrong static route; fix it; write a one-page postmortem (§6.1 worksheet); commit to Git.
  - 🧪 Build your **toolbox container** (python3, requests, netmiko/scrapli, ncclient, pyang, ansible, pytest, tcpdump/tshark, iperf3, scapy, nfdump, snmp tools, rsyslog, chrony, FreeRADIUS, a TACACS+ daemon). You'll reuse it all year.
  - 🐍 First Netmiko script: connect to R1, run `show ip interface brief`, print the result.
- **D7 · Sun 15 Nov · 1.5 h** — **Weekly review** (§11.5).
  - 🧠 N1: ask for a briefing doc/study guide of the whole blueprint; skim it.
  - 🐍 Appendix B items 1–3 without running; then run and check.

#### Week 2 · 16–22 Nov 2026 · Forwarding, CEF, switching HA, addressing
*Goal: understand how a switch/router actually forwards; subnetting is fast.*

- **D8 · Mon 16 Nov · 1.5 h**
  - 🎥 Arash: *Layer 3 Switching and IP Forwarding Fundamentals* + quiz.
  - 🃏 +10: SVI vs routed port, `ip routing`, router-on-a-stick, why an SVI is down (no active port in VLAN / VLAN missing), ARP's role in forwarding.
  - 🧠 N1·T1 "inter-VLAN routing and Layer 3 switching".
  - 🐍 `if/elif/else`: given `status = "administratively down"`, print "shut", "down" or "up" with three branches.
- **D9 · Tue 17 Nov · 1.5 h**
  - 🎥 Arash: *Network Forwarding Architectures and CEF* + quiz.
  - 🃏 +12: process vs fast vs CEF switching, FIB vs RIB, adjacency table, CAM vs TCAM, punt/glean adjacencies, why CEF scales.
  - 🧠 N1·T3 output of `show ip cef` / `show adjacency`.
  - 🐍 `for` loop over `[{"name":"Gi1","up":True},{"name":"Gi2","up":False}]`; print only the down ones.
- **D10 · Wed 18 Nov · 2 h**
  - 🧪 Lab: router-on-a-stick and SVI inter-VLAN routing side by side. Verify `show ip route`, `show ip cef`, `show adjacency`, `show ip arp`, `show mac address-table`. Break: VLAN missing on the switch, SVI shut, trunk not carrying the VLAN, `ip routing` missing.
  - 🃏 +5 "what's broken?" cards from the faults.
  - 🐍 `range()` and `enumerate()`: print `1 Gi0/1 … 4 Gi0/4` from a list.
- **D11 · Thu 19 Nov · 1.5 h**
  - 🎥 Arash: *High Availability and SDM in Network Switching* + quiz. Read the SSO/NSF overview in the Cisco HA configuration guide.
  - 🃏 +8: SSO vs NSF vs NSR, what FHRP protects vs what SSO protects, SDM templates, StackWise / StackWise Virtual.
  - 🧪 Boson: 1 Simulation lab on basic switching/routing (learn the time pressure).
  - 🐍 Functions: `def is_up(intf): return intf["up"]`; call it three times; predict the outputs.
- **D12 · Fri 20 Nov · 1.5 h**
  - 🎥 Arash: *IPv4 Addressing, CIDR & NAT* — **addressing/CIDR part only** (stop when NAT starts; you'll finish it on D165).
  - 📝 20 min VLSM + summarisation drill (find the summary of 4 given /24s).
  - 🐍 `import ipaddress`; build `ipaddress.ip_network("10.1.0.0/22")`; print `.num_addresses`, `.netmask`, `.broadcast_address` — predict first.
- **D13 · Sat 21 Nov · 3.5 h**
  - 🧪 Dual-stack forwarding lab: IPv4 + IPv6 on SVIs and routed links; static routes both stacks; IPv6 static to a link-local next hop (needs the exit interface). Capture ARP and NDP.
  - 🧪 Boson: 2 Simulation labs (any already-covered basics).
  - 📝 First **Circuit P** (§8.5): 10 min, one loop + one format specifier + one JSON item from Appendix B.
  - 🃏 +6 from the lab.
- **D14 · Sun 22 Nov · 1.5 h** — **Weekly review** + **Phase 0 exit gate:** lab deploy/destroy/redeploy works and baseline score is recorded.
  - 🐍 Appendix B items 4–6.

### Phase 1 — Core campus (Layer 2)

#### Week 3 · 23–29 Nov 2026 · VLANs, 802.1Q trunks, DTP, VTP (3.1.a)
*Goal: diagnose any trunk problem from `show` output alone. Lab: **L01**.*

- **D15 · Mon 23 Nov · 1.5 h**
  - 🎥 Arash: *VLANs and Trunking Fundamentals* + quiz.
  - 🃏 +10: 802.1Q tag fields (TPID 0x8100, PCP, DEI, 12-bit VID), native VLAN untagged, allowed vs active vs pruned lists, voice VLAN, VLAN ranges.
  - 🧠 N1·T1 "802.1Q trunking and native VLAN".
  - 🐍 Slicing: `vid = "VLAN0010"`; predict `vid[4:]`, `int(vid[4:])`, `vid[-2:]`.
- **D16 · Tue 24 Nov · 1.5 h**
  - 🎥 Arash: *Advanced VLAN Configuration and Layer 2 Diagnostics* + quiz.
  - 🃏 +8: `show interfaces trunk` columns, `show interfaces switchport` admin vs operational mode, native VLAN mismatch symptoms (CDP message, VLAN leaking).
  - 🧠 N1·T3 `show interfaces trunk` output with a missing VLAN.
  - 🐍 Nested dict: `sw = {"SW1": {"vlans": [10, 20]}}`; append 30; print the list.
- **D17 · Wed 25 Nov · 2 h**
  - 🧪 **L01 build:** 3 switches, VLANs 10/20/99, static trunks, native 99, hosts in each VLAN. Verify with `show interfaces trunk`, `show vlan brief`, `show mac address-table`, tagged pcap on a trunk.
  - 🃏 +4 command/verification cards.
  - 🐍 Loop over `{"Gi0/1": [10,20], "Gi0/2": [10]}` and print trunks missing VLAN 20.
- **D18 · Thu 26 Nov · 2 h**
  - 🎥 Arash: *Dynamic Trunking Protocol (DTP) Fundamentals* + quiz.
  - 🧪 Test every DTP mode pair in L01 and build your own matrix; compare with the course.
  - 🃏 +8: DTP matrix as cloze (`dynamic auto` + `dynamic auto` = {{c1::access}}), `switchport nonegotiate`, DTP security risk.
  - 🐍 Write `dtp_result(a, b)` with a dict lookup for 3 mode pairs.
- **D19 · Fri 27 Nov · 1.5 h**
  - 🎥 Arash: *VLAN Trunking Protocol (VTP) Fundamentals* + quiz.
  - 🃏 +6: server/client/transparent/off, revision-number danger, VTPv3 primary server, pruning.
  - 🧠 N1·T6 match VTP modes → behaviours.
  - 🐍 `while` count-down from 5 with `break` at 2 — predict printed lines.
- **D20 · Sat 28 Nov · 3.5 h**
  - 🧪 **L01 break/fix** with fault library #1 and #2 (§5) plus: VLAN missing on one switch, access/trunk mismatch, `nonegotiate` on one side. Diagnose with `show` only before touching config. Time each fix.
  - 🧪 VTP mini-lab: watch a higher-revision switch overwrite the VLAN database (isolated lab only).
  - 🧪 Boson: 2 Simulation labs filtered to 3.1.a.
  - 📝 Circuit P (10 min).
- **D21 · Sun 29 Nov · 1.5 h** — **Weekly review.** 🐍 Appendix B 7–9.

#### Week 4 · 30 Nov–6 Dec 2026 · EtherChannel (3.1.b)
*Goal: "fix the EtherChannel on one device so it comes up" in ≤ 8 min. Lab: **L02**.*

- **D22 · Mon 30 Nov · 2 h**
  - 🎥 Arash: *Etherchannel Bundle or Aggregation Fundamentals*.
  - 🃏 +10: why bundle, LACP active/passive, PAgP desirable/auto, static `on`, consistency requirements (speed, duplex, mode, allowed/native VLANs).
  - 🧠 N1·T1 "EtherChannel negotiation".
  - 🐍 `zip(["Gi0/1","Gi0/2"], ["P","s"])` → print each member and flag.
- **D23 · Tue 1 Dec · 1.5 h**
  - 🎥 Arash: *EtherChannel Modes, Load Balancing, and L3 Aggregation* + **EtherChannel Quiz**.
  - 🃏 +10: compatible mode pairs, flags `P s I D U S R H`, load-balance hash choices, L3 port-channel, min-links.
  - 🧠 N1·T3 `show etherchannel summary` with a suspended member.
  - 🐍 Dict of members → count how many have flag `"P"`.
- **D24 · Wed 2 Dec · 2 h**
  - 🧪 **L02 build:** LACP L2 channel, PAgP channel, static channel, and an L3 port-channel. Verify `show etherchannel summary`, `show lacp neighbor`, `show etherchannel load-balance`, `show interfaces port-channel`. Capture LACPDUs.
  - 🃏 +4.
  - 🐍 Function `bundle_ok(local, remote)` returning True/False for LACP pairs.
- **D25 · Thu 3 Dec · 2 h**
  - 🧪 **L02 break/fix:** faults #3 and #4 plus `on` vs `active`, one member with a different allowed-VLAN list, one member access vs trunk, member shut. Fix on the **member** interfaces.
  - 🧪 Boson: 2 Simulation labs on EtherChannel.
  - 🃏 +6 fault → evidence cards.
  - 🐍 Predict: `flags = "SU"`; `print("U" in flags and "S" in flags)`.
- **D26 · Fri 4 Dec · 1 h**
  - 📝 Read the EtherChannel chapter of the Cisco Layer 2 configuration guide (add it to N2).
  - 🧠 N2·T2 EtherChannel config with one mistake.
  - 🐍 f-strings: `f"{'Po1':<6}{'SU':>4}"` — predict spacing, run.
- **D27 · Sat 5 Dec · 3.5 h**
  - 🧪 Exam-style drill: a script (or a friend/AI) breaks one side of a channel; fix in ≤ 8 min; repeat ×5 with different faults (ChatGPT §3.1.b *Prove*: 10 randomized failures over the week).
  - 🧪 Boson: 3 Simulation labs (EtherChannel + trunks).
  - 📝 Circuit P.
  - 🃏 +5.
- **D28 · Sun 6 Dec · 1.5 h** — **Weekly review.** 🐍 Appendix B 10–12.

#### Week 5 · 7–13 Dec 2026 · STP fundamentals, PVST+, root bridge (3.1.c)
*Goal: predict root bridge, root ports and blocked ports on paper. Lab: **L03** (classic/PVST+ part).*

- **D29 · Mon 7 Dec · 2 h**
  - 🎥 Arash: *Spanning Tree Protocol (STP) Fundamentals* + quiz.
  - 🃏 +12: bridge ID (priority + sys-ID-ext + MAC), root election, root/designated/blocking ports, port costs, timers 2/15/20, BPDU types.
  - 🧠 N1·T1 "802.1D election".
  - 🐍 `min()` over a list of bridge IDs as tuples `(priority, mac)` — predict the root.
- **D30 · Tue 8 Dec · 2 h**
  - 🎥 Arash: *Advanced Spanning Tree and PVST+* + quiz.
  - 🃏 +10: PVST+ per-VLAN instances, sys-ID-ext math (32768 + VLAN), priority multiples of 4096, tie-breakers (cost → sender BID → sender port ID).
  - 🧠 N1·T3 `show spanning-tree vlan 10`.
  - 🐍 `32768 + 10`, `4096 * 6` — write a function that returns a valid priority or raises `ValueError`.
- **D31 · Wed 9 Dec · 2 h**
  - 🧪 **L03 part 1:** 4 switches (triangle + one). Predict root/roles on paper first, then verify `show spanning-tree`, `show spanning-tree detail`. Capture BPDUs.
  - 🃏 +4.
  - 🐍 Sort `[("SW2",4),("SW1",19),("SW3",4)]` by cost with `sorted(..., key=lambda x: x[1])`.
- **D32 · Thu 10 Dec · 1.5 h**
  - 🎥 Arash: *STP Root Bridge and Real-World Implementation* + quiz.
  - 🃏 +8: `spanning-tree vlan X root primary/secondary` behaviour, deterministic root placement, aligning STP root with FHRP active.
  - 🧪 Boson: 1 STP Simulation lab.
  - 🐍 Dict comprehension: `{v: "SW1" for v in [10,20]}`.
- **D33 · Fri 11 Dec · 1 h**
  - 🧪 L03: root per VLAN for load sharing (VLAN 10 → SW1, VLAN 20 → SW2); verify blocked links differ per VLAN.
  - 🐍 Predict `print(*[10, 20, 30], sep=",")`.
- **D34 · Sat 12 Dec · 3.5 h**
  - 📝 Paper drills: 5 topologies with given priorities/MACs/costs → root, root ports, designated, blocked. Confirm two of them in the lab.
  - 🧪 Boson: 3 STP Simulation labs.
  - 📝 Circuit P.
  - 🃏 +6.
- **D35 · Sun 13 Dec · 1.5 h** — **Weekly review.** 🐍 Appendix B 13–15.

#### Week 6 · 14–20 Dec 2026 · STP convergence, tuning, protection
*Goal: every STP protection feature, its trigger, its state, its recovery. Lab: **L04** (guards part).*

- **D36 · Mon 14 Dec · 1.5 h**
  - 🎥 Arash: *STP Convergence and Optimization Techniques* — first half.
  - 🃏 +6: topology change process (TCN), why 30–50 s convergence, PortFast idea.
  - 🐍 Format practice: `"{:<10}{:>8}".format("Gi0/1", "FWD")`.
- **D37 · Tue 15 Dec · 1.5 h**
  - 🎥 Arash: *STP Convergence and Optimization Techniques* — second half + quiz.
  - 🃏 +6: UplinkFast/BackboneFast (legacy, recognition), how RSTP replaces them.
  - 🧠 N1·T1 "STP convergence".
  - 🐍 `"{:^9}".format("ROOT")` and `"{:*^9}".format("SW")` — predict.
- **D38 · Wed 16 Dec · 2 h**
  - 🎥 Arash: *STP Topology Tuning and Optimization* + quiz.
  - 🧪 L03: tune port cost and port priority to move the blocked port; predict before each change.
  - 🃏 +4.
  - 🐍 Loop and print a fixed-width table of 4 ports (name, role, state).
- **D39 · Thu 17 Dec · 1.5 h**
  - 🎥 Arash: *STP Protection and Loop Prevention Mechanisms* + quiz.
  - 🃏 +12: PortFast/edge, BPDU Guard (err-disabled), BPDU Filter (global vs interface), Root Guard (root-inconsistent, auto-recovers), Loop Guard (loop-inconsistent), UDLD, `errdisable recovery`.
  - 🧠 N1·T6 match feature → trigger → resulting state.
  - 🐍 Dict: `guard = {"bpduguard": "err-disabled", "rootguard": "root-inconsistent"}`; print with `.get("loopguard", "unknown")`.
- **D40 · Fri 18 Dec · 1 h**
  - 🧪 **L04 guards:** BPDU guard on an edge port → plug a "rogue" switch → err-disable → recover manually and via `errdisable recovery`; root guard on distribution downlinks → superior BPDU → root-inconsistent.
  - 🐍 Predict `bool("")`, `bool("0")`, `bool([])`, `bool([0])`.
- **D41 · Sat 19 Dec · 3.5 h**
  - 🧪 Faults #5 and #6 (§5) and loop guard on a uni-directional failure if your platform supports it. Timed.
  - 🧪 Boson: 3 STP/L2 Simulation labs.
  - 📝 Circuit P.
  - 🃏 +6.
- **D42 · Sun 20 Dec · 1.5 h** — **Weekly review.** 🐍 Re-do any missed Appendix B items.

#### Week 7 · 21–27 Dec 2026 · RSTP 🎄 (holiday-light)
*Goal: RSTP roles/states/proposal-agreement; then rest.*

- **D43 · Mon 21 Dec · 1.5 h**
  - 🎥 Arash: *Rapid Spanning Tree Protocol (RSTP) Fundamentals* + quiz.
  - 🃏 +10: RSTP roles (root, designated, alternate, backup), states (discarding, learning, forwarding), edge ports, link types (p2p vs shared), proposal/agreement, why sync is fast.
  - 🐍 List of port dicts → print alternates only.
- **D44 · Tue 22 Dec · 1.5 h**
  - 🧪 L03 converted to `rapid-pvst`: continuous ping across a failed root port — compare loss with PVST+ from W5. `debug spanning-tree events` (lab only, stop it afterwards).
  - 🃏 +4.
  - 🐍 Predict `[p for p in ["Gi1","Gi2"] if p.endswith("2")]`.
- **D45 · Wed 23 Dec · 30 min** — Anki only (+ 🐍 one drill).
- **D46 · Thu 24 Dec 🎄** — Off.
- **D47 · Fri 25 Dec 🎄** — Off.
- **D48 · Sat 26 Dec 🎄** — Off (optional: 15 min Anki).
- **D49 · Sun 27 Dec · 1 h** — Light weekly review; 🧠 N1·T5 on L2 so far (15 Q).

#### Week 8 · 28 Dec 2026–3 Jan 2027 · MST + L2 consolidation 🎄
*Goal: MST region from a written design; Phase 1 gate. Labs: **L04** (MST part), **P1** start.*

- **D50 · Mon 28 Dec · 1.5 h**
  - 🎥 Arash: *Multiple Spanning Tree Protocol (MSTP) Operation* — first half.
  - 🃏 +6: why MST, region = name + revision + VLAN-to-instance map, IST/MST0.
  - 🐍 Build `{"MST1": range(10,20), "MST2": range(20,30)}`; find the instance for VLAN 25.
- **D51 · Tue 29 Dec · 1.5 h**
  - 🎥 Arash: *MSTP Operation* — second half + quiz.
  - 🃏 +8: CIST, CST, boundary ports, interaction with PVST+, per-instance root.
  - 🧠 N1·T2 MST config with a region mismatch.
  - 🐍 Function `same_region(a, b)` comparing name/revision/map dicts.
- **D52 · Wed 30 Dec · 2 h**
  - 🧪 **L04 MST:** two instances with different roots; verify `show spanning-tree mst`, `show spanning-tree mst configuration`; mismatch name, revision, then map; find boundary ports; fix.
  - 🃏 +4.
- **D53 · Thu 31 Dec · 45 min** — L04 break/fix, one round. 🐍 one drill.
- **D54 · Fri 1 Jan 2027 🎄** — Off.
- **D55 · Sat 2 Jan · 3.5 h**
  - 🧪 L2 mini-capstone from blank in ≤ 30 min: trunks + EtherChannel + MST + guards.
  - 🧪 Boson: all L2 Simulation labs you haven't done (or repeat the slowest).
  - 📝 Start **P1 (campus resilience)** write-up: diagram, VLAN table, configs (FHRP added in W24).
- **D56 · Sun 3 Jan · 1.5 h** — **Weekly review + Phase 1 exit gate:** blind troubleshooting of 6 distinct L2 failures (have someone or a script inject them). 🐍 Appendix B mixed 5 items.

### Phase 2 — Routing core

#### Week 9 · 4–10 Jan 2027 · Static routing, IPv6 static, routing algorithms
*Goal: route selection logic (longest match → AD → metric) is automatic.*

- **D57 · Mon 4 Jan · 2 h**
  - 🎥 Arash: *Static Routing and Routing Table Fundamentals* + quiz.
  - 🃏 +10: RIB codes, longest-prefix match, AD table (Appendix A), recursive lookup, connected/local routes.
  - 🧠 N1·T1 "routing table and route selection".
  - 🐍 Strings → ints: `"10.1.1.0/24".split("/")` → prefix length as `int`.
- **D58 · Tue 5 Jan · 2 h**
  - 🎥 Arash: *Advanced Static Routing and Default Route Operation* + quiz.
  - 🃏 +10: directly attached vs recursive vs fully specified, floating static (AD), Null0 discard routes, default route, `ip default-gateway` vs `ip route 0.0.0.0`.
  - 🐍 `ipaddress.ip_address("10.1.1.5") in ipaddress.ip_network("10.1.1.0/24")` — predict.
- **D59 · Wed 6 Jan · 2 h**
  - 🧪 Static lab: overlapping prefixes to prove LPM; floating static failover; recursive route failure; Null0 summary. Verify `show ip route`, `show ip cef <prefix>`.
  - 🃏 +4.
  - 🐍 Write `longest_match(dest, prefixes)` using `ipaddress` and `max(..., key=lambda n: n.prefixlen)`.
- **D60 · Thu 7 Jan · 1.5 h**
  - 🎥 Arash: *IPv6 Static and Default Routing Fundamentals* + quiz.
  - 🧪 Dual-stack static: link-local next hop requires the exit interface; default `::/0`.
  - 🃏 +6.
  - 🐍 `ipaddress.ip_network("2001:db8::/32").prefixlen` and `.compressed`.
- **D61 · Fri 8 Jan · 1.5 h**
  - 🎥 Arash: *Dynamic Routing Protocols and Routing Algorithm* — first half.
  - 🃏 +6: distance vector vs link state vs path vector, classful vs classless, convergence.
  - 🐍 Predict `sorted([110, 90, 20, 1])` and `min(...)`.
- **D62 · Sat 9 Jan · 3.5 h**
  - 🎥 Arash: *Dynamic Routing Protocols and Routing Algorithm* — second half + quiz.
  - 🧪 Same prefix learned by static, OSPF and EIGRP — prove AD wins; then make a longer prefix win over a lower AD.
  - 🧪 Boson: 2 Simulation labs (static/default routing if available, otherwise L2 repeats).
  - 📝 Circuit P + **Circuit R** (§8.5) first run.
- **D63 · Sun 10 Jan · 1.5 h** — **Weekly review.** 🐍 Appendix B 16–17.

#### Week 10 · 11–17 Jan 2027 · EIGRP I (3.2.a)
*Goal: DUAL, FD/RD/feasible successor by hand. Lab: **B07** part 1.*

- **D64 · Mon 11 Jan · 1.5 h**
  - 🎥 Arash: *EIGRP Fundamentals and Core Concepts* + quiz.
  - 🃏 +10: advanced distance vector, protocol 88, 224.0.0.10, RTP, packet types (hello/update/query/reply/ack), AD 90/170.
  - 🧠 N1·T1 "EIGRP fundamentals".
  - 🐍 Dict of neighbors → print `f"{ip:<15}{intf:<8}{uptime}"`.
- **D65 · Tue 12 Jan · 1.5 h**
  - 🎥 Arash: *EIGRP Operations and Neighbor Relationship* + quiz.
  - 🃏 +8: neighbor requirements (AS, K-values, subnet, auth), hello/hold 5/15, passive interface effect.
  - 🐍 `try/except KeyError` when reading `nbr["holdtime"]` from an incomplete dict.
- **D66 · Wed 13 Jan · 2 h**
  - 🧪 **B07 part 1:** 4-router EIGRP (named mode on three, classic on one). Break: K-value mismatch, AS mismatch, passive interface, authentication mismatch.
  - 🃏 +5.
  - 🐍 Function that returns the list of neighbors with `holdtime < 5`.
- **D67 · Thu 14 Jan · 2 h**
  - 🎥 Arash: *EIGRP Metrics and Path Calculation* + quiz.
  - 🃏 +8: classic metric (bandwidth + delay with default K-values), wide metrics, why bandwidth is the minimum and delay is the sum.
  - 🐍 Implement the classic metric formula for K1=K3=1: `256 * (10**7 // min_bw_kbps + sum_delay_usec // 10)` — compute for one path and check against `show ip eigrp topology`.
- **D68 · Fri 15 Jan · 1 h**
  - 📝 Hand-calculate metrics for 3 paths in B07; verify in the lab.
  - 🐍 Same function over 3 paths; print the lowest with `min()`.
- **D69 · Sat 16 Jan · 3.5 h**
  - 🎥 Arash: *EIGRP Route Selection and Convergence Process* + quiz.
  - 🧪 B07: find successor and feasible successor from `show ip eigrp topology all-links`; fail the successor with and without an FS; watch queries; configure a stub and see queries stop.
  - 🃏 +8: FD, RD, feasibility condition (RD < FD), active vs passive, SIA.
  - 📝 Circuit R.
- **D70 · Sun 17 Jan · 1.5 h** — **Weekly review.** 🐍 Appendix B 18.

#### Week 11 · 18–24 Jan 2027 · EIGRP II + OSPF I
*Goal: finish EIGRP, write the EIGRP-vs-OSPF comparison, start OSPF.*

- **D71 · Mon 18 Jan · 1.5 h**
  - 🎥 Arash: *EIGRP Equal and Unequal Cost Paths Load Balancing* + quiz.
  - 🧪 B07: `variance` — prove only feasible successors are used.
  - 🃏 +5.
  - 🐍 Predict `[m for m in [100, 150, 300] if m <= 100 * 2]`.
- **D72 · Tue 19 Jan · 1.5 h**
  - 🎥 Arash: *EIGRP Route Summarization and Optimization* + quiz.
  - 🧪 Quick interface summary + stub lab.
  - 🃏 +6.
  - 🐍 `ipaddress.collapse_addresses()` on four /24s — predict the result, then run.
- **D73 · Wed 20 Jan · 2 h**
  - 🧪 **B07 part 2:** same topology, now OSPF single area; fail the same link; compare convergence and metrics with EIGRP.
  - 📝 Write the **3.2.a comparison sheet** (§4: protocol type, updates, path calculation, adjacency, areas, metrics, load balancing, symptoms).
  - 🃏 +8 from the comparison sheet.
- **D74 · Thu 21 Jan · 1.5 h**
  - 🎥 Arash: *OSPF Routing Fundamentals and Area Concepts* + quiz.
  - 🃏 +8: link state, LSDB, SPF, areas, ABR/ASBR, backbone rule, protocol 89, 224.0.0.5/.6.
  - 🧠 N1·T1 "OSPF areas".
  - 🐍 Nested dict `{"area0": ["R1","R2"], "area1": ["R2","R3"]}` → find the ABR (in 2 areas).
- **D75 · Fri 22 Jan · 1.5 h**
  - 🎥 Arash: *OSPF Configuration Methods and Router ID Fundamentals* + quiz.
  - 🃏 +6: `network` wildcard vs interface `ip ospf 1 area 0`, RID selection order, `clear ip ospf process`.
  - 🐍 Function `wildcard(mask)` → `"0.0.0.255"` from `"255.255.255.0"`.
- **D76 · Sat 23 Jan · 3.5 h**
  - 🎥 Arash: *OSPF Neighbor Adjacency and Authentication* + quiz.
  - 🧪 Single-area OSPF on 4 routers with both config methods; MD5 and SHA (key-chain) authentication; break auth.
  - 🧪 Boson: 2 OSPF Simulation labs.
  - 📝 Circuit P.
  - 🃏 +8: full adjacency requirements list.
- **D77 · Sun 24 Jan · 1.5 h** — **Weekly review.** 🐍 Appendix B 19.

#### Week 12 · 25–31 Jan 2027 · OSPF II: states, DR/BDR, LSAs, route types, cost
*Lab: **L05**.*

- **D78 · Mon 25 Jan · 2 h**
  - 🎥 Arash: *OSPF Neighbor States and Database Exchange Process* + *OSPF DR and BDR Election Process* + quizzes.
  - 🃏 +10: Down→Init→2-Way→ExStart→Exchange→Loading→Full, DBD/LSR/LSU/LSAck, DROTHERs stay 2-Way, DR election (priority, RID, non-preemptive).
  - 🐍 List of states → index of `"EXSTART"`; predict `states.index("FULL")`.
- **D79 · Tue 26 Jan · 2 h**
  - 🧪 **L05 part 1:** broadcast segment (via an L2 switch) with DR/BDR control by priority + p2p links; capture hellos/DBDs. Faults #8 and #9 (network-type mismatch, MTU → EXSTART).
  - 🃏 +5.
- **D80 · Wed 27 Jan · 1.5 h**
  - 🎥 Arash: *OSPF LSA Type-1* + *LSA Type-2* + quizzes.
  - 🧪 `show ip ospf database router` / `network` — draw the topology from the LSDB.
  - 🃏 +6.
  - 🐍 Parse a fake LSDB list of dicts; count LSAs by type with a dict counter.
- **D81 · Thu 28 Jan · 1.5 h**
  - 🎥 Arash: *OSPF LSA Type-3 and Inter-Area Route Summarization* + *OSPF Route Types and Path Selection Rules* + *OSPF Default Route Advertisement and Control* + quizzes.
  - 🃏 +10: O vs O IA vs E1/E2 vs N1/N2 preference, `default-information originate [always]`, LSA 3/4/5/7 roles.
  - 🧠 N1·T3 `show ip route ospf` with mixed route types.
- **D82 · Fri 29 Jan · 1 h**
  - 🎥 Arash: *OSPF Cost and Path Selection Rules* + quiz.
  - 🃏 +5: cost = ref-bw / bw, `auto-cost reference-bandwidth` must match everywhere, `ip ospf cost`.
  - 🐍 Function `ospf_cost(bw_mbps, ref=100)` with `max(1, ...)` — predict for 10, 100, 1000 Mbps.
- **D83 · Sat 30 Jan · 3.5 h**
  - 🧪 **L05 full build:** backbone + two normal areas, two loopbacks per remote area, default route origination, cost manipulation to steer a path; verify reachability both directions.
  - 🧪 Boson: 2 OSPF Simulation labs.
  - 📝 Circuit R.
- **D84 · Sun 31 Jan · 1.5 h** — **Weekly review.** 🐍 Appendix B 20.

#### Week 13 · 1–7 Feb 2027 · OSPF III: summarisation, network types, filtering, OSPFv3
*Labs: **L06**, **L07**. Exam-style: "multi-area OSPF + summarisation".*

- **D85 · Mon 1 Feb · 1.5 h**
  - 🎥 Arash: *OSPF Inter-Area Route Summarization* + *OSPF Network Types and Operations* + quizzes.
  - 🃏 +10: `area X range` on the ABR, `summary-address` on the ASBR, discard route, network types + timers + DR behaviour (Appendix A).
  - 🐍 `ipaddress.ip_network("10.1.0.0/22").subnets(new_prefix=24)` → list them.
- **D86 · Tue 2 Feb · 2 h**
  - 🧪 **L06:** summarise area 1 and area 2 at their ABRs; verify exact route visibility; fault #10 (summary covering an unreachable prefix).
  - 🃏 +4.
- **D87 · Wed 3 Feb · 1.5 h**
  - 🎥 Arash: *OSPF Route Filtering Techniques* + quiz.
  - 🧪 L06 filtering: `area X filter-list prefix`, `area X range … not-advertise`, `distribute-list in` (RIB only, LSDB unchanged — prove it).
  - 🃏 +6.
- **D88 · Thu 4 Feb · 1.5 h**
  - 🎥 Arash: *OSPFv3 Operation and Implementation* + quiz.
  - 🃏 +6: per-interface config, link-local next hops, RID needed on IPv6-only, multiple instances per link.
  - 🐍 Predict `"FE80::1".lower().startswith("fe80")`.
- **D89 · Fri 5 Feb · 1.5 h**
  - 🎥 Arash: *OSPFv3 LSA Types and Flooding Scope* + quiz.
  - 🃏 +6: Link LSA (8), Intra-Area-Prefix LSA (9), flooding scopes.
- **D90 · Sat 6 Feb · 3.5 h**
  - 🎥 Arash: *OSPFv3 Address Family Operation* + quiz.
  - 🧪 **L07:** OSPFv3 multi-area (IPv6 AF, then IPv4 AF).
  - 🧪 **Timed exam-sim:** L05+L06 from blank (multi-area + summarisation) ≤ 15 min, twice.
  - 🧪 Boson: 2 OSPF Simulation labs.
- **D91 · Sun 7 Feb · 1.5 h** — **Weekly review.** 🧠 N3·T8 teach-back "why is OSPF stuck in EXSTART?".

#### Week 14 · 8–14 Feb 2027 · ACLs (basics), prefix lists, route-maps, PBR
*Lab: **B08**.*

- **D92 · Mon 8 Feb · 1.5 h**
  - 🎥 Arash: *Access Control Lists (ACLs) Types and Applications* + quiz.
  - 📝 20 wildcard-mask drills.
  - 🃏 +6: standard/extended/named, first-match, implicit deny, placement.
  - 🐍 Function that converts a prefix length to a wildcard (`/27` → `0.0.0.31`).
- **D93 · Tue 9 Feb · 1.5 h**
  - 🎥 Arash: *IP and IPv6 Prefix Lists Fundamentals* + quiz.
  - 📝 20 `ge`/`le` drills (which prefixes match `10.0.0.0/8 ge 24 le 28`?).
  - 🃏 +8.
  - 🐍 Implement a tiny prefix-list matcher with `ipaddress` (`subnet_of` + prefixlen checks).
- **D94 · Wed 10 Feb · 1.5 h**
  - 🎥 Arash: *Route-Map Fundamentals and Match Logic* + quiz.
  - 🃏 +8: permit/deny sequences, multiple `match` = AND, multiple values on one line = OR, implicit deny, `continue`.
  - 🧠 N1·T2 route-map with one logic mistake.
- **D95 · Thu 11 Feb · 1.5 h**
  - 🎥 Arash: *PBR with ACL Implementation* + *PBR with Packet Length Implementation* + quizzes.
  - 🃏 +6: inbound application, `set ip next-hop` vs `default next-hop`, `verify-availability`, `ip local policy`.
- **D96 · Fri 12 Feb · 1.5 h**
  - 🧪 **B08 build:** two ISP paths; source subnet A → ISP2, everything else follows the RIB; packet-length PBR example.
  - 🐍 Predict a loop that matches packets of different lengths against `range(0, 129)`.
- **D97 · Sat 13 Feb · 3.5 h**
  - 🧪 B08 break/fix: policy on the wrong interface, ACL mismatch, next hop down without `verify-availability`.
  - 📝 Interpret 10 route-map + ACL + RIB combinations on paper (3.2.d *Prove*).
  - 🧪 Boson: 2 Simulation labs (repeat weakest so far).
  - 📝 Circuit P.
- **D98 · Sun 14 Feb · 1.5 h** — **Weekly review.**

#### Week 15 · 15–21 Feb 2027 · BGP I: sessions and advertisements (3.2.c)
*Lab: **L08**. Exam-style: "eBGP with many loopbacks".*

- **D99 · Mon 15 Feb · 2 h**
  - 🎥 Arash: *BGP Fundamentals and Path Vector Operation* + quiz.
  - 🃏 +10: path vector, ASNs (2/4-byte, private), TCP 179, eBGP vs iBGP (TTL, AD 20/200, next hop), loop prevention via AS_PATH.
  - 🧠 N1·T1 "BGP fundamentals".
- **D100 · Tue 16 Feb · 2 h**
  - 🎥 Arash: *BGP Timers, Neighbor Relationships, and State Machine* + quiz.
  - 🃏 +8: Idle/Connect/Active/OpenSent/OpenConfirm/Established and what each stuck state means; keepalive/hold 60/180.
  - 🐍 Dict `{"10.0.12.2": "Established", "10.0.13.3": "Active"}` → print the down peers.
- **D101 · Wed 17 Feb · 2 h**
  - 🧪 **L08 part 1:** 3–4 ASes directly connected; sessions up; fault #11 (wrong AS).
  - 🃏 +4.
- **D102 · Thu 18 Feb · 1.5 h**
  - 🎥 Arash: *Injecting Routes into the BGP Table* + quiz.
  - 🧪 L08: advertise 10–20 prefixes (loopbacks of mixed lengths); fault #12 (no exact RIB match).
  - 🃏 +5.
- **D103 · Fri 19 Feb · 1.5 h**
  - 🎥 Arash: *BGP Route Summarization and Aggregation* + quiz.
  - 🃏 +5: `aggregate-address` `summary-only` / `as-set`, `s` suppressed code.
  - 🐍 Write a script that generates a random addressing table of 15 prefixes for tomorrow's drill.
- **D104 · Sat 20 Feb · 3.5 h**
  - 🎥 Arash: *Multiprotocol BGP (MP-BGP) for IPv6 Routing* + quiz.
  - 🧪 L08 IPv6 address family.
  - 🧪 **Timed exam-sim:** eBGP + 15–20 networks from your generated table ≤ 10 min, twice (subnetting accuracy!).
  - 🧪 Boson: 2 BGP Simulation labs.
- **D105 · Sun 21 Feb · 1.5 h** — **Weekly review.** 🐍 Appendix B 21.

#### Week 16 · 22–28 Feb 2027 · BGP II: policy, communities, best path (part 1)

- **D106 · Mon 22 Feb · 1.5 h**
  - 🎥 Arash: *BGP Route Filtering and Policy Control* — first half.
  - 🃏 +5.
- **D107 · Tue 23 Feb · 1.5 h**
  - 🎥 Arash: *BGP Route Filtering and Policy Control* — second half + quiz.
  - 🃏 +6: prefix-list/route-map/filter-list in/out, AS-path regex basics (`^$`, `_65001_`).
  - 🐍 `re.search(r"_65001_", " 65002 65001 ")` style drills with Python `re` (note: Cisco `_` ≠ Python; use `(^|\s)65001(\s|$)`).
- **D108 · Wed 24 Feb · 2 h**
  - 🎥 Arash: *BGP Session Clearing and Soft Reset Mechanisms* + quiz.
  - 🧪 L08: filter in/out with prefix-lists and route-maps; `clear ip bgp * soft in/out`; verify `advertised-routes` / `received-routes`.
  - 🃏 +5.
- **D109 · Thu 25 Feb · 1.5 h**
  - 🎥 Arash: *BGP Communities and Route Control* + quiz.
  - 🃏 +6: well-known communities (no-export, no-advertise, local-AS), `send-community`.
- **D110 · Fri 26 Feb · 1.5 h**
  - 🎥 Arash: *BGP Path Selection with Longest Prefix Match* + *BGP Best Path Selection and Weight Attribute* + quizzes.
  - 🃏 +5.
- **D111 · Sat 27 Feb · 3.5 h**
  - 🎥 Arash: *BGP Best Path Selection and Local Preference Attribute* + *BGP Path Preference for Locally Injected Routes* + quizzes.
  - 🧪 Dual-homed lab: change weight, then local preference; record which path gets `>` each time; tag a community and match it.
  - 🧪 Boson: 2 BGP Simulation labs.
  - 📝 Circuit R.
- **D112 · Sun 28 Feb · 1.5 h** — **Weekly review.**

#### Week 17 · 1–7 Mar 2027 · BGP III: best path (part 2) + **Checkpoint 1**
*Projects: **P2** write-up. Integrated: **C01**.*

- **D113 · Mon 1 Mar · 1.5 h**
  - 🎥 Arash: *BGP Best Path Selection with AIGP Metric* + *AS-Path Attribute* + quizzes.
  - 🃏 +5.
- **D114 · Tue 2 Mar · 1.5 h**
  - 🎥 Arash: *Origin Code Attribute* + *MED Attribute* + *eBGP over iBGP Preference* + quizzes.
  - 🃏 +6.
- **D115 · Wed 3 Mar · 1.5 h**
  - 🎥 Arash: *IGP Metric* + *Oldest eBGP Path* + *Router ID* + *Neighbor IP Address* + *Path Attribute Types and Categories* + quizzes.
  - 🃏 +8: the full best-path order (Appendix A mnemonic) as one ordered cloze; attribute categories.
  - 🧠 N1·T6 order the best-path steps.
- **D116 · Thu 4 Mar · 1.5 h**
  - 🎥 Arash: *BGP Autonomous System (AS) Numbers and Removal* + *BGP Multihoming and Failover Routing* + quizzes.
  - 🧪 Multihoming failover; AS-path prepend; `remove-private-as`.
  - 🃏 +4.
- **D117 · Fri 5 Mar · 1 h**
  - 🧪 One-attribute-at-a-time experiment table: change one attribute, record winner, explain.
  - 📝 Start **P2 (multi-area enterprise routing)** write-up.
- **D118 · Sat 6 Mar · 4 h — Checkpoint 1**
  - 📝 Pearson OCG practice exam filtered to the L2 + routing chapters, timed (45 Q).
  - 🧪 **C01** (branch routing and switching restoration) from a hidden broken state, read-only commands first.
  - 🧪 Boson: all routing Simulation labs once more, timed.
- **D119 · Sun 7 Mar · 1.5 h** — **Weekly review + Phase 2 exit gate:** multi-area OSPF and eBGP built from blank (NAT gate later, D167). Log Checkpoint 1 misses (§8.3).

### Phase 3 — Virtualization: VRF, GRE, IPsec

#### Week 18 · 8–14 Mar 2027 · VRF-lite and GRE (2.2)
*Labs: **L11**, **L12**, **L13**. Exam-style: "VRF + tunnel + static routes so X and Y use the tunnel".*

- **D120 · Mon 8 Mar · 2 h**
  - 🎥 Arash: *Virtual Routing and Forwarding (VRF) Lite Fundamentals* + quiz.
  - 🃏 +10: VRF = separate RIB/FIB, `vrf definition` + address families, `vrf forwarding` **removes the interface IP**, VRF static routes, `ping vrf`, RD/RT only matter with MP-BGP/MPLS.
  - 🧠 N1·T1 "VRF-lite".
  - 🐍 Two dicts with the same prefix key in different "VRFs" → show why they don't collide (`vrfs["RED"]["10.1.1.0/24"]`).
- **D121 · Tue 9 Mar · 2 h**
  - 🧪 **L11:** RED and BLUE with identical subnets on shared routers; per-VRF static routes; prove isolation; fault #13 (VRF route in the global table).
  - 🃏 +4.
- **D122 · Wed 10 Mar · 1.5 h**
  - 🎥 Arash: *Generic Routing Encapsulation (GRE) Fundamentals* + quiz.
  - 🃏 +8: protocol 47, 24-byte overhead, no encryption, tunnel up/down rules, keepalives, `ip mtu 1400` / `ip tcp adjust-mss 1360`, recursive routing.
- **D123 · Thu 11 Mar · 2 h**
  - 🧪 **L12:** GRE over a global underlay; OSPF or static across it; capture outer/inner headers; fault #14 (no underlay route) and recursive routing (advertise the tunnel destination through the tunnel).
  - 🃏 +5.
  - 🐍 Compute payload MTU: `1500 - 20 - 4 - 20` and print with labels using `format()`.
- **D124 · Fri 12 Mar · 1 h**
  - 📝 Read the Cisco GRE source/destination VRF membership guide (§10; add to N2). Draw all four combinations: global/global, VRF over global, global over VRF, VRF over VRF. Label inner vs outer RIB.
  - 🃏 +6: `vrf forwarding` on the tunnel = **inner** VRF; `tunnel vrf` = **outer/transport** VRF.
  - 🧠 N2·T1 "VRF-aware GRE".
- **D125 · Sat 13 Mar · 3.5 h**
  - 🧪 **L13:** GRE tunnel interface in a customer VRF over the global underlay; static routes so only subnets X and Y cross the tunnel; test both directions.
  - 🧪 **Timed exam-sim:** L13 from blank ≤ 12 min.
  - 🧪 Boson: VRF/tunnel Simulation labs.
  - 📝 Circuit P.
- **D126 · Sun 14 Mar · 1.5 h** — **Weekly review.** 🐍 Appendix B 22.

#### Week 19 · 15–21 Mar 2027 · IPsec, front-door VRF, overlay restoration
*Labs: **L14**, **L15**, **C02**. Project: **P3**.*

- **D127 · Mon 15 Mar · 1.5 h**
  - 🎥 Arash: *IPsec & IKE Fundamentals* + *IPsec AH & ESP Protocols* + *IPsec & IKE Deep Dive* + quizzes.
  - 🃏 +10: ESP 50 vs AH 51, tunnel vs transport mode, IKEv1 main/aggressive/quick mode vs IKEv2, SAs, NAT-T UDP 4500, ISAKMP UDP 500.
- **D128 · Tue 16 Mar · 1.5 h**
  - 🎥 Arash: *Site-to-Site IPsec GRE Tunneling* + *IPsec VTI and IKE Fundamentals* + quizzes.
  - 🃏 +6: crypto map (policy-based) vs VTI (route-based), GRE over IPsec, `tunnel protection ipsec profile`.
  - 🧠 N1·T2 IKEv2 config with a proposal mismatch.
- **D129 · Wed 17 Mar · 2 h**
  - 🧪 **L14:** front-door transport VRF (`tunnel vrf`) + separate overlay VRF; fault #15 (wrong `tunnel vrf`).
  - 🃏 +4.
- **D130 · Thu 18 Mar · 2 h**
  - 🧪 **L15:** IPsec VTI (or GRE protected by IPsec); verify `show crypto ikev2 sa`, `show crypto ipsec sa` encaps/decaps; encrypted pcap. Break: PSK, proposal, peer address.
  - 🃏 +4.
- **D131 · Fri 19 Mar · 1 h**
  - 📝 Start the 2.3 comparison matrix (VRF, VLAN, GRE, IPsec now; VXLAN, LISP in W27): function, layer, encapsulation, security, control plane, use case.
  - 🧠 N2·T6 match tunnel/VRF commands → inner/outer.
- **D132 · Sat 20 Mar · 4 h**
  - 🧪 **C02** (dual customer VRF overlay restoration): single faults first, then a hidden combination. Record all four path perspectives.
  - 📝 **Phase 3 gate:** explain both tunnel VRFs out loud; prove 3 tunnel variants.
  - 📝 **P3 (multi-tenant WAN overlay)** write-up with the inner-vs-outer packet anatomy diagram.
- **D133 · Sun 21 Mar · 1.5 h** — **Weekly review.**

### Phase 6 (moved earlier) — Programmability

#### Week 20 · 22–28 Mar 2027 · APIs, REST, JSON, Postman, Catalyst Center API 🐣
*Labs: **B12**, **B15**. The passer's automation list (§11.2) starts here.*

- **D134 · Mon 22 Mar · 2 h**
  - 🎥 Arash: *APIs and Network Programmability* + quiz.
  - 🃏 +10: northbound vs southbound APIs, controller-based networking, REST constraints, API vs CLI (structured data, idempotency, auth).
  - 🧠 N4·T1 "network APIs".
  - 🐍 `import json`; `json.dumps({"hostname": "R1", "enabled": True})` — predict the string (note `true`).
- **D135 · Tue 23 Mar · 2 h**
  - 🎥 Arash: *RESTful APIs and Data Serialization* + quiz.
  - 🃏 +10: JSON vs XML vs YAML syntax, JSON types, invalid JSON (single quotes, trailing commas, `True`, comments), Python ↔ JSON type mapping.
  - 🐍 **6.2 drill:** repair 5 broken JSON documents; validate each with `json.loads()`.
- **D136 · Wed 24 Mar · 2 h**
  - 🧪 Postman: Catalyst Center always-on sandbox. Request 1: **`POST /dna/system/api/v1/auth/token` with Basic Auth** → `Token`. Request 2: `GET /dna/intent/api/v1/network-device` with header `X-Auth-Token`. Save as a collection with variables (base URL, token); no secrets in Git.
  - 🃏 +6: each step, method, auth type, header name.
- **D137 · Thu 25 Mar 🐣 · 1.5 h**
  - 🎥 Arash: *REST API Response Codes and Payload Interpretation* + *REST API Security Fundamentals* + quizzes.
  - 🧪 **B12 start:** break the request 5 ways — no token (401), wrong method (405), bad URI (404), wrong `Content-Type` on a POST (415), malformed JSON body (400). Screenshot each.
  - 🃏 +8: 200/201/202/204/400/401/403/404/405/409/415/429/500/503 meanings; 401 vs 403.
- **D138 · Fri 26 Mar 🐣 · 1.5 h**
  - 🐍 Python version of D136: `requests.post(..., auth=HTTPBasicAuth(u, p))` → token → `requests.get(..., headers={"X-Auth-Token": token})` → loop over `response.json()["response"]` and print a `.format()` table. Handle non-200 with `if r.status_code != 200`.
  - 🃏 +4.
- **D139 · Sat 27 Mar 🐣 · 3.5 h**
  - 🧪 **B12 full:** 15 deliberate API mistakes (§4 6.5 *Do*): POST instead of GET, stale token, missing `Accept`, TLS verification error, etc. For each: hypothesis → layer → smallest fix → retry → sanitized transcript.
  - 🧪 **B15:** inventory parse/format/backup script with `json.dump`/`json.load`, `try/except`, and two `pytest` tests.
  - 📝 Circuit A (§8.5).
- **D140 · Sun 28 Mar 🐣 · 1 h** — Light weekly review. 🧠 N4·T4 ×5 (dump/dumps/load/loads blanks).

#### Week 21 · 29 Mar–4 Apr 2027 · YANG, NETCONF, RESTCONF, EEM, orchestration tools
*Labs: **L21**, **L22**, **L27**, **B16**, **B17**.*

- **D141 · Mon 29 Mar 🐣 · 1 h**
  - 📝 YANG basics: module, container, list (key), leaf, leaf-list, typedef, `config true/false`; read the YANG section of RFC 7950's introduction and the IOS XE programmability guide overview (add to N4).
  - 🧪 `pyang -f tree` on `ietf-interfaces.yang`.
  - 🃏 +8.
- **D142 · Tue 30 Mar · 1.5 h**
  - 🎥 Arash: *NETCONF and RESTCONF Configuration and Verification* + quiz.
  - 🧪 Enable `netconf-yang`, `restconf`, `ip http secure-server` on a Catalyst 8000V (or the IOS XE sandbox).
  - 🃏 +8: NETCONF SSH/830/XML, operations, datastores; RESTCONF HTTPS, `/restconf/data/...`, `application/yang-data+json`, verb mapping.
- **D143 · Wed 31 Mar · 2 h**
  - 🧪 **L21:** `ncclient` `get-config` with a subtree filter, `edit-config` to add a loopback, read back; break with a wrong namespace and invalid XML.
  - 🧪 **B16:** YANG path → NETCONF XML → RESTCONF URI + JSON body for the same change.
  - 🐍 `xml.etree.ElementTree` — find all `<name>` elements in an interfaces reply.
- **D144 · Thu 1 Apr · 2 h**
  - 🧪 **L22:** RESTCONF GET/PUT/PATCH/DELETE in Postman and Python; fault #22 (valid auth, invalid YANG path); collect 400/401/404/405/409/415 on purpose.
  - 🃏 +6.
- **D145 · Fri 2 Apr · 1.5 h**
  - 🎥 Arash: *Network Automation and Embedded Event Manager (EEM)* + quiz.
  - 🃏 +8: applet structure (`event` + ordered `action`), event detectors (syslog, timer, cli, track, interface, none), `$_cli_result`, action labels sort as **strings**.
- **D146 · Sat 3 Apr · 4 h**
  - 🧪 **L27:** 4 applets from blank — syslog-triggered evidence capture, cron data collection, `event none` + `event manager run`, `event cli pattern` with `sync`; fault #25 (loop with no guard) in an isolated lab.
  - 🎥 Arash: *Configuration Management and Automation Tools* + quiz.
  - 🧪 **B17:** Ansible playbook (`ios_command` + an NTP change via `ios_config`); run twice to see `changed` vs `ok`.
  - 🃏 +10: Ansible/Puppet/Chef/SaltStack table (§4 6.7): agentless vs agent, push vs pull, language, artifacts (playbooks/manifests/cookbooks+recipes/states), master/minion, multi-master.
  - 🧠 N4·T6 tool → attribute drag-and-drop.
- **D147 · Sun 4 Apr · 1.5 h** — **Weekly review + early Phase 6 gate:** own script + API + EEM lab incl. failure cases (re-gated D236).

### Phase 2b — IP services

#### Week 22 · 5–11 Apr 2027 · Multicast I (3.3.d)
*Lab: **B10** part 1–2.*

- **D148 · Mon 5 Apr · 2 h**
  - 🎥 Arash: *IP Multicast Essentials* + quiz.
  - 🃏 +10: 224/4, 232/8 SSM, 239/8 scoped, L2 mapping `01:00:5e` + 23 bits (32:1), source/receiver/tree concepts.
  - 🐍 Convert a multicast IP to its MAC in Python (mask the low 23 bits) — check two examples by hand.
- **D149 · Tue 6 Apr · 2 h**
  - 🎥 Arash: *IGMP and IGMP Snooping Fundamentals* + quiz.
  - 🃏 +10: IGMPv2 report/leave/group-specific query, IGMPv3 INCLUDE/EXCLUDE source lists, querier, snooping.
- **D150 · Wed 7 Apr · 2 h**
  - 🧪 **B10 part 1:** receivers join (Linux or `ip igmp join-group`); IGMP snooping on the L2 switch; capture v2 vs v3 reports.
  - 🃏 +4.
- **D151 · Thu 8 Apr · 1.5 h**
  - 🎥 Arash: *PIM Dense Mode Fundamentals* + quiz.
  - 🧪 Quick PIM-DM flood-and-prune observation (contrast only).
  - 🃏 +5.
- **D152 · Fri 9 Apr · 1.5 h**
  - 🎥 Arash: *PIM Sparse Mode Fundamentals* + quiz.
  - 🃏 +8: RP, register/register-stop, (*,G) shared tree, (S,G) source tree, SPT switchover, RPF check uses the unicast RIB.
- **D153 · Sat 10 Apr · 3.5 h**
  - 🧪 **B10 part 2:** PIM-SM with static RP; read `show ip mroute`, `show ip pim neighbor`, `show ip rpf`; break RPF with a static route out the wrong interface; prove unicast still works.
  - 📝 Pearson: multicast chapter questions.
  - 📝 Circuit A.
- **D154 · Sun 11 Apr · 1.5 h** — **Weekly review.**

#### Week 23 · 12–18 Apr 2027 · Multicast II + NTP/PTP (3.3.d, 3.3.a)
*Lab: **B09**.*

- **D155 · Mon 12 Apr · 2 h**
  - 🎥 Arash: *PIM Designated Router (DR) and PIM Forwarder* + *PIM Rendezvous Point (RP) Mechanisms Static RP, Auto-RP & BSR* + quizzes.
  - 🃏 +8.
- **D156 · Tue 13 Apr · 1.5 h**
  - 🎥 Arash: *Advanced Multicast Concepts - SSM, Bidir-PIM, and MSDP* + quiz.
  - 🧪 SSM with IGMPv3 (`ip pim ssm default`); optional BSR.
  - 🃏 +6.
- **D157 · Wed 14 Apr · 1.5 h**
  - 📝 Multicast comparison chart (ASM vs SSM vs Bidir vs MSDP: purpose, tree, RP?, boundary).
  - 🧠 N1·T3 three mroute entries to interpret.
  - 🃏 +4.
- **D158 · Thu 15 Apr · 2 h**
  - 🎥 Arash: *Cisco Device Time Management & NTP Fundamentals* + quiz.
  - 🃏 +8: stratum, server/peer/client/master, authentication (`authenticate`, `authentication-key`, `trusted-key`), `show ntp associations` symbols, UDP 123.
- **D159 · Fri 16 Apr · 1 h**
  - 🎥 Arash: *Precision Time Protocol (PTP) Fundamentals* + quiz.
  - 🃏 +6: grandmaster, ordinary/boundary/transparent clocks, BMCA, hardware timestamping, why sub-microsecond.
- **D160 · Sat 17 Apr · 3.5 h**
  - 🧪 **B09:** chrony server + two routers; authenticated NTP; block UDP 123 and diagnose; annotate one sample PTP config (3.3.a is *interpret*).
  - 🧪 Boson: 2 Simulation labs (repeat weakest).
  - 📝 Circuit P.
- **D161 · Sun 18 Apr · 1.5 h** — **Weekly review.**

#### Week 24 · 19–25 Apr 2027 · FHRP + NAT/PAT (3.3.c, 3.3.b, 1.1.b)
*Labs: **L10**, **L09**. Project: **P1** completed.*

- **D162 · Mon 19 Apr · 1.5 h**
  - 🎥 Arash: *Hot Standby Router Protocol (HSRP) Fundamentals* + quiz.
  - 🃏 +8: v1 vs v2, vMAC formats, priority 100, preempt **off** by default, hello/hold 3/10, tracking decrement.
- **D163 · Tue 20 Apr · 1.5 h**
  - 🎥 Arash: *VRRP Fundamentals* + *GLBP Fundamentals* + quizzes.
  - 🃏 +8: VRRP master/backup, preempt **on**, can use the real interface IP, protocol 112; GLBP AVG/AVF (contrast).
- **D164 · Wed 21 Apr · 2 h**
  - 🧪 **L10:** HSRP then VRRP; tracking an uplink; continuous ping during failover and recovery; align with STP root from W5.
  - 🃏 +4.
- **D165 · Thu 22 Apr · 1.5 h**
  - 🎥 Arash: *IPv4 Addressing, CIDR & NAT* — **NAT part** + quiz.
  - 🃏 +8: inside/outside local/global, static, dynamic pool, PAT overload, `ip nat inside/outside`, translation table.
- **D166 · Fri 23 Apr · 1.5 h**
  - 🧪 **L09 build:** PAT for inside hosts, one static publication, `show ip nat translations/statistics`, captures both sides.
- **D167 · Sat 24 Apr · 3.5 h**
  - 🧪 L09 + L10 break/fix (interface direction, ACL wildcard, pool mask, no preempt, decrement too small).
  - 🧪 Boson: NAT/FHRP Simulation labs.
  - 📝 Finish **P1** with FHRP; **Phase 2 NAT gate:** NAT built from blank.
- **D168 · Sun 25 Apr · 1.5 h** — **Weekly review.**

### Phase 5a — QoS interpretation (1.4)

#### Week 25 · 26 Apr–2 May 2027 · QoS I: fundamentals, models, classification, marking

- **D169 · Mon 26 Apr · 1.5 h**
  - 🎥 Arash: *QoS Fundamentals Delay, Jitter & Packet Loss* + quiz.
  - 🃏 +6: delay types, jitter, loss, voice/video tolerances.
- **D170 · Tue 27 Apr · 1 h**
  - 🎥 Arash: *QoS Models Best Effort, IntServ & DiffServ* + quiz.
  - 🃏 +5.
- **D171 · Wed 28 Apr · 2 h**
  - 🎥 Arash: *QoS Classification & L3 Marking* + quiz.
  - 🃏 +10: ToS byte, IPP 3 bits, DSCP 6 bits, EF 46, AFxy = 8x + 2y, CSx = 8x, drop precedence.
  - 🐍 Function `af(x, y)` returning `8*x + 2*y`; print a table of AF11–AF43 with `format()`.
- **D172 · Thu 29 Apr · 1.5 h**
  - 🎥 Arash: *QoS Classification & L2 Marking* + quiz.
  - 🃏 +6: CoS/PCP in 802.1Q, DEI, trust boundary.
- **D173 · Fri 30 Apr · 1 h**
  - 🎥 Arash: *QoS Classification & Marking Across All Layers* + quiz.
  - 🃏 +5: CoS ↔ DSCP mapping, NBAR classification.
- **D174 · Sat 1 May · 3.5 h**
  - 🧪 Trust-boundary and marking lab (simple MQC `set dscp` preview); capture markings in Wireshark.
  - 📝 50 DSCP/CoS/IPP conversion drills.
  - 📝 Circuit S (§8.5) first run.
- **D175 · Sun 2 May · 1.5 h** — **Weekly review.**

#### Week 26 · 3–9 May 2027 · QoS II: MQC, policing, shaping, queuing + **Boson Exam A**
*Lab: **B04** (20 packet traces).*

- **D176 · Mon 3 May · 1.5 h**
  - 🎥 Arash: *MQC Foundations* + *MQC Classification* + *MQC Marking* + *QoS Traffic Policing & Shaping Fundamentals* + quizzes.
  - 🃏 +8: class-map `match-all` (default) vs `match-any`, policy order, `class-default`, `service-policy input/output`.
- **D177 · Tue 4 May · 1.5 h**
  - 🎥 Arash: *Single-Rate Two-Color* + *srTCM* + *MQC Policing* + *trTCM* + quizzes.
  - 🃏 +8: CIR/Bc/Be/PIR, conform/exceed/violate, `Tc = Bc / CIR`.
  - 🐍 Compute `Tc` for CIR 1,000,000 bps and Bc 8,000 bits; print in ms with `.1f`.
- **D178 · Wed 5 May · 1.5 h**
  - 🎥 Arash: *QoS Congestion Management* + *CBWFQ & LLQ* + *Congestion Avoidance* + *Advanced CBWFQ & Hierarchical QoS Queuing* + quizzes.
  - 🃏 +8: LLQ `priority` vs `bandwidth`, WRED, tail drop, parent shaper + child queuing.
- **D179 · Thu 6 May 🇳🇴 (Ascension) · 1.5 h**
  - 🧪 **B04 build:** annotate a full one-page QoS config (ACLs + 3–4 class-maps + policy-map + service-policy); build it; traffic generators with DSCP marks and sizes.
- **D180 · Fri 7 May · 1.5 h**
  - 🧪 B04 traces 1–10: predict class → action → outcome, then send and read `show policy-map interface`.
- **D181 · Sat 8 May · 4 h — Boson Exam A (study mode)**
  - 📝 **Boson ExSim Exam A** in study mode (§11.4). Mark untaught security/assurance items as "not yet studied" — don't panic about them.
  - 🧪 B04 traces 11–20 (if time; otherwise Sunday).
- **D182 · Sun 9 May · 2 h** — Review **every** Exam A item; error log; **weekly review**; Phase 5a gate: 20 traced packets with explanations.

### Phase 3b/5b — Overlays, server virtualization, design, SD-Access, SD-WAN

#### Week 27 · 10–16 May 2027 · LISP, VXLAN, server virtualization, NFV (2.3, 2.1)
*Labs: **B06**, **B05**. Optional LISP lab on IOS XE.*

- **D183 · Mon 10 May · 1.5 h**
  - 🎥 Arash: *LISP Architecture and IP Mobility* + quiz.
  - 🃏 +6: EID vs RLOC, identity/location split, why it helps mobility.
- **D184 · Tue 11 May · 1.5 h**
  - 🎥 Arash: *LISP Control Plane Operations* + quiz.
  - 🃏 +8: Map-Register, Map-Notify, Map-Request, Map-Reply, negative Map-Reply, MS vs MR, map-cache.
  - 🧠 N1·T6 LISP messages → sender/receiver.
- **D185 · Wed 12 May · 1.5 h**
  - 🎥 Arash: *LISP Packet Encapsulation* + quiz.
  - 📝 Diagram a LISP lookup with synthetic registrations (Host A → Host B across two xTRs).
  - 🃏 +4: UDP 4341 data / 4342 control.
- **D186 · Thu 13 May · 2 h**
  - 🎥 Arash: *LISP Interworking with Non-LISP Sites* + quiz.
  - 🃏 +8: ITR, ETR, xTR, PITR, PETR, PxTR — who encapsulates/decapsulates and when (the passer named all six).
  - 🧪 Optional: 2 xTRs + MS/MR on IOS XE; verify registrations and map-cache.
- **D187 · Fri 14 May · 1.5 h**
  - 🎥 Arash: *VXLAN and Traditional Layer 2 Networking* + *VXLAN Architecture Fundamentals* + *VXLAN Control Planes and SD-Access* + quizzes.
  - 🧪 **B06:** Linux VXLAN (`ip link add vxlan100 type vxlan id 100 … dstport 4789`) across a routed underlay; capture; label outer IP/UDP/VXLAN/inner Ethernet; VNI mismatch fault.
  - 🃏 +6: VTEP, 24-bit VNI, UDP 4789, ~50-byte overhead, flood-and-learn vs EVPN vs LISP control planes.
- **D188 · Sat 15 May · 3.5 h**
  - 🎥 Arash: *Server Virtualization and Data Center Networking* + *Server Virtualization and Virtual Networking* + *Network Functions Virtualization (NFV) Architecture* + quizzes.
  - 🧪 **B05:** two Linux nodes on separate bridges with tagged sub-interfaces; capture tags; compare bridge/macvlan/veth.
  - 📝 Finish the 2.3 comparison matrix (VRF, VLAN, VXLAN, GRE, LISP, IPsec).
  - 🃏 +8: type 1 vs type 2 (examples), VM components, vSwitch/vDS/OVS, NFV (VNF, NFVI, MANO).
- **D189 · Sun 16 May · 1.5 h** — **Weekly review.**

#### Week 28 · 17–23 May 2027 · Enterprise design + SD-Access (1.1, 1.3) 🇳🇴
*Labs: **B01**, **B03**.*

- **D190 · Mon 17 May 🇳🇴 (Constitution Day / Whit Monday) · 1 h**
  - 🎥 Arash: *Hierarchical LAN Design Model* + *High Availability in Network Design* + quizzes.
  - 🃏 +6.
- **D191 · Tue 18 May · 1.5 h**
  - 🎥 Arash: *Enterprise Network Architecture Designs* + *Cloud Network Design* + quizzes.
  - 🃏 +10: 2-tier/collapsed core vs 3-tier, L2 vs routed access, leaf-spine, IaaS/PaaS/SaaS, public/private/hybrid, cloud connectivity options.
- **D192 · Wed 19 May · 2 h**
  - 🧪 **B01:** 2-tier vs 3-tier routed campus; remove a core/aggregation link; time recovery; write a short design memo (choose + defend the rejected alternative).
- **D193 · Thu 20 May · 1.5 h**
  - 🎥 Arash: *Software-Defined Access (SD-Access) Architecture and DNA Center* + quiz.
  - 🃏 +8: planes — LISP control, VXLAN data, TrustSec/SGT policy, Catalyst Center management.
- **D194 · Fri 21 May · 1.5 h**
  - 🎥 Arash: *Cisco SD-Access Architecture* + quiz.
  - 🃏 +10: control-plane node (MS/MR), edge node, border node (internal/external/anywhere), intermediate node, **fabric WLC**, fabric AP (VXLAN to edge), extended node, VN vs SGT, anycast gateway.
- **D195 · Sat 22 May · 3.5 h**
  - 📝 Read the SD-Access Design Guide roles + transits + wireless sections (add to N2). Optional: first part of Arash *Wireless Network Architecture Models* for fabric-WLC context.
  - 🧪 **B03:** draw host onboarding and an edge-to-edge flow, plus a flow to a non-fabric legacy network via the border; label encap/decap and policy points. Make image-occlusion cards.
  - 🧠 N2·T1 "SD-Access roles and planes" (repeat until 10/10).
  - 📝 Circuit A.
- **D196 · Sun 23 May · 1.5 h** — **Weekly review.**

#### Week 29 · 24–30 May 2027 · Catalyst SD-WAN + connectivity troubleshooting (1.2, 6.4, 4.1)
*Lab: **B02**.*

- **D197 · Mon 24 May · 1.5 h**
  - 🎥 Arash: *Cisco SD-WAN Architecture and Solutions* — first half.
  - 🃏 +8: Manager (vManage) = management, Controller (vSmart) = control/OMP, Validator (vBond) = orchestration/auth/NAT traversal, WAN Edge (vEdge/cEdge) = data.
- **D198 · Tue 25 May · 1.5 h**
  - 🎥 Arash: *Cisco SD-WAN Architecture and Solutions* — second half + quiz.
  - 🃏 +10: OMP, TLOC (system IP + color + encapsulation), colors, VPN 0 / 512 / service VPNs, DTLS/TLS control, IPsec + BFD data, app-aware routing, benefits vs limitations.
- **D199 · Wed 26 May · 1.5 h**
  - 🎥 Arash: *Updates for Cisco SD-Access and SD-WAN* + quiz.
  - 🧪 **B02:** SD-WAN sandbox UI tour (devices, control connections, TLOCs, tunnels, BFD); draw onboarding of a new branch.
  - 🧠 N2·T6 components → planes.
- **D200 · Thu 27 May · 1.5 h**
  - 🧪 SD-WAN Manager API in Postman using the vendor docs/sandbox for the current auth flow (6.4) — don't assume it's the Catalyst Center token endpoint (§4 6.4).
  - 🃏 +4.
- **D201 · Fri 28 May · 1.5 h**
  - 🎥 Arash: *ICMP and Network Connectivity Troubleshooting* + quiz.
  - 🃏 +6: ICMP types/codes you'll see, extended ping options.
- **D202 · Sat 29 May · 3.5 h**
  - 🎥 Arash: *IPv4 Header and Traceroute Analysis* + quiz.
  - 🧪 Extended ping/traceroute with VRF, source, size, DF bit; find the path MTU through your W18 GRE tunnel; ICMP-disabled hop false positive.
  - 📝 Pearson: architecture chapters questions.
  - 📝 Circuit P.
- **D203 · Sun 30 May · 1.5 h** — **Weekly review + Phase 3b/5b gate:** draw SD-WAN, SD-Access and LISP/VXLAN diagrams from memory and defend design alternatives.

### Phase 4 — Assurance + operational security

#### Week 30 · 31 May–6 Jun 2027 · SNMP, syslog, NetFlow, SPAN family (4.1–4.3)
*Labs: **L16**, **L17**, **L18**, **L19**.*

- **D204 · Mon 31 May · 1.5 h**
  - 🎥 Arash: *SNMP Architecture and Operations* + quiz.
  - 🃏 +8: v1/v2c/v3, noAuthNoPriv/authNoPriv/authPriv, get/getnext/getbulk/set/trap/inform, UDP 161/162, MIB/OID.
- **D205 · Tue 1 Jun · 1.5 h**
  - 🎥 Arash: *Syslog and System Message Logging* + quiz.
  - 🃏 +8: severities 0–7 (mnemonic in Appendix A), facilities, `logging trap` level includes everything lower-numbered, timestamps, `terminal monitor`.
- **D206 · Wed 2 Jun · 2 h**
  - 🧪 **L16:** rsyslog + SNMPv3 authPriv `snmpwalk` + traps; conditional debug limited to one interface/neighbor, then `undebug all`; fault from §5.
  - 🃏 +4.
- **D207 · Thu 3 Jun · 2 h**
  - 🎥 Arash: *NetFlow Monitoring and Analysis* + *Flexible NetFlow Architecture and Operation* + quizzes.
  - 🧪 **L17:** custom record (match = key, collect = non-key) → exporter → monitor → interface; nfdump collector; fault #18 (monitor not applied).
  - 🃏 +6.
- **D208 · Fri 4 Jun · 1.5 h**
  - 🎥 Arash: *SPAN and Traffic Monitoring Fundamentals* + *RSPAN Implementation and Operation* + *Encapsulated Remote SPAN (ERSPAN)* + quizzes.
  - 🃏 +8: local SPAN, RSPAN VLAN (`remote-span`), ERSPAN (GRE, session ID), destination port behaviour.
- **D209 · Sat 5 Jun · 3.5 h**
  - 🧪 **L18** local SPAN to an analyzer; **L19** RSPAN across a trunk and ERSPAN across L3 (if your image supports it); fault #19.
  - 🧪 Boson: assurance Simulation labs.
  - 📝 Circuit A.
- **D210 · Sun 6 Jun · 1.5 h** — **Weekly review.**

#### Week 31 · 7–13 Jun 2027 · IP SLA, Catalyst Center assurance, security design (4.4, 4.5, 5.4)
*Labs: **L20**, **B11**, **B13**, **B14**. Project: **P4**.*

- **D211 · Mon 7 Jun · 1.5 h**
  - 🎥 Arash: *IP SLA and Object Tracking Operations* + quiz.
  - 🃏 +8: operation → schedule → track → `ip route … track`; `threshold` ≠ failover; udp-jitter needs a responder.
- **D212 · Tue 8 Jun · 2 h**
  - 🧪 **L20:** IP SLA ICMP echo to a distant target + track + floating static failover; fault #20 (operation never scheduled).
  - 🧪 **Timed exam-sim:** router + switch — **local SPAN + IP SLA + Flexible NetFlow** from blank ≤ 10 min (the reported multi-feature lab).
- **D213 · Wed 9 Jun · 1.5 h**
  - 🎥 Arash: *Cisco DNA Center Assurance and Client Insights* + *Network Assurance Updates* + quizzes.
  - 🧪 **B11:** Catalyst Center sandbox — inventory, health, issues, path trace; read Cisco's current pages on AI-powered assurance/analytics (4.5) and add them to N2.
  - 🃏 +8: Day-0/1/2 workflows, templates, PnP, SWIM, assurance, AI insights vs human-approved change.
- **D214 · Thu 10 Jun · 1.5 h**
  - 🎥 Arash: *Cisco Threat Defense and Security Solutions* + quiz.
  - 📝 Read the two **NGFW must-read** pages (§10) — add both to N2.
  - 🃏 +10: NGFW vs stateful firewall (app ID/control, IPS, URL filtering, identity, reputation/threat intel, malware/file inspection, TLS decryption), Secure Firewall/FTD/FMC, IDS vs IPS.
- **D215 · Fri 11 Jun · 1.5 h**
  - 🎥 Arash: *Network Access Control and Authentication Technologies* + quiz. Optional: EAP part of *EAP Authentication and the Four-Way Handshake*.
  - 🃏 +8: 802.1X roles, EAP methods, MAB, WebAuth, ISE posture/profiling, TrustSec classification/propagation/enforcement, MACsec 802.1AE + MKA.
- **D216 · Sat 12 Jun · 3.5 h**
  - 🧪 **B13** NGFW app-aware policy walkthrough; **B14** SGT matrix + MACsec vs IPsec trust map; threat model for branch/campus/DC (5.4.a *Do*).
  - 🧠 N2·T1 ×2 (NGFW; TrustSec/MACsec) — this is the buzzword area, repeat until confident.
  - 📝 **P4** (monitoring/SLO/incident) write-up.
- **D217 · Sun 13 Jun · 1.5 h** — **Weekly review.**

#### Week 32 · 14–20 Jun 2027 · ACLs in depth + user access (5.2.a, 5.1.a)
*Labs: **L25**, **L23**.*

- **D218 · Mon 14 Jun · 1.5 h**
  - 🎥 Arash: *Standard IPv4 Access Control Lists (ACLs)* + quiz.
  - 🃏 +6.
- **D219 · Tue 15 Jun · 2 h**
  - 🎥 Arash: *Extended IPv4 Access Control Lists (ACLs)* + quiz.
  - 🃏 +8: protocol numbers (OSPF 89, EIGRP 88, GRE 47, ESP 50, VRRP 112), ports, `established`, direction.
- **D220 · Wed 16 Jun · 2 h**
  - 🧪 **L25:** named ACL policy that blocks OSPF by mistake; **fix it by inserting a sequence-numbered line, deleting nothing**; verify hit counters and adjacency; negative test matrix.
  - 🧪 Boson: the OSPF/ACL Simulation lab the passer mentioned (and any other ACL labs).
- **D221 · Thu 17 Jun · 1.5 h**
  - 🎥 Arash: *Port Access Control Lists (PACLs)* + *VLAN Access Control Lists (VACLs)* + *ACL Processing and Downloadable ACLs (dACLs)* + quizzes.
  - 🃏 +6.
- **D222 · Fri 18 Jun · 1.5 h**
  - 🎥 Arash: *Securing User Access and Password Encryption* + quiz.
  - 🃏 +6: type 7 vs 5/8/9, `enable secret`, `service password-encryption` limits.
- **D223 · Sat 19 Jun · 3.5 h**
  - 🎥 Arash: *Privilege Levels and Role-Based Access Control (RBAC)* + quiz.
  - 🧪 **L23:** hardened SSH-only management with `access-class`, local users at different privilege levels, custom privilege for one command; break and recover from console.
  - 📝 Circuit S (ACL/CoPP packet traces).
- **D224 · Sun 20 Jun · 1.5 h** — **Weekly review.**

#### Week 33 · 21–27 Jun 2027 · SSH, AAA, ZBFW, CoPP (5.1, 5.2.b) — **Arash course finished**
*Labs: **L24**, **L26**, **C03**. Project: **P5**.*

- **D225 · Mon 21 Jun · 2 h**
  - 🎥 Arash: *Remote Access with Telnet and SSH* + quiz.
  - 🃏 +6: SSH prerequisites (hostname, domain, RSA keys, local user, `transport input ssh`).
- **D226 · Tue 22 Jun · 1.5 h**
  - 🎥 Arash: *Authentication, Authorization, and Accounting (AAA)* + quiz.
  - 🃏 +8: method lists, default vs named, **fallback only on server error/unreachable, not on reject**, TACACS+ vs RADIUS.
- **D227 · Wed 23 Jun · 2 h**
  - 🧪 **L24:** TACACS+/FreeRADIUS containers + local emergency account; test reachable/wrong password/server down/authz deny/fallback/accounting; fault #21. Keep a console session open.
- **D228 · Thu 24 Jun · 1.5 h**
  - 🎥 Arash: *Zone Based Firewall (ZBFW)* + quiz.
  - 🃏 +5: zones, zone-pairs, `inspect`/`pass`/`drop`, self zone — and how ZBFW differs from an NGFW.
- **D229 · Fri 25 Jun · 1.5 h**
  - 🎥 Arash: *Control Plane Policing (CoPP)* + quiz.
  - 🃏 +6: control vs data plane traffic, ACL permit = "belongs to class", `police`, `service-policy input` under `control-plane`.
- **D230 · Sat 26 Jun · 4 h**
  - 🧪 **L26:** CoPP protecting OSPF/BGP/management, policing ICMP; fault #17.
  - 🧪 **Timed exam-sim:** "fix the ACL so OSPF works without deleting anything + configure CoPP" ≤ 10 min.
  - 🧪 **C03** (observe and defend), single faults then hidden.
  - 📝 **P5** write-up.
- **D231 · Sun 27 Jun · 1.5 h** — **Weekly review + Phase 4 gate** (combined observability/security incident lab passed). 🎉 Course complete — re-score every blueprint ID (§9.2).

### Phase 7 — Integration and readiness

#### Week 34 · 28 Jun–4 Jul 2027 · Boson Exam B, automation re-gate, hidden faults

- **D232 · Mon 28 Jun · 2.5 h** — 📝 **Boson ExSim Exam B**, simulation mode, timed (120 min). Save `copy run start` on every device you touch in labs — practise the habit.
- **D233 · Tue 29 Jun · 2 h** — 📝 Review every Exam B item (right and wrong); error log; re-lab the top 3 misses.
- **D234 · Wed 30 Jun · 2 h** — 🧪 Remediate weakest domain #1: redo its Tier A labs from blank; 🧠 N3·T5 on that domain.
- **D235 · Thu 1 Jul · 2 h** — 🐍 **P6 (programmable operations)** part 1: inventory → structured JSON → validation → report; pytest.
- **D236 · Fri 2 Jul · 1.5 h** — 🐍 **Automation re-gate:** 30 timed items — Python output/format/loops/exceptions, JSON functions, cut-off scripts, HTTP codes, EEM action order, tool matching (🧠 N4·T4/T6 + Appendix B). Target ≥ 90%.
- **D237 · Sat 3 Jul · 4 h** — 🧪 **C01 + C02 from hidden multi-fault states** (§5 rule: only now combine faults). 🧪 Boson: every Simulation lab once, timed.
- **D238 · Sun 4 Jul · 1.5 h** — **Weekly review.**

#### Week 35 · 5–11 Jul 2027 · Boson Exam C, Cisco U, graduation test

- **D239 · Mon 5 Jul · 2.5 h** — 📝 **Boson Exam C**, simulation mode, timed.
- **D240 · Tue 6 Jul · 2 h** — 📝 Review Exam C; error log; cards from confidently-wrong items.
- **D241 · Wed 7 Jul · 2 h** — 🧪 Remediate weakest domain #2.
- **D242 · Thu 8 Jul · 2.5 h** — 📝 Optional **Cisco U practice exam** (mainly for its labs; caveats §11.1). Otherwise: P6 part 2.
- **D243 · Fri 9 Jul · 1.5 h** — 🧠 **Buzzword blitz** (N2·T1/T6): SD-WAN components/planes (old and new names), SD-Access planes/roles incl. fabric WLC, LISP roles (ITR/ETR/xTR/PITR/PETR/PxTR), VXLAN, NGFW, security portfolio, TrustSec/MACsec, Catalyst Center workflows and AI features.
- **D244 · Sat 10 Jul · 4 h** — 🧪 **C03 hidden state** + **§9.4 graduation test**. If every box is ticked (or nearly), **confirm/book the exam for D250**; if not, move D246–D250 back one or two weeks and repeat W34–W35 for the gaps.
- **D245 · Sun 11 Jul · 1.5 h** — **Weekly review**; recheck the Cisco blueprint for any newer revision (§9.4).

#### Week 36 · 12–16 Jul 2027 · Final exam, taper, **exam day**

- **D246 · Mon 12 Jul · 2.5 h** — 📝 **Boson Exam D**, simulation mode, timed.
- **D247 · Tue 13 Jul · 2 h** — 📝 Review Exam D; final pass through the whole error log (redo every logged item without notes).
- **D248 · Wed 14 Jul · 2 h** — 🧪 **Exam-sim set, 60 min:** (1) EtherChannel fix + STP, (2) multi-area OSPF + summarisation, (3) eBGP with many networks, (4) SPAN + IP SLA + FNF, (5) VRF + tunnel + static routes, (6) ACL-permits-OSPF + CoPP. **Save every device.** 🐍 15 timed Python/JSON items. 📝 Logistics: ID, test-centre address/route or online-proctoring system check, appointment time.
- **D249 · Thu 15 Jul · 1 h** — Taper: Appendix A, the DSCP/AF table, SD-WAN/SD-Access role tables, the `format()` table and JSON function rule from Appendix B; 20 min Anki. No new material. Sleep early.
- **D250 · Fri 16 Jul 2027 — 🎯 EXAM DAY** — see §14.

---

## 14. Exam day and after

**Exam morning (D250):**
1. Light breakfast; 10–15 min Anki *only if it calms you* — no new cards.
2. Quick look at Appendix A and Appendix B's JSON rule (`dump`/`load` = files, `dumps`/`loads` = strings).
3. Arrive early (or start the online check-in early) with the required ID.

**In the exam (from §8.4, plus the passers' advice):**
- **Labs:** read the whole task first; list every requirement (e.g. "without deleting anything", "only on SW2"); check current state with `show` before changing; verify each requirement after; **`copy running-config startup-config` on every device you changed** before moving on — one passer forgot and worried for the rest of the exam.
- **Multiple choice:** read what is actually asked (current behaviour vs best fix); eliminate with evidence; expect many questions to feel uncertain — passers report second-guessing and still passing. Don't let one item eat the time for the next five.
- **Code items:** trace line by line on the whiteboard (types, padding, newlines, file vs string).

**After the exam (D251+):**
- Note (privately, for yourself) which *areas* felt weak — not questions; Cisco's confidentiality rules apply (§10).
- Pass: update the portfolio README, publish sanitized labs/projects, choose the CCNP Enterprise concentration exam.
- Not yet: read the score report by domain, rebuild a 4–6 week plan from §13 for the weak domains, and rebook. The labs and cards you built are still yours.

---

## Appendix A — Numbers to memorise

**Administrative distance:** Connected 0 · Static 1 · eBGP 20 · EIGRP internal 90 · OSPF 110 · IS-IS 115 · RIP 120 · EIGRP external 170 · iBGP 200 · Unknown 255.

**IP protocol numbers:** ICMP 1 · TCP 6 · UDP 17 · GRE 47 · ESP 50 · AH 51 · EIGRP 88 · OSPF 89 · PIM 103 · VRRP 112.

**Ports:** SSH 22 · Telnet 23 · TACACS+ TCP 49 · DNS 53 · HTTP 80 · NTP UDP 123 · SNMP 161/162 · BGP TCP 179 · HTTPS/RESTCONF 443 · ISAKMP UDP 500 · syslog UDP 514 · NETCONF 830 · HSRP UDP 1985 · RADIUS 1812/1813 (legacy 1645/1646) · NetFlow commonly UDP 2055 · IPFIX 4739 · NAT-T UDP 4500 · LISP 4341 data / 4342 control · VXLAN UDP 4789 · CAPWAP 5246/5247 · PTP UDP 319/320.

**Multicast:** 224.0.0.0/4 · 232.0.0.0/8 SSM · 239.0.0.0/8 admin-scoped · 224.0.0.1 all hosts · .2 all routers (HSRPv1) · .5 OSPF all · .6 OSPF DR · .10 EIGRP · .13 PIM · .18 VRRP · .22 IGMPv3 · .102 HSRPv2. MAC `01:00:5E` + low 23 bits (32:1 overlap).

**FHRP:** HSRP vMAC `0000.0c07.acXX` (v1) / `0000.0c9f.fXXX` (v2), hello 3 s / hold 10 s, priority 100, preempt off · VRRP vMAC `0000.5e00.01XX`, priority 100, preempt on.

**OSPF network types:** broadcast (DR, 10/40) · point-to-point (no DR, 10/40) · non-broadcast (DR, 30/120, static neighbours) · point-to-multipoint (no DR, 30/120). **LSAs:** 1 router · 2 network · 3 summary · 4 ASBR summary · 5 external · 7 NSSA external · (v3: 8 link, 9 intra-area prefix).

**BGP best path ("We Love Oranges AS Oranges Mean Pure Refreshment"):** Weight (high) → Local Pref (high) → locally Originated → AS-path (short) → Origin (IGP < EGP < ?) → MED (low) → Paths: eBGP over iBGP → IGP metric to next hop → oldest eBGP path → Router ID (low) → neighbour IP (low). (AIGP, if used, is evaluated after locally originated.)

**STP:** priority increments of 4096 (default 32768 + VLAN as sys-ID-ext) · 802.1D timers 2/15/20 s · short costs 10 Mb=100, 100 Mb=19, 1 Gb=4, 10 Gb=2.

**DSCP:** EF 46 · AFxy = 8x + 2y (AF11 10, AF21 18, AF31 26, AF41 34) · CSx = 8x (CS1 8, CS3 24, CS6 48) · default 0.

**Syslog levels:** 0 Emergency · 1 Alert · 2 Critical · 3 Error · 4 Warning · 5 Notice · 6 Informational · 7 Debug (*Every Awesome Cisco Engineer Will Need Ice-cream Daily*).

## Appendix B — Verified Python & JSON drill bank

Cover the answers, predict, then run. **Every answer below was produced by running the code** (Python 3).

**`format()` mini-language — `{:[fill][align][sign][#][0][width][,][.precision][type]}`**

| Expression | Output |
|---|---|
| `"{:#>15}, {:#>7}".format("673624583672328", "jbdhs")` | `673624583672328, ##jbdhs` |
| `"{:#>15}".format("42")` | `#############42` |
| `"{:<8}\|{:>6}\|{:^7}\|".format("Gi1","up","1500")` | `Gi1     \|    up\| 1500  \|` |
| `"{:*^9}".format("SW")` | `***SW****` |
| `format(0.8, '.0%')` / `'.2%'` / `'.8%'` | `80%` / `80.00%` / `80.00000000%` |
| `"{:08.3f}".format(3.14159)` | `0003.142` |
| `"{:,}".format(1234567)` | `1,234,567` |
| `"{:x} {:#x} {:b} {:#b}".format(255,255,5,5)` | `ff 0xff 101 0b101` |
| `"{:05d}".format(42)` / `"{:+d}".format(42)` | `00042` / `+42` |
| `"{1} {0} {1}".format("a","b")` | `b a b` |
| `"%s has %d routes, %.2f%%" % ("R1",12,99.5)` | `R1 has 12 routes, 99.50%` |

`#` trap: in `{:#>15}` the `#` is the **fill** (because `>` follows it); in `{:#x}` it's the **alternate-form** flag.

**JSON rule:** `dump` = Python → JSON **file** · `dumps` = Python → JSON **string** · `load` = JSON **file** → Python · `loads` = JSON **string** → Python · `JSONEncoder().encode()` ≈ `dumps` · `JSONDecoder().decode()` ≈ `loads`. **"s" = string.**

```python
# 1
a = [10, 20, 30, 40, 50]
print(a[1:4], a[-2:], a[::-1][0])
```
<details><summary>Answer</summary><code>[20, 30, 40] [40, 50] 50</code></details>

```python
# 2
ints = {"Gi1": "up", "Gi2": "down", "Gi3": "down"}
count = 0
for k, v in ints.items():
    if v == "down":
        count += 1
        print(f"{k} needs attention")
print(count)
```
<details><summary>Answer</summary><code>Gi2 needs attention</code> / <code>Gi3 needs attention</code> / <code>2</code></details>

```python
# 3
try:
    vlan = int("Gi1")
except ValueError:
    print("bad value")
else:
    print("ok")
finally:
    print("done")
```
<details><summary>Answer</summary><code>bad value</code> / <code>done</code></details>

```python
# 4
print("10.1.1.1/24".split("/")[0].split(".")[-1], "/".join(["a","b"]), " R1 \n".strip().lower())
```
<details><summary>Answer</summary><code>1 a/b r1</code></details>

```python
# 5  RESTCONF-style payload
data = {"ietf-interfaces:interfaces": {"interface": [
          {"name": "GigabitEthernet1", "enabled": True},
          {"name": "Loopback0", "enabled": False}]}}
for i in data["ietf-interfaces:interfaces"]["interface"]:
    if not i["enabled"]:
        print(i["name"])
print(len(data["ietf-interfaces:interfaces"]["interface"]))
```
<details><summary>Answer</summary><code>Loopback0</code> / <code>2</code></details>

```python
# 6
for i in range(1, 10, 3):
    if i == 4:
        continue
    print(i, end=" ")
```
<details><summary>Answer</summary><code>1 7</code></details>

```python
# 7
x = [1, 2]; y = x; y.append(3)
print(x, x is y)
```
<details><summary>Answer</summary><code>[1, 2, 3] True</code></details>

```python
# 8
print(7 // 2, 7 % 2, 2 ** 3, 7 / 2, "ab" * 3)
```
<details><summary>Answer</summary><code>3 1 8 3.5 ababab</code></details>

```python
# 9
for idx, r in enumerate(["R1", "R2", "R3"], start=1):
    print(idx, r)
```
<details><summary>Answer</summary><code>1 R1</code> / <code>2 R2</code> / <code>3 R3</code></details>

```python
# 10
print([v for v in range(10, 60, 10) if v != 30])
```
<details><summary>Answer</summary><code>[10, 20, 40, 50]</code></details>

```python
# 11
d = {"a": 1}
print(d.get("b", "n/a"), d.get("a"))
```
<details><summary>Answer</summary><code>n/a 1</code></details>

```python
# 12
s = "GigabitEthernet0/1"
print(s[:2], s[-3:], s.replace("GigabitEthernet", "Gi"))
```
<details><summary>Answer</summary><code>Gi 0/1 Gi0/1</code></details>

```python
# 13
total, n = 0, 0
while True:
    n += 1
    if n > 4:
        break
    total += n
print(total)
```
<details><summary>Answer</summary><code>10</code></details>

```python
# 14
import json
s = json.dumps({"a": 1})
print(type(s).__name__, s, type(json.loads(s)).__name__)
print(json.JSONEncoder().encode({"x": None}), json.JSONDecoder().decode('{"x": true}'))
```
<details><summary>Answer</summary><code>str {"a": 1} dict</code> / <code>{"x": null} {'x': True}</code></details>

```python
# 15  fill in the blanks
import json
ospf = {"router_id": "192.168.1.1", "area": 0}
with open("ospf_backup.json", "w") as f:
    json.____(ospf, f)            # A
with open("ospf_backup.json") as f:
    cfg = json.____(f)            # B
body = json.____(ospf)            # C  -> a string
```
<details><summary>Answer</summary>A = <code>dump</code> · B = <code>load</code> · C = <code>dumps</code></details>

```python
# 16
print(sorted(["10.0", "2.0", "1.0", "1.5"]))   # how EEM sorts action labels (as strings)
```
<details><summary>Answer</summary><code>['1.0', '1.5', '10.0', '2.0']</code></details>

```python
# 17
print(json.dumps({"b": 2, "a": [1, True, None]}, sort_keys=True))
```
<details><summary>Answer</summary><code>{"a": [1, true, null], "b": 2}</code></details>

```python
# 18
print(list(zip(["R1", "R2"], ["1.1.1.1", "2.2.2.2"])))
```
<details><summary>Answer</summary><code>[('R1', '1.1.1.1'), ('R2', '2.2.2.2')]</code></details>

```python
# 19
print("{:<8}|{:>6}|{:^7}|".format("Gi1", "up", "1500"))
print(f"{'Gi0/1':<10}{'up':>6}")
```
<details><summary>Answer</summary><code>Gi1     |    up| 1500  |</code> / <code>Gi0/1         up</code></details>

```python
# 20
def add_vlan(v, vlans=[]):
    vlans.append(v)
    return vlans
print(add_vlan(10)); print(add_vlan(20))
```
<details><summary>Answer</summary><code>[10]</code> / <code>[10, 20]</code> (the default list is shared between calls)</details>

```python
# 21
import ipaddress
n = ipaddress.ip_network("10.1.0.0/22")
print(n.num_addresses, n.netmask, n.broadcast_address)
```
<details><summary>Answer</summary><code>1024 255.255.252.0 10.1.3.255</code></details>

```python
# 22
inventory = [{"item_id": "673624583672328", "item_code": "jbdhs"},
             {"item_id": "42", "item_code": "ab"}]
for item in inventory:
    print("{:#>15}, {:#>7}".format(item["item_id"], item["item_code"]))
```
<details><summary>Answer</summary><code>673624583672328, ##jbdhs</code> / <code>#############42, #####ab</code></details>

**JSON — find all the errors:**
```text
{
  'hostname': "R1",
  "interfaces": [
    {"name": "Gi1", "enabled": True, "mtu": 1500,},
  ],
  "ntp": None
}
```
<details><summary>Answer</summary>Single-quoted key · <code>True</code> → <code>true</code> · trailing comma after <code>1500</code> · trailing comma after the object in the array · <code>None</code> → <code>null</code>.</details>

**Catalyst Center requests skeleton (write it from memory by D236):**
```python
import requests
from requests.auth import HTTPBasicAuth

BASE = "https://<catalyst-center-sandbox>"
r = requests.post(f"{BASE}/dna/system/api/v1/auth/token",
                  auth=HTTPBasicAuth("user", "pass"), verify=False)   # step 1: POST + Basic Auth
token = r.json()["Token"]
headers = {"X-Auth-Token": token, "Content-Type": "application/json"} # step 2: token header
devices = requests.get(f"{BASE}/dna/intent/api/v1/network-device", headers=headers, verify=False)
if devices.status_code == 200:
    for d in devices.json()["response"]:
        print("{:<20}{:<16}{}".format(d["hostname"], d["managementIpAddress"], d["platformId"]))
else:
    print("Error:", devices.status_code)
```
*(`verify=False` is lab-only; in production verify certificates (§5.3). Get the current sandbox URL and credentials from DevNet.)*

## First 14 days — concrete starting sequence

> *(Kept from the original guide for reference. §13 Days 1–14 expands this into a dated, day-by-day version with the same steps plus Arash videos, NotebookLM quizzes, Boson ExSim and daily Python.)*

**Day 1:** Create Git repository, set up Markdown notes, record your target timeframe and free resources, download official v1.2 blueprint, take a short legitimate no-notes baseline, write initial competency scores.

**Days 2–3:** Verify host virtualization and Containerlab environment, choose a legal open routing image, deploy two routers and two host containers, ping IPv4/IPv6, inspect interface/routing table and capture traffic. Prove destroy/redeploy; create a reusable results template.

**Days 4–5:** Refresh VLSM/summarization, IPv6, Linux, Docker and Python fundamentals. Solve 20 original JSON/Python questions in the interpreter. Make cards only from gaps discovered.

**Days 6–7:** Establish Git workflow, build a small routed topology, collect `show` outputs, inject an incorrect route, fix it, save a one-page postmortem and rehearse operational rollback.

**Days 8–9:** Study 3.1.a (802.1Q) using Cisco docs + your main course. Draw topology, write two VLAN test matrices, perform L01 using a licensed IOS-L2-capable platform **if available**; otherwise use Linux/OVS bridge for tagging behavior while identifying Cisco CLI differences.

**Days 10–11:** Study 3.1.b EtherChannel; practice LACP and errors in L02 on a suitable switch image. Check administrative vs operational modes, capture LACP frames if supported.

**Days 12–13:** Study 3.1.c RSTP; build L03, select root, remove a link, deliberately trigger a guard in isolated lab; document port roles and restore.

**Day 14:** Closed-notes review: describe trunks, EtherChannel, RSTP and a basic packet walk; complete 15 novel questions plus a 30-minute troubleshooting exercise; update blueprint status and set next fortnight's objectives. Keep Python/spaced recall alive every day.

---

> **Final principle:** Certification is the milestone. The enduring asset is a version-controlled lab portfolio where you can **design it, build it, explain it, break it, repair it, automate it, and prove it works**.