<a href="https://adriansalas.tech"><img src="banner.png" alt="Adrián Salas Pérez — sysadmin and junior pentester (eJPT)" width="100%"></a>

### Sysadmin by day. Breaking my own lab by night.

I'm Adrián, a systems administrator from Palencia, Spain, working my way into offensive security.
I keep production servers running for a living. At home I build networks so I can attack them and see where they give way.

[![Website](https://img.shields.io/badge/web-adriansalas.tech-FF4B3A?style=for-the-badge&labelColor=2B2B31)](https://adriansalas.tech)
[![LinkedIn](https://img.shields.io/badge/linkedin-adriansalastech-4C8DFF?style=for-the-badge&labelColor=2B2B31)](https://www.linkedin.com/in/adriansalastech/)
[![Email](https://img.shields.io/badge/email-adrian%40adriansalas.tech-F1EEE8?style=for-the-badge&labelColor=2B2B31)](mailto:adrian@adriansalas.tech)
<br>
![eJPTv2 certified](https://img.shields.io/badge/eJPTv2-certified-3DD68C?style=for-the-badge&labelColor=2B2B31)
![CPTS in progress](https://img.shields.io/badge/CPTS-in_progress-9FEF00?style=for-the-badge&labelColor=2B2B31&logo=hackthebox&logoColor=9FEF00)

---

## What I've built

### [palantir](https://github.com/salitress/palantir) — recon that stops where exploitation starts

[![release](https://img.shields.io/github/v/release/salitress/palantir?style=flat&labelColor=2B2B31&color=FF4B3A)](https://github.com/salitress/palantir/releases)
[![selftest](https://img.shields.io/github/actions/workflow/status/salitress/palantir/selftest.yml?style=flat&labelColor=2B2B31&label=selftest)](https://github.com/salitress/palantir/actions/workflows/selftest.yml)
[![licence](https://img.shields.io/github/license/salitress/palantir?style=flat&labelColor=2B2B31&color=F1EEE8&label=licence)](https://github.com/salitress/palantir/blob/main/LICENSE)
[![stars](https://img.shields.io/github/stars/salitress/palantir?style=flat&labelColor=2B2B31&color=F1EEE8)](https://github.com/salitress/palantir/stargazers)

An nmap-driven recon scanner for authorised labs and engagements (HTB, CPTS, OSCP).
One command takes a target from port discovery to a report:

```text
ping sweep → ports → service enumeration → UDP → banner grabbing
           → per-protocol footprinting (SMB, LDAP, Kerberos, MSSQL, NFS, SNMP, web…)
           → known exploits (searchsploit, offline) → verified default credentials
           → web and vhost fuzzing → HTML / Markdown report
```

Everything it does is read-only. Nothing is exploited automatically: each next step is left as a command ready to copy.
A single Python 3 file with a standard-library-only core; every external tool is optional and skipped if it's missing.

### [kerbrute](https://github.com/salitress/kerbrute) — a fork I fixed before I trusted it

![language](https://img.shields.io/github/languages/top/salitress/kerbrute?style=flat&labelColor=2B2B31&color=4C8DFF)
![last commit](https://img.shields.io/github/last-commit/salitress/kerbrute?style=flat&labelColor=2B2B31&color=F1EEE8)

I read the whole codebase before changing anything, and found five real bugs:

- `--delay` never actually forced a single thread, so "slow" runs still sent requests in parallel.
- `-o / --output` wrote nothing: a second internal logger silently replaced the configured one.
- Windows-format wordlists (`\r\n`) corrupted usernames and passwords without any warning.
- `KDC_ERR_ETYPE_NOSUPP` aborted the whole run instead of skipping that one account.
- A duplicated error check that was dead code.

Then I added what I was missing: `--jitter` to randomise the delay, `--lockout-threshold` to stop trying an account before it locks, and `--json` for clean NDJSON output that pipes into `jq`.

### [Honeypot SIEM](https://adriansalas.tech/proyectos/honeypot/) — real attackers, watched live

[![dashboard](https://img.shields.io/website?url=https%3A%2F%2Fadriansalas.tech%2Fproyectos%2Fhoneypot%2Fdashboard%2F&label=dashboard&up_message=live&down_message=offline&up_color=3DD68C&style=flat&labelColor=2B2B31)](https://adriansalas.tech/proyectos/honeypot/dashboard/)

A Cowrie SSH honeypot feeding Elasticsearch through native ingest pipelines, with Kibana on top and a Python bot that sends alerts to Telegram. It runs on my own Proxmox and pfSense, and it was my final-year project for ASIR (2026).
The dashboard is public: **[see who is knocking right now](https://adriansalas.tech/proyectos/honeypot/dashboard/)**.

---

## Where I am on the road

```text
[x]  SMR      Microcomputer Systems and Networks (vocational diploma)
[x]  ASIR     Network Systems Administration (higher vocational diploma)
[x]  eJPTv2   INE Security — 88 %, September 2026
[~]  CPTS     Hack The Box — in progress
[ ]  CWES     Hack The Box
[ ]  OSCP     OffSec
[ ]  OSEP     OffSec
```

## Day job

**Systems Administrator at ICON Multimedia** (Palencia), since March 2026: production servers, Windows Server roles, VMware vSphere and Proxmox, and pfSense with VLANs, firewalling and NAT.

## What I work with

<img src="https://skillicons.dev/icons?i=linux,kali,windows,powershell,bash,py,docker,git,elasticsearch,nginx&theme=dark&perline=10" alt="Linux, Kali, Windows, PowerShell, Bash, Python, Docker, Git, Elasticsearch, nginx" height="42">

**Systems** &nbsp; GNU/Linux / Windows Server / Proxmox VE / VMware vSphere / Docker<br>
**Networks** &nbsp; pfSense / VLANs / Cisco / DNS and DHCP / firewalls and ACLs<br>
**Offence** &nbsp; nmap / NetExec / Impacket / ffuf / searchsploit / Active Directory<br>
**Defence** &nbsp; Elastic Stack (SIEM) / honeypots / hardening<br>
**Code** &nbsp; Python / Bash / Git

## How I work

- **By hand first.** I automate a step only once I've done it manually enough times to know what it should do.
- **Read before running.** If I'm going to depend on a tool, I read its code. That is how the kerbrute fixes happened.
- **Write it down.** Every module I study and every box I break ends up in my notes.

---

Open to junior roles in pentesting or SOC, on-site in Spain or remote. Spanish is my native language and my English is B2.
The quickest way to reach me is [adrian@adriansalas.tech](mailto:adrian@adriansalas.tech).
