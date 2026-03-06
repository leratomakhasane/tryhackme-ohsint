# Project: TryHackMe — OhSINT

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

## 🔍 Steps Performed
**Step 1 — Metadata Extraction**\
**MITRE: T1592 — Gather Victim Host Information**\
The first action when handling any unknown file is to examine its metadata — this is standard practice in both OSINT investigations and DFIR work.
```
exiftool WindowsXP.jpg
```
Analysing the EXIF data revealed an attributed field that provided a starting username — the initial pivot point for all further investigation.\
![Screenshot of the output from the exiftool]()

**Step 2 — Username Pivoting & Social Media OSINT**\
**MITRE: T1593 — Search Open Websites/Domains | T1593.001 — Social Media**\
With a username in hand, the next step was passive reconnaissance — searching publicly available sources without any direct interaction with systems.
```
Google search: [discovered username]
```
This surfaced several publicly accessible profiles across different platforms, each containing additional clues that could be chained together

**Step 3 — Geolocation via BSSID**\
**MITRE: T1591.001 — Determine Physical Locations**\
One of the discovered profiles contained a network identifier — specifically a BSSID (Wi-Fi access point hardware address). This type of data, when cross-referenced with public wireless databases, can resolve to a physical location.

**Step 4 — Hidden Data Discovery**\
**MITRE: T1027 — Obfuscated Files or Information**\
A personal blog associated with the target contained information that was not immediately visible — only accessible by inspecting the raw page source rather than the rendered view.

🗺️ MITRE ATT&CK Mapping
Technique ID | Name | Application
--- |--- | ---
TA0043 | Reconnaissance | Overarching tactic for the entire room
T1592 | Gather Victim Host Information | EXIF metadata extraction via ExifTool
T1593 | Search Open Websites/Domains | Username pivot across public platforms
T1593.001 | Social Media | Social media profile enumeration
