---
title: 'Security Bulletin: IBM ToolsCenter Dynamic System Analysis (DSA) Preboot is affected by multiple vulnerabilities.'
date: 2019-12-05T01:38:00+01:00
draft: false
---

CVEID:   CVE-2019-3863 DESCRIPTION:   A flaw was found in libssh2 before 1.8.1. A server could send a multiple keyboard interactive response messages whose total length are greater than unsigned char max characters. This value is used as an index to copy memory causing in an out of bounds memory write error.CVSS Base score: 7.5CVSS Temporal Score: See: https://ift.tt/2rb6B2j for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:H/I:H/A:H) CVEID:   CVE-2019-3862 DESCRIPTION:   An out of bounds read flaw was discovered in libssh2 before 1.8.1 in the way SSH\_MSG\_CHANNEL\_REQUEST packets with an exit status message and no payload are parsed. A remote attacker who compromises a SSH server may be able to cause a Denial of Service or read data in the client memory.CVSS Base score: 7.3CVSS Temporal Score: See: https://ift.tt/364OfyQ for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L) CVEID:   CVE-2019-3861 DESCRIPTION:   An out of bounds read flaw was discovered in libssh2 before 1.8.1 in the way SSH packets with a padding length value greater than the packet length are parsed. A remote attacker who compromises a SSH server may be able to cause a Denial of Service or read data in the client memory.CVSS Base score: 5CVSS Temporal Score: See: https://ift.tt/2rZCiLO for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:L/A:L) CVEID:   CVE-2019-3860 DESCRIPTION:   An out of bounds read flaw was discovered in libssh2 before 1.8.1 in the way SFTP packets with empty payloads are parsed. A remote attacker who compromises a SSH server may be able to cause a Denial of Service or read data in the client memory.CVSS Base score: 5CVSS Temporal Score: See: https://ift.tt/2Prq1bt for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:L/A:L) CVEID:   CVE-2019-3859 DESCRIPTION:   An out of bounds read flaw was discovered in libssh2 before 1.8.1 in the \_libssh2\_packet\_require and \_libssh2\_packet\_requirev functions. A remote attacker who compromises a SSH server may be able to cause a Denial of Service or read data in the client memory.CVSS Base score: 5CVSS Temporal Score: See: https://ift.tt/386biuJ for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:L/A:L) CVEID:   CVE-2019-3858 DESCRIPTION:   An out of bounds read flaw was discovered in libssh2 before 1.8.1 when a specially crafted SFTP packet is received from the server. A remote attacker who compromises a SSH server may be able to cause a Denial of Service or read data in the client memory.CVSS Base score: 5CVSS Temporal Score: See: https://ift.tt/38b75pY for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:L/A:L) CVEID:   CVE-2019-3857 DESCRIPTION:   An integer overflow flaw which could lead to an out of bounds write was discovered in libssh2 before 1.8.1 in the way SSH\_MSG\_CHANNEL\_REQUEST packets with an exit signal are parsed. A remote attacker who compromises a SSH server may be able to execute code on the client system when a user connects to the server.CVSS Base score: 7.5CVSS Temporal Score: See: https://ift.tt/2Yhvvti for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:H/I:H/A:H) CVEID:   CVE-2019-3856 DESCRIPTION:   An integer overflow flaw, which could lead to an out of bounds write, was discovered in libssh2 before 1.8.1 in the way keyboard prompt requests are parsed. A remote attacker who compromises a SSH server may be able to execute code on the client system when a user connects to the server.CVSS Base score: 7.5CVSS Temporal Score: See: https://ift.tt/34IsS6f for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:H/I:H/A:H) CVEID:   CVE-2019-3855 DESCRIPTION:   An integer overflow flaw which could lead to an out of bounds write was discovered in libssh2 before 1.8.1 in the way packets are read from the server. A remote attacker who compromises a SSH server may be able to execute code on the client system when a user connects to the server.CVSS Base score: 7.5CVSS Temporal Score: See: https://ift.tt/2xmHzMV for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:H/I:H/A:H) CVEID:   CVE-2017-9763 DESCRIPTION:   The grub\_ext2\_read\_block function in fs/ext2.c in GNU GRUB before 2013-11-12, as used in shlr/grub/fs/ext2.c in radare2 1.5.0, allows remote attackers to cause a denial of service (excessive stack use and application crash) via a crafted binary file, related to use of a variable-size stack array.CVSS Base score: 3.3CVSS Temporal Score: See: https://ift.tt/36761l8 for the current score.CVSS Vector: (CVSS:3.0/AV:L/AC:L/PR:N/UI:R/S:U/C:N/I:N/A:L) CVEID:   CVE-2017-5357 DESCRIPTION:   regex.c in GNU ed before 1.14.1 allows attackers to cause a denial of service (crash) via a malformed command, which triggers an invalid free.CVSS Base score: 7.5CVSS Temporal Score: See: https://ift.tt/2LnDnEh for the current score.CVSS Vector: (CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:H) CVEID:   CVE-2018-18384 DESCRIPTION:   Info-ZIP UnZip 6.0 has a buffer overflow in list.c, when a ZIP archive has a crafted relationship between the compressed-size value and the uncompressed-size value, because a buffer size is 10 and is supposed to be 12.CVSS Base score: 7.8CVSS Temporal Score: See: https://ift.tt/2YrUIBr for the current score.CVSS Vector: (CVSS:3.0/AV:L/AC:L/PR:N/UI:R/S:U/C:H/I:H/A:H) CVEID:   CVE-2018-14404 DESCRIPTION:   A NULL pointer dereference vulnerability exists in the xpath.c:xmlXPathCompOpEval() function of libxml2 through 2.9.8 when parsing an invalid XPath expression in the XPATH\_OP\_AND or XPATH\_OP\_OR case. Applications processing untrusted XSL format inputs with the use of the libxml2 library may be vulnerable to a denial of service attack due to a crash of the application.CVSS Base score: 3.3CVSS Temporal Score: See: https://ift.tt/2OTjyXL for the current score.CVSS Vector: (CVSS:3.0/AV:L/AC:L/PR:N/UI:R/S:U/C:N/I:N/A:L) CVEID:   CVE-2016-9318 DESCRIPTION:   libxml2 2.9.4 and earlier, as used in XMLSec 1.2.23 and earlier and other products, does not offer a flag directly indicating that the current document may be read but other files may not be opened, which makes it easier for remote attackers to conduct XML External Entity (XXE) attacks via a crafted document.CVSS Base score: 5.5CVSS Temporal Score: See: https://ift.tt/2rlLd8L for the current score.CVSS Vector: (CVSS:3.0/AV:L/AC:L/PR:N/UI:R/S:U/C:H/I:N/A:N) CVEID:   CVE-2019-6128 DESCRIPTION:   The TIFFFdOpen function in tif\_unix.c in LibTIFF 4.0.10 has a memory leak, as demonstrated by pal2rgb.CVSS Base score: 3.3CVSS Temporal Score: See: https://ift.tt/2OSkX0G for the current score.CVSS Vector: (CVSS:3.0/AV:L/AC:L/PR:N/UI:R/S:U/C:N/I:N/A:L) CVEID:   CVE-2016-5102 DESCRIPTION:   Buffer overflow in the readgifimage function in gif2tiff.c in the gif2tiff tool in LibTIFF 4.0.6 allows remote attackers to cause a denial of service (segmentation fault) via a crafted gif file.CVSS Base score: 5.5CVSS Temporal Score: See: https://ift.tt/34OW37u for the current score.CVSS Vector: (CVSS:3.0/AV:L/AC:L/PR:N/UI:R/S:U/C:N/I:N/A:H) [...read more](https://www.ibm.com/blogs/psirt/security-bulletin-ibm-toolscenter-dynamic-system-analysis-dsa-preboot-is-affected-by-multiple-vulnerabilities/)

  
  
from IBM Product Security Incident Response Team https://ift.tt/2DN7sZI