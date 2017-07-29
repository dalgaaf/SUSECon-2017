<!-- .slide: data-state="section-break" id="section-break-7" data-timing="10s" -->
# Status and Next Steps


<!-- .slide: data-state="normal" id="status-0" data-timing="20s" data-menu-title="Status" -->
## Status

### Dovecot Ceph Plugin
* Open sourced
  * github
* still under development
* still includes librmb
  * planned: move to Ceph project


<!-- .slide: data-state="normal" id="status-1" data-timing="20s" data-menu-title="Testing" -->
## Testing

### Functional testing
* Setup small 5-node cluster 
* SLES12-SP3 GMC 
* SES5 Beta
* Run Dovecot functional tests against Ceph


<!-- .slide: data-state="normal" id="status-2" data-timing="20s" data-menu-title="PoC" -->
## Proof-of-Concept

### Hardware
* 9 SSD nodes for CephFS
* 12 HDD nodes
* 3 MDS / 3 MON

### 2 FCs + 1 vFC

### Testing
* run load tests
* run failure scenarios against Ceph
* improve and tune Ceph setup
* verify and optimize hardware


<!-- .slide: data-state="normal" id="status-3" data-timing="20s" data-menu-title="Further Development" -->
## Further Development

### Goal: Pure RADOS backend, store metadata/index in Ceph omap

<div>
     <img style="height: 70%; left: 5%; position: absolute" alt="librmb architecture overview"
          data-src="images/dovecot-plugin-architecture-pure-rados.svg" />
</div>



<!-- .slide: data-state="normal" id="status-4" data-timing="20s" data-menu-title="Next Steps" -->
## Next Steps

### Production
* verify if all requirements are fulfilled
* integrate in production
* migrate users step-by-step
* extend to final size
  * 128 HDD nodes, 1200 OSDs, 4,7 PiB
  * 15 SSD nodes, 120 OSDs, 175 TiB
