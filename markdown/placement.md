<!-- .slide: data-state="section-break" id="section-break-6" data-timing="10s" -->
# Placement


<!-- .slide: data-state="normal" id="placement-1" data-timing="20s" data-menu-title="Placement issues" -->
## Issues

### Datacenter
* usually two independent fire compartments (FCs)
* may additional virtual FCs

### Requirements
* Lost of customer data MUST be prevented
* Any server, switch or rack can fail
* One FC can fail
* Data replication at least 3 times (or equivalent)


<!-- .slide: data-state="normal" id="placement-2" data-timing="20s" data-menu-title="Placement issues" -->
## Issues

### Questions
* How to place 3 copies in two FCs?
* How independent and reliable are the virtual FCs?
* Network architecture?
* Network bandwidth?


<!-- .slide: data-state="normal" id="placement-3" data-timing="20s" data-menu-title="3FCs" -->
<div>
  <center><img data-src="images/fc-ceph-EC+3xReplication-color.svg" style="width:85%"></center>
</div>


<!-- .slide: data-state="normal" id="placement-net-1" data-timing="20s" data-menu-title="Network" -->
## Network

### 10G network
* 2 NICs / 4 ports per node
* SFP+ DAC

### Multi-chassis Link Aggregation (MC-LAG/M-LAG)
* For aggregation and fail-over

### Spine-Leaf architecture
* Interconnect must not reflect theoretical rack/FC bandwidth
* L2: terminated in rack
* L3: TOR <-> spine / spine <-> spine
* Border Gateway Protocol (BGP)


<!-- .slide: data-state="normal" id="placement-net-2" data-timing="20s" data-menu-title="Network Overview" -->
<div>
  <center><img data-src="images/network-arch.svg" style="width:80%"></center>
</div>
