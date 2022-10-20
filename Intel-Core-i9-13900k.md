# Intel's 13th generation Core, Raptor Lake

Today, October 20, 2022, marks the release of Intel's 13th generation Core processor series, codename Raptor Lake. Raptor Lake is essentially the second half of this fall's desktop CPU releases and the mid-cycle upgrade for Intel’s current LGA-1700 platform. Intel's 13th generation is designed to bring more performance to the same platform as the previous generation, Alder Lake on LGA-1700.

Intel isn't significantly tweaking their CPU architectures for Raptor Lake and is more of a refined version of Alder Lake. The P cores are based on what’s technically a new architecture, Raptor Cove, while the E cores are still based on the same Gracemont architecture on Alder Lake.


### Difference Compared to 12th Generation Alder Lake

Between the 12th Generation Alder Lake vs. the 13th Generation Raptor Lake we see higher clockspeeds and additional cache in the six SKUs across the Core i9, i7, and i5 product segments. The six SKUs are made of 3 tiers of chips, each with a segment that supports overclocking (K) and without integrated graphics (F). This gives us the six SKUs. 

Compared to the relevant 12th Gen Core SKUs, Intel has replaced the P cores with new Raptor Cove cores on a 1:1 basis. Meanwhile for the E cores, Intel has effectively doubled the number of E cores for each corresponding SKU.


**The 13th Generation Raptor Lake is improved over the 12th Generation Alder Lake:**
1. Higher clockspeeds, especially for the P cores
2. Additional E cores 
3. Additional L2 cache for both the P and E cores. 
4. L3 cache is also a bit larger to accommodate for the larger number of E cores.
e.g., the Core i5-13600K now has eight E-cores whereas the Core i5-12600K had four.
5. Increase in the power limit (PL2). 
Intel's Boost Core works so that the processor can increase the clock speeds until it hits a power limit called **PL2**. This means Intel has increased their power limit from 241W to 253W which gives the CPU more performance.

**Specifications for the Core i9-13900K vs i9-12900K**

|               | i9-13900K     |i9-12900K | 
| ------------- |:-------------:| :-------------:| 
| uArch         | Raptor Cove + Gracemont |Golden Cove + Gracemont
| Cores         |  8P + 16E (32 T)|8P + 8E (24T)|
|Base Freq (P)  |3300 |3200|
|Turbo Freq (P) |5800 |5200|
|TDP            |125 W |125 W| 
|PL2/PPT        |253 W |241 W|
|iGPU/Cores     |Xe-LP, 32|Xe-LP, 32|
|L3 Cache       |36 MB | 30 MB|
|DDR5           |2 x 5600| 2 x 4800|
|CPU PCIe       |5.0 x16 + 4.0 x4 | 5.0 x16 + 4.0 x4
|MSRP           |$589 |$589|


The flagship chip, the Core i9-13900K has a max P-Core turbo of 5.8 GHz which is an **increase of 600 MHz** over the Core i9-12900K. If we consider the difference between the 12th and 13th generation, it has double the amount of efficiency cores 24C/32T, larger L2 Cash - 2MB per P-Core, 4 MB per E-core cluster. There is 15% ST (single threaded) and 41% MT (multi-threaded) performance.

One thing to note about the efficiency cores is that Intel has **lowered the base frequency of these cores** to 2.2 GHz base, which is down from 2.4GHz on Alder Lake. But at the same time, however, they have also **increased the E-core max turbo clockspeed** to 4.3 GHz, 400Mhz higher than the 3.9 GHz cores on Alder Lake.

* Core i9-12900K =  8P and 16E / 32
* Core i7-13700K =  8P and 8E / 24 
* Core i5-13600K =  6P and 8E / 20 (4 more cores than the Alder Lake i5-12600K)

### Z790 Chipset & DDR5-5600 Support
The launch of the 13th Gen Core chips also comes with a new generation of motherboards from Intel: Z790. For those with the Z690, do not panic! :) The 13th Gen Core chips are backwards-compatible with 600 series boards with the necessary BIOS update. This motherboard has PCIe Gen 5.0 and 4.0 support and USB 3.2 Gen 2x2 - 20 Gbps.

### Perks of Z790:
* first boards validated for the higher DDR5-5600 memory speeds (whereas Alder Lake running at DDR5-4800)
* more I/O flexibility: Z790 has 20 PCIe 4 lanes, compared to 12 on Z690. However, there is 8 PCIe 3 lanes, which is 8 fewer than on Z690.
* one more USB 20Gbps (USB 3.2 Gen 2x2) making for a total of 5, which is one more lane more than the Z690 motherboard. 

Raptor Lake, in time, will be in integrated into the mobile parts with U, P, H, and HX series processors. We'll just have to wait to see! 🦖
