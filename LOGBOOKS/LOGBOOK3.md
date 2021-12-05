# Descrição

-   The CVE-2017-0199 is an exploit that allows remote execution of code
    on the target, via a specially crafted RTF document.
-   It abuses the Object Linking and Embedding (OLE) API.
-   Known vulnerable platforms are: Microsoft Office (2007, 2010, 2013,
    2016), Microsoft Windows (Vista, 7, 8.1, Server 2008)

# Catalogação

-   The exploit was discovered in July of 2016 when Ryan Hanson found a
    weakness in the way that Microsoft Word processes documents from
    another format.
-   In October of 2016, he reported it to Microsoft, expecting to
    receive a so called bug-bounty.
-   Integrity Impact: Complete (There is a total compromise of system
    integrity)
-   Access Complexity: Medium (The access conditions are somewhat
    specialized. Some conditions must be met to exploit)

# Exploit

-   There are several exploits available on <https://www.exploit-db.com>
-   Including one already automated as a payload on the Metasploit
    framework (source: <https://www.exploit-db.com/exploits/41934>).

# Ataques

-   The first victims were sent emails enticing them to click a link to
    documents that infected them with eavesdropping software.
-   A notorious piece of financial hacking software known as Latenbot
    was being distributed using the same Microsoft bug.
-   By April 9 2017, a program to exploit the flaw was on sale on
    underground markets for criminal hackers.
-   It was used to send documents booby-trapped with Dridex
    banking-fraud software to millions of computers in Australia.
