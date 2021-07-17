---
title: 'Empirical Comparison of DOS Kernels (2015)'
date: 2019-12-30T07:55:00+01:00
draft: false
---

  
  
from Hacker News https://ift.tt/2kmqyzK

```
 Conventional Memory Detail: Segment Total Name Type ------- ---------------- ------------ ------------- 0000 1,024 (1K) interrupt vector table 0040 768 (1K) BIOS data area 0070 6,544 (6K) IO system data NUL system device driver CON system device driver AUX system device driver PRN system device driver CLOCK$ system device driver A: - C: system device driver COM1 system device driver LPT1 system device driver LPT2 system device driver LPT3 system device driver CONFIG$ system device driver COM2 system device driver COM3 system device driver COM4 system device driver 0209 2,128 (2K) DOS system data 020b 1,024 (1K) EBDA data area 024c 544 (1K) SECTORBUF data area 026f 512 (1K) BUFFERS BUFFERS=30,0 028f 64 (0K) DOS system code 0294 80 (0K) COMMAND data area 029a 240 (0K) MEM environment 02aa 55,248 (54K) MEM program 1028 589,152 (575K) free Upper Memory Detail: Segment Total Name Type ------- ---------------- ------------ ------------- a000 199,280 (195K) reserved d0a7 23,424 (23K) DOS system data d0a9 912 (1K) UIDE device driver UDVD1 installed DEVICE=UIDE d0e3 464 (0K) DRIVEDATA data area d101 2,080 (2K) FILES FILES=40 (35 in this block) d184 256 (0K) FCBS data area d195 16,080 (16K) BUFFERS BUFFERS=30,0 d583 448 (0K) LASTDRV LASTDRIVE=E d5a0 3,072 (3K) STACKS STACKS=9,256 d660 5,712 (6K) COMMAND program d7c6 64 (0K) free d7cb 3,088 (3K) COMMAND environment d88d 192 (0K) free d89a 912 (1K) FDAPM program d8d4 6,208 (6K) SHSUCDX program da59 11,648 (11K) DOSLFNMS program dd32 752 (1K) RDISK program E: installed DEVICE=RDISK dd62 3,088 (3K) CTMOUSE program de24 7,600 (7K) free Memory Type Total Used Free ---------------- -------- -------- -------- Conventional 640K 11K 629K Upper 61K 53K 8K Reserved 323K 323K 0K Extended (XMS) 3,467,520K 2,097,941K 1,369,579K ---------------- -------- -------- -------- Total memory 3,468,544K 2,098,328K 1,370,216K Total under 1 MB 701K 64K 637K Memory accessible using Int 15h 0K ( 0 bytes) Largest executable program size 629K (644,416 bytes) Largest free upper memory block 7K ( 7,616 bytes) Available space in High Memory Area 6K ( 6,128 bytes) Windows is resident in the high memory area. 
```

```
 Conventional Memory Detail: Segment Total Name Type ------- ---------------- ------------ ------------- 0000 1,024 (1K) interrupt vector table 0040 768 (1K) BIOS data area 0070 10,512 (10K) IO system data NUL system device driver CON system device driver AUX system device driver PRN system device driver CLOCK$ system device driver A: - C: system device driver COM1 system device driver LPT1 system device driver LPT2 system device driver LPT3 system device driver COM2 system device driver COM3 system device driver COM4 system device driver XMSXXXX0 system device driver 0301 2,416 (2K) DOS system data 0303 1,136 (1K) MOVEXBDA device driver MOVXBDA# installed DEVICE=MOVEXBDA 034b 160 (0K) UMBPCI device driver UMBPCIXX installed DEVICE=UMBPCI 0356 544 (1K) SECTORBUF data area 0379 512 (1K) BUFFERS BUFFERS=30,0 0399 64 (0K) DOS system code 039e 80 (0K) COMMAND data area 03a4 256 (0K) MEM environment 03b5 55,248 (54K) MEM program 1133 584,880 (571K) free Upper Memory Detail: Segment Total Name Type ------- ---------------- ------------ ------------- a000 196,608 (192K) reserved d000 23,424 (23K) DOS system data d002 912 (1K) UIDE device driver UDVD1 installed DEVICE=UIDE d03c 464 (0K) DRIVEDATA data area d05a 2,080 (2K) FILES FILES=40 (35 in this block) d0dd 256 (0K) FCBS data area d0ee 16,080 (16K) BUFFERS BUFFERS=30,0 d4dc 448 (0K) LASTDRV LASTDRIVE=E d4f9 3,072 (3K) STACKS STACKS=9,256 d5b9 5,584 (5K) COMMAND program d717 64 (0K) free d71c 3,088 (3K) COMMAND environment d7de 192 (0K) free d7eb 912 (1K) FDAPM program d825 208 (0K) free d833 6,208 (6K) SHSUCDX program d9b8 11,648 (11K) DOSLFNMS program dc91 752 (1K) RDISK program E: installed DEVICE=RDISK dcc1 3,088 (3K) CTMOUSE program dd83 10,176 (10K) free Memory Type Total Used Free ---------------- -------- -------- -------- Conventional 640K 15K 625K Upper 64K 54K 10K Reserved 320K 320K 0K Extended (XMS) 3,467,520K 2,097,941K 1,369,579K ---------------- -------- -------- -------- Total memory 3,468,544K 2,098,330K 1,370,214K Total under 1 MB 704K 69K 635K Memory accessible using Int 15h 0K ( 0 bytes) Largest executable program size 625K (640,144 bytes) Largest free upper memory block 10K ( 10,192 bytes) Available space in High Memory Area 5K ( 5,232 bytes) Windows is resident in the high memory area. 
```

```
 Conventional Memory Detail: Segment Total Name Type ------- ---------------- ------------ ------------- 0000 1,024 (1K) interrupt vector table 0040 768 (1K) BIOS data area 0070 8,400 (8K) IO system data NUL system device driver CON system device driver PRN system device driver AUX system device driver LPT1 system device driver LPT2 system device driver LPT3 system device driver COM1 system device driver COM2 system device driver COM3 system device driver COM4 system device driver CLOCK$ system device driver A: - C: system device driver 027d 1,248 (1K) DOS system data 027f 192 (0K) FILES FILES=40 (3 in this block) 028c 1,024 (1K) EBDA data area 02cc 3,008 (3K) COMMAND program 0389 272 (0K) MEM environment 039b 55,248 (54K) MEM program 1119 585,296 (572K) free Upper Memory Detail: Segment Total Name Type ------- ---------------- ------------ ------------- a000 199,280 (195K) reserved d0a7 9,344 (9K) DOS system data d0a9 4,624 (5K) UIDE device driver UDVD1 installed DEVICE=UIDE d1cb 1,904 (2K) FILES FILES=40 (32 in this block) d243 448 (0K) LASTDRV LASTDRIVE=E d260 2,304 (2K) STACKS data area d2f0 2,048 (2K) COMMAND environment d371 192 (0K) free d37e 6,208 (6K) SHSUCDX program d503 11,648 (11K) DOSLFNMS program d7dc 752 (1K) RDISK program E: installed DEVICE=RDISK d80c 3,088 (3K) CTMOUSE program d8ce 29,456 (29K) free Memory Type Total Used Free ---------------- -------- -------- -------- Conventional 640K 14K 626K Upper 61K 32K 29K Reserved 323K 323K 0K Extended (XMS) 3,467,520K 2,098,041K 1,369,479K ---------------- -------- -------- -------- Total memory 3,468,544K 2,098,410K 1,370,134K Total under 1 MB 701K 46K 655K Memory accessible using Int 15h 0K ( 0 bytes) Largest executable program size 626K (640,560 bytes) Largest free upper memory block 29K ( 29,472 bytes) Available space in High Memory Area 10K ( 9,927 bytes) FreeDOS is resident in the high memory area. 
```