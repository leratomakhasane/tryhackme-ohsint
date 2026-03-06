# 🔍 Project: TryHackMe — OhSINT

> **Platform:** TryHackMe | **Room:** OhSINT | **Difficulty:** Easy<br>
> **MITRE Tactic:** TA0043 — Reconnaissance<br>
> **Learning Path:** SOC Analysis → Incident Response → DFIR

###### ⚠️ Spoiler Warning
>This write-up documents my methodology and thought process after completing the room. If you haven't attempted OhSINT yet, I'd encourage you to try it first — the learning is in the doing.
[Try it on TryHackMe →](https://tryhackme.com/room/ohsint)


## 🎯 Objective
Given a single image file (WindowsXP.jpg), perform open-source intelligence (OSINT) gathering to uncover as much information about the file's owner as possible — with no other starting context.\
This challenge simulates the **pre-attack reconnaissance phase** used by real threat actors, mapped directly to the **MITRE ATT&CK framework**. The goal is to develop the investigative pivot mindset foundational to SOC analysis, incident response, and digital forensics.


## 🧠 Skills Learned
- Extracting and interpreting **EXIF/file metadata** using ExifTool
- **Username pivoting** across social media, code repositories, and personal sites
- Performing **passive OSINT** without direct target interaction
- **Geolocating** a **target** using a Wi-Fi BSSID and Wigle.net
- Identifying **obfuscated data** hidden in HTML/CSS source code
- Mapping findings to the **MITRE ATT&CK framework** (TA0043 Reconnaissance)
- Thinking in **evidence chains** — connecting artifacts into a full intelligence picture
- Applying an **attacker's perspective** to understand blue team detection opportunities

## 🛠️ Tools
- **ExifTool** — metadata extraction from image files
- **Google** — passive OSINT, username enumeration across platforms
- **Twitter/X** — social media profile analysis
- **GitHub** — public repository review for exposed sensitive data
- **Wigle.net** — BSSID-to-location geolocation mapping
- **Browser DevTools** — HTML/CSS source inspection to uncover hidden content
- **WordPress** — blog platform analysis for exposed personal information
