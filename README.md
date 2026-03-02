# Haunted-BTLO-Writeup

Description:'''Haunted Company Inc., a long-established Credit Reporting Agency, has been successfully operating in major financial hubs such as New York, London, and Tokyo. As a privately owned entity without external investors, the company has maintained consistent client satisfaction and steady earnings reports. With plans for expansion, the management has decided to take the company public, and the Initial Public Offering (IPO) is scheduled to occur within the next few days.

However, a crisis emerged just as the IPO date approaches. One of the company's websites has been defaced, raising alarms. Shortly after, it is discovered that the company's Tokyo server has come under attack. Concerned about the timing and the potential damage to the company’s reputation, the management is determined to identify the threat actor behind this attack and understand the breach mechanism to create detection before the IPO.

As a Threat Intelligence Analyst, you are tasked with collaborating with other analysts to uncover the identity of the adversary and assess the situation.

Available External and Internal Threat Intelligence:

New York(External: Business Commonality): Report on the 2017 GenX Breach, a major cyber attack on a leading Credit Reporting Agency. London(Internal Intelligence: Adversary Analysis): Analysis report for Haunted Company Inc., including Asset-Threat Mapping and adversary analysis featuring FIN7, APT27, Twisted Spider, and TG-3390, all of which are known to target the finance sector. Tokyo(Cyber Activity Attribution): Malware analysis from the compromised server, providing critical insights into the tools used during the attack. '''.

We are presented with a lab instance, however first questions focus on threat intel and osint so it doesn't require digging into the lab.

1. In 2017, a well-known company was attacked. What is the name of the company, its country of origin, and its business model? (Format: XxxX Xxxxxxxxx, XX, Xxxxx Xxxxxxxxx Xxxxxx) 

This was a little confusing but based on threat intel we are given in description, I googled this:

<img width="1696" height="1111" alt="image" src="https://github.com/user-attachments/assets/a9f1c1af-6e2c-499e-b423-fdd42b7d14ed" />

So based on info we have the answer is GenX Financial, US, credit reporting agency

2. According to the data breach summary, one of their critical assets was compromised, and they later discovered a vulnerability in one of their public-facing applications. What type of weakness was exploited to breach their network? (Format: Axxxxxxxxxx Vxxxxxxxxxxxxx) 

This required to read the actual report on the vulnerability (https://archive.epic.org/privacy/data-breach/equifax/):

<img width="1907" height="330" alt="image" src="https://github.com/user-attachments/assets/4ec88a77-647c-4e5d-9f5f-c634b9af754f" />

Answer would be Application vulnerability since asked for a type.

3. How long did this breach go undetected? What was the Mean Time to Detect (MTTD)? (Format: XX days) 

This info is readily available on wiki: 

<img width="1518" height="351" alt="image" src="https://github.com/user-attachments/assets/7bfb31c1-2df1-4175-9650-dbbd4f7226db" />

4. What application was targeted by the attacker? What vulnerability was exploited, and where is this application located within the network? (Format: Xxxxxx Xxxxxx, CVE-XXXX-XXXX, XXXX)

This info was in the report provided earlier.

5. The attackers exfiltrated millions of records. How many consumer details were estimated to be exposed? How, and through which channel, was the data exfiltrated from the premises? (Format: XXX Million, xxxxxxxxx)

Google AI overview is very useful for this:

<img width="1478" height="784" alt="image" src="https://github.com/user-attachments/assets/f4360ce2-278e-43a8-acce-a4c95212e68c" />

6. Later, during the investigation, a flaw was discovered in their ACIS code rendering system. What were these flaws? (Format: XXX Xxxxxxxxx, Xxxxxxxx Xxxxxx Xxxxxx Xxxxxxxxx)

There is also a pdf report which contains answer to this question specifically: https://oversight.house.gov/wp-content/uploads/2018/12/Equifax-Report.pdf

<img width="2042" height="390" alt="image" src="https://github.com/user-attachments/assets/0349f11f-df40-492f-9194-7ec410b2acc7" />

7. What file was inserted during the attack, and which country did the attack originate from? (Format: XXX, Xxxxx) 

Searching the report for keywords:

<img width="2125" height="543" alt="image" src="https://github.com/user-attachments/assets/65ece3a3-d4c0-40f5-b20d-3589e9ca636f" />

Since the wiki report indicated this breach is associated with ''China's People's Liberation Army '' we can answer: JSP, China

8. It is said that if a specific network security technique had been properly implemented, the attacker likely would have failed to accomplish their mission. What is this technique called? (Format: Nxxxxxx Sxxxxxxxxxxx)

This info is again in the report, under the anatomy:

<img width="2179" height="666" alt="image" src="https://github.com/user-attachments/assets/02bfc2d5-eafd-4acb-8fd2-e785517e8f94" />

9. Adversary Analysis, this one group in particular as being involved in numerous attacks, including an attack on a medical research company during COVID-19. What is the name of this threat group (according to MITRE), what threat vector do they use, what is their country of origin, and what is their motivation? (Format: XXXX, Xxxxxxxxxx, Xxxxxx, Xxxxxxxxx)

