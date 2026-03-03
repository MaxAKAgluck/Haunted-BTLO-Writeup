
# Haunted-BTLO-Writeup

## Description

Haunted Company Inc., a long-established Credit Reporting Agency, has been successfully operating in major financial hubs such as New York, London, and Tokyo. As a privately owned entity without external investors, the company has maintained consistent client satisfaction and steady earnings reports. With plans for expansion, the management has decided to take the company public, and the Initial Public Offering (IPO) is scheduled to occur within the next few days.

However, a crisis emerged just as the IPO date approaches. One of the company's websites has been defaced, raising alarms. Shortly after, it is discovered that the company's Tokyo server has come under attack. Concerned about the timing and the potential damage to the company’s reputation, the management is determined to identify the threat actor behind this attack and understand the breach mechanism to create detection before the IPO.

As a Threat Intelligence Analyst, you are tasked with collaborating with other analysts to uncover the identity of the adversary and assess the situation.

Available External and Internal Threat Intelligence:

New York (External: Business Commonality): Report on the 2017 GenX Breach, a major cyber attack on a leading Credit Reporting Agency. London (Internal Intelligence: Adversary Analysis): Analysis report for Haunted Company Inc., including Asset-Threat Mapping and adversary analysis featuring FIN7, APT27, Twisted Spider, and TG-3390, all of which are known to target the finance sector. Tokyo (Cyber Activity Attribution): Malware analysis from the compromised server, providing critical insights into the tools used during the attack.

We are presented with a lab instance; however, the first questions focus on threat intel and OSINT, so it doesn't require digging into the lab.

1. In 2017, a well-known company was attacked. What is the name of the company, its country of origin, and its business model? (Format: XxxX Xxxxxxxxx, XX, Xxxxx Xxxxxxxxx Xxxxxx)

This was a little confusing, but based on the threat intel we are given in the description, I googled this:

<img width="1696" height="1111" alt="image" src="https://github.com/user-attachments/assets/a9f1c1af-6e2c-499e-b423-fdd42b7d14ed" />

So based on the info we have, the answer is GenX Financial, US, credit reporting agency

2. According to the data breach summary, one of their critical assets was compromised, and they later discovered a vulnerability in one of their public-facing applications. What type of weakness was exploited to breach their network? (Format: Axxxxxxxxxx Vxxxxxxxxxxxxx)

This required reading the actual report on the vulnerability (https://archive.epic.org/privacy/data-breach/equifax/):

<img width="1907" height="330" alt="image" src="https://github.com/user-attachments/assets/4ec88a77-647c-4e5d-9f5f-c634b9af754f" />

Answer would be Application vulnerability since asked for a type.

3. How long did this breach go undetected? What was the Mean Time to Detect (MTTD)? (Format: XX days)

This info is readily available on wiki:

<img width="1518" height="351" alt="image" src="https://github.com/user-attachments/assets/7bfb31c1-2df1-4175-9650-dbbd4f7226db" />

4. What application was targeted by the attacker? What vulnerability was exploited, and where is this application located within the network? (Format: Xxxxxx Xxxxxx, CVE-XXXX-XXXX, XXXX)

This info was in the report provided earlier.

5. The attackers exfiltrated millions of records. How many consumer details were estimated to be exposed? How, and through which channel, was the data exfiltrated from the premises? (Format: XXX Million, xxxxxxxxx)

Google AI overview is useful for this:

<img width="1478" height="784" alt="image" src="https://github.com/user-attachments/assets/f4360ce2-278e-43a8-acce-a4c95212e68c" />

6. Later, during the investigation, a flaw was discovered in their ACIS code rendering system. What were these flaws? (Format: XXX Xxxxxxxxx, Xxxxxxxx Xxxxxx Xxxxxx Xxxxxxxxx)

There is also a pdf report I found which contains answer to this question specifically: https://oversight.house.gov/wp-content/uploads/2018/12/Equifax-Report.pdf

<img width="2042" height="390" alt="image" src="https://github.com/user-attachments/assets/0349f11f-df40-492f-9194-7ec410b2acc7" />

7. What file was inserted during the attack, and which country did the attack originate from? (Format: XXX, Xxxxx)

Searching the report for keywords:

<img width="2125" height="543" alt="image" src="https://github.com/user-attachments/assets/65ece3a3-d4c0-40f5-b20d-3589e9ca636f" />

Since the wiki report indicated this breach is associated with ''China's People's Liberation Army'' we can answer: JSP, China

8. It is said that if a specific network security technique had been properly implemented, the attacker likely would have failed to accomplish their mission. What is this technique called? (Format: Nxxxxxx Sxxxxxxxxxxx)

This info is again in the report, under the anatomy:

<img width="2179" height="666" alt="image" src="https://github.com/user-attachments/assets/02bfc2d5-eafd-4acb-8fd2-e785517e8f94" />

9. Adversary Analysis, this one group in particular as being involved in numerous attacks, including an attack on a medical research company during COVID-19. What is the name of this threat group (according to MITRE), what threat vector do they use, what is their country of origin, and what is their motivation? (Format: XXXX, Xxxxxxxxxx, Xxxxxx, Xxxxxxxxx)

This question was a bit misleading for me, but then I realised this probably doesn't correlate with the previous questions (as I didn't find a specific APT involved in the Equifax breach).

As I started researching, several groups stood out and I couldn't decide which one is meant in the question, so I went to the lab environment to check out if I missed something. In the readme several reports were mentioned but I thought these are only names serving as hints, because in the investigation folder on Desktop there were no such files. Still, I searched the disk C and actually found these reports in zip files!

<img width="898" height="162" alt="image" src="https://github.com/user-attachments/assets/f4019f69-b7e4-4d00-81b5-4400f8dc824f" />

Only when I opened them I realised that all info could probably obtained from these 😅.

I checked out the reports and APTs that there mentioned there and found this:

<img width="1255" height="867" alt="image" src="https://github.com/user-attachments/assets/50be7816-bf86-4b42-a236-5f98be03eeb1" />

It is the right answer - FIN7, ransomware, Russia, financial

10. Investigating the other threat group. What is the APT number assigned to this group? What is the name of the specific operation that involved dropping web shells on SharePoint servers? In what year was this group first observed, and what is their possible motivation?

This simply requires checking the other report (which I already read at that time):

<img width="1465" height="574" alt="image" src="https://github.com/user-attachments/assets/099d90be-c065-4bf7-912d-b2484a56b3d2" />

Answer is APT27, SharePoint Server Compromise, 2010, Espionage.

11. Haunted Company Inc. in Tokyo is under cyber attack. Based on the IOCs that were provided (hint: BAT!), what attack vectors did the threat actor use? (Format: Sxxxxx Exxxxxxxxxx, Wxxxxxxx)

I looked at the TokyoIOC folder:

<img width="1041" height="77" alt="image" src="https://github.com/user-attachments/assets/dca856f7-ecd8-4053-b67f-f9371fd0f233" />

But the files are password-protected and there is also an archive passwords.zip which hints we need to access it first.

Initial investigation folder has a link to the "haunted" website, so I went there first:

<img width="1713" height="755" alt="image" src="https://github.com/user-attachments/assets/b8ddc23f-0eb5-4741-b967-b3f99acdc90a" />

There is a script section with full html encoded in b64:

```html
<script>
  // Base64-encoded version of the full HTML code
  const base64Content = `PCFET0NUWVBFIGh0bWw+CjxodG1sIGxhbmc9ImVuIj4KPGhlYWQ+CiAgICA8bWV0YSBjaGFyc2V0PSJVVEYtOCI+CiAgICA8bWV0YSBuYW1lPSJ2aWV3cG9ydCIgY29udGVudD0id2lkdGg9ZGV2aWNlLXdpZHRoLCBpbml0aWFsLXNjYWxlPTEuMCI+CiAgICA8dGl0bGU+VHJpY2sgb3IgVGhyZWF0OiBIYXVudGVkIEZlc3RpdmFsPC90aXRsZT4KICAgIDxzdHlsZT4KICAgICAgICBAZm9udC1mYWNlIHsKICAgICAgICAgICAgZm9udC1mYW1pbHk6ICdDcmVlcHN0ZXInOwogICAgICAgICAgICBzcmM6IHVybCgnZm9udHMvQ3JlZXBzdGVy`
</script>
```

Decoding and we get a hint at what file contains the pass to zip archive:

<img width="613" height="185" alt="image" src="https://github.com/user-attachments/assets/f6a594be-de35-48cf-8a31-978df63f9ac3" />

Check metadata (sorry I was too lazy to open exiftool):

<img width="362" height="205" alt="image" src="https://github.com/user-attachments/assets/2796964d-aac7-4c50-b099-e7addf1cde3a" />

After opening passwords.zip we get a pass: ''hauntedfestival666''

I used it to open TokyoIOC folder, there are 2 docs - rtf and aspx.

Based on these malicious files the answer is Social Engineering, Webshell since rtf contains script code that is executed after opening it and aspx file has ExternalURL value which contains injected server-side script.

12. One of the IOCs contains shellcode. Use a tool and review the output to identify the offset of the PEB (Process Environment Block). (Hint: Output + OSINT!) (Format: 0x..)

This requires us to use OfficeMalScanner.

I decided to scan the rtf since its the most likely candidate for executable code:

<img width="765" height="165" alt="image" src="https://github.com/user-attachments/assets/e9d2528e-f7e3-4f52-a916-08bff692dea0" />

I then used rtfscan as suggested:

<img width="1013" height="531" alt="image" src="https://github.com/user-attachments/assets/982bf746-6dcf-4eba-b4e2-681d845962dc" />

I then used GPT on how to interpret the output and get the PEB offset:

<img width="1290" height="432" alt="image" src="https://github.com/user-attachments/assets/9ea78cc9-3384-434d-8f55-9a84403eef7e" />

The answer is 0xcc.

13. Based on the intelligence gathered, which threat group was responsible for the cyberattack on Haunted Company Inc.? What is the name of the malware they used to compromise Tokyo's infrastructure? (Hint: OSINT!) (Format: Xxxxxx Xxxxx-XXXX, XxxxxXxxxxxx)

Since we choose between 2 groups described in local/internal reports, I suspected that APT27 fits the profile much better, I then used the hash of the rtf file and queried virustotal, immediately found the connection:

<img width="1271" height="100" alt="image" src="https://github.com/user-attachments/assets/27afd472-a033-4aa1-8c66-5c73aa5b30cf" />

The report also mentions this behaviour:

```text
ChinaChopper a web-based executable script is dropped via asystem token, involves identifying the Exchange server and attempting to install theOwaAuth web shell to the web directory to establish persistence.
```

which is what we saw in the IOC files.

Therefore the answer is Threat group-3390, ChinaChopper.

15. Referring to the Asset-Threat Diagram which is an integral part of building intelligence, It appears the attacker exploited a vulnerability in Tokyo's infrastructure. What is the latest CVE for the version the threat actor targeted, and what type of attack was it? (Format: CVE-XXXX-XXXXX, XXX)

This diagram is found in the same zip as the reports. As we found earlier, attackers used a webshell, and looking at the diagram Apache Struts seems to be the perfect candidate, so I googled:

<img width="1189" height="670" alt="image" src="https://github.com/user-attachments/assets/4041ce21-09a1-4a52-961b-bf1488c95447" />

Seems like recently there was another rce CVE discovered :), but we are interested in the year 2023, which is the answer: CVE-2023-50164, RCE.

In conclusion, I would say it is an interesting room on Threat Intel and OSINT, a bit misleading in the sense that folders are located on the disk and we're not given exact paths and need to figure this out ourselves.
