---
title: 'Rainbow Crackalack'
date: 2019-11-27T22:43:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-9YTEBMUFs_I/XcyrDfXeMRI/AAAAAAAAQ0Q/yOg8gFfn7bs1GaCJTRR6OlAqd4DVLVZsQCNcBGAsYHQ/s640/brute_force_rt_comparison.png)](https://1.bp.blogspot.com/-9YTEBMUFs_I/XcyrDfXeMRI/AAAAAAAAQ0Q/yOg8gFfn7bs1GaCJTRR6OlAqd4DVLVZsQCNcBGAsYHQ/s1600/brute_force_rt_comparison.png)

**Rainbow Crackalack - Rainbow Table Generation And Lookup Tools**

This project produces open-source code to generate[rainbow tables](https://www.kitploit.com/search/label/Rainbow%20Tables "rainbow tables")as well as use them to look up password hashes. While the current release only supports NTLM, future releases aim to support MD5, SHA-1, SHA-256, and possibly more. Both Linux and[Windows](https://www.kitploit.com/search/label/Windows "Windows")are supported!  
For more information, see the project website:[https://www.rainbowcrackalack.com/](https://www.rainbowcrackalack.com/ "https://www.rainbowcrackalack.com/")  
[

](https://www.blogger.com/u/1/null)  
**Volunteering**  
The project for generating NTLM 9-character tables is now underway! If you create 5 tables for us, your name will be listed on the[project website](https://www.rainbowcrackalack.com/ "project website")as a project supporter. If you create 200 tables, we will mail you a free magnetic hard drive containing NTLM 9-character tables with 50% efficiency. Ships world-wide!  
If you have modern GPU equipment and you'd like to contribute, please[reach out using this form](https://www.rainbowcrackalack.com/?showcontact=true "reach out using this form")to coordinate efforts.  
  
**NTLM Tables**  
Currently, NTLM 8-character tables are available for[free download via Bittorrent](https://www.rainbowcrackalack.com/rainbow_crackalack_ntlm_8.torrent "free download via Bittorrent"). For convenience, they[may also be purchased](https://www.rainbowcrackalack.com/#download "may also be purchased")on an SSD with a USB 3.0 external enclosure.  
  
**Examples**  
  
**Generating NTLM 9-character tables**  
The following command shows how to generate a standard 9-character NTLM table:  
```
# ./crackalack_gen ntlm ascii-32-95 9 9 0 803000 67108864 0
```The arguments are designed to be comparable to those of the original (and now closed-source) rainbow crack tools. In order, they mean:  

Argument

Meaning

ntlm

The hash algorithm to use. Currently only "ntlm" is supported.

ascii-32-95

The character set to use. This effectively means "all available characters on the US keyboard".

9

The minimum plaintext character length.

9

The maximum plaintext character length.

0

The reduction index. Not used under standard conditions.

803000

The chain length for a single rainbow chain.

67108864

The number of chains per table (= 64M)

0

The table part index. Keep all other args the same, and increment this field to generate a single set of tables.

  
**Table lookups against NTLM 8-character hashes**  
The following command shows how to look up a file of NTLM[hashes](https://www.kitploit.com/search/label/Hashes "hashes")(one per line) against the NTLM 8-character tables:  
```
# ./crackalack_lookup /export/ntlm8_tables/ /home/user/hashes.txt
```  
**Recommended Hardware**  
The NVIDIA GTX & RTX lines of GPU hardware has been well-tested with the Rainbow Crackalack software, and offer an excellent price/performance ratio. Specifically, the GTX 1660 Ti or RTX 2060 are the best choices for building a new[cracking](https://www.kitploit.com/search/label/Cracking "cracking")machine.[This document](https://docs.google.com/spreadsheets/d/1jigNGvt9SUur_SNH7QDEACapJbrdL_wKYtprM23IDpM/edit?usp=sharing "This document")contains the raw data that backs this recommendation.  
However, other modern equipment can work just fine, so you don't necessarily need to purchase something new. The NVIDIA GTX and AMD Vega product lines are still quite useful for cracking!  
  
**Change Log**  

*   v1.0: June 11, 2019: Initial revision.
*   v1.1: August 8, 2019: massive speed improvements (credit Steve Thomas), finalization of NTLM9 spec, bugfixes.

  
**Windows Build**  
A 64-bit Windows build can be achieved on an Ubuntu host machine by installing the following prerequisites:  
```
# apt install mingw-w64 opencl-headers
```Then starting the build with:  
```
# make clean; ./make_windows.sh
```  
Author: [Joe Testa](https://www.positronsecurity.com/company/ "Joe Testa") ([@therealjoetesta](https://twitter.com/therealjoetesta "@therealjoetesta"))  
  
  

**[Download Rainbowcrackalack](http://hopigrarn.com/3lmu "Download Rainbowcrackalack")**

**Regards**

**Kang Asu**