---
id: 2013-003
title: Brute force DES attack permits compromise of AFS cell
issued: 24-Jul-2013
updated: 24-Jul-2013
severity: High
affected: OpenAFS servers before versions 1.4.15 and 1.6.5
---

The small size of the DES key space permits an attacker to brute force a
cell's service key and then forge traffic from any user within the cell.
The key space search can be performed in under 1 day at a cost of around
\$100 using publicly available services.

Instructions:

* [How to rekey your cell](/security/how-to-rekey.txt)
* [How to install rxkad k5 support for servers running OpenAFS 1.6](/security/install-rxkad-k5-1.6.txt)
* [How to install rxkad k5 support for servers running OpenAFS 1.4](/security/install-rxkad-k5-1.4.txt)


