# Exploit Description 

The CVE-2017-0199 is an exploit that allows the remote execution of code
on the target system, via a specially crafted RTF document abusing the
Object Linking and Embedding (OLE) API.

Currently, the known vulnerable platforms are:

-   Microsoft Office (2007, 2010, 2013, 2016)
-   Windows Vista
-   Windows Server 2008
-   Windows 7
-   Windows 8.1

## Origin

The exploit was discovered in July of 2016, when Ryan Hanson, an Idaho
State University graduate and consultant at boutique security firm Optiv
Inc in Boise, found a weakness in the way that Microsoft Word processes
documents from another format. That allowed him to insert a link to a
malicious program that would take control of a computer. Hanson then
continued to exploit the flaw, combining it with others to make it even
deadlier. In October of 2016, he reported it to Microsoft, expecting to
receive a so called bug-bounty.

## Known uses of the exploit

There are several exploits available on <https://www.exploit-db.com>,
including one already automated as a payload on the Metasploit
framework, found here <https://www.exploit-db.com/exploits/41934>

## Attacks carried out

It is unclear how other attackers got a hold of this exploit, but in
January of 2017, attacks from all around began. The first known victims
were sent emails enticing them to click on a link to documents in
Russian about military issues in Russia and areas held by Russian-backed
rebels in eastern Ukraine, researchers said. Their computers were then
infected with eavesdropping software made by Gamma Group, a private
company that sells to agencies of many governments. Whilst the initial
attacks were small, it rapidly became dangerous, as a notorious piece of
financial hacking software known as Latenbot was being distributed using
the same Microsoft bug. It is unclear how many people were ultimately
infected or how much money was stolen.

## Sources

<https://www.reuters.com/article/us-microsoft-cyber-idUKKBN17S32G>

<https://www.cve.org/CVERecord?id=CVE-2017-0199>

<https://www.securitytracker.com/id/1038224>

<https://www.exploit-db.com>
