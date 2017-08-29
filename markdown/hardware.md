<!-- .slide: data-state="section-break" id="section-break-5" data-timing="10s" -->
# Hardware


<!-- .slide: data-state="normal" id="hardware-0" data-timing="20s" data-menu-title="Hardware" -->
## Hardware

<div>
     <img style="height: 20%; left: 65%; position: absolute" alt="librmb architecture overview"
          data-src="images/HPE-DL380Gen9.jpg" />
</div>

### Commodity x86_64 server
* HPE ProLiant DL380 Gen9
* Dual socket
  * Intel® Xeon® E5 V4
* 2x Intel® X710-DA2 Dual-port 10G
* 2x boot SSDs, SATA, HBA, no separate RAID controller

<br>
### CephFS, Rados, MDS and MON nodes


<!-- .slide: data-state="normal" id="hardware-1" data-timing="20s" data-menu-title="Storage nodes" -->
## Storage Nodes

### CephFS SSD Nodes
* <b>CPU:</b> E5-2643v4 @ 3.4 GHz, 6 Cores, turbo 3.7GHz
* <b>RAM:</b> 256 GByte, DDR4, ECC
* <b>SSD:</b> 8x 1.6 TB SSD, 25 DWPD, SAS, RR/RW 103k/69k iops

### Rados HDD Nodes
* <b>CPU:</b> E5-2640v4 @ 2.4 GHz, 10 Cores, turbo 3.4GHz
* <b>RAM:</b> 128 GByte, DDR4, ECC
* <b>SSD:</b> 2x 400 GByte, 3 DWPD, SAS, RR/RW 108k/49k iops
  * for BlueStore database etc.
* <b>HDD:</b> 10x 4 TByte, 7.2K, 128 MB cache, SAS


<!-- .slide: data-state="normal" id="hardware-2" data-timing="20s" data-menu-title="Compute nodes" -->
## Compute Nodes

### MDS
* <b>CPU:</b> E5-2643v4 @ 3.4 GHz, 6 Cores, turbo 3.7GHz
* <b>RAM:</b> 256 GByte, DDR4, ECC

<br>
### MON / SUSE admin
* <b>CPU:</b> E5-2640v4 @ 2.4 GHz, 10 Cores, turbo 3.4GHz
* <b>RAM:</b> 64 GByte, DDR4, ECC


<!-- .slide: data-state="normal" id="hardware-3" data-timing="20s" data-menu-title="Hardware specs" -->
## Why this specific HW?

### Community recommendations?
* OSD: 1x 64-bit AMD-64, 1GB RAM/1TB of storage, 2x 1GBit NICs
* MDS: 1x 64-bit AMD-64 quad-core, 1 GB RAM minimum per MDS, 2x 1GBit NICs

### NUMA, high clocked CPUs and large RAM overkill?
* Vendor did not offer single CPU nodes for number of drives
* MDS performance is mostly CPU clock bound and partly single threaded
  * High clocked CPUs for fast single threaded performance
* Large RAM: better caching!

