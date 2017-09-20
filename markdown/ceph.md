<!-- .slide: data-state="section-break" id="section-break-3" data-timing="10s" -->
# Ceph


<!-- .slide: data-state="normal" id="ceph-overview" data-timing="20s" data-menu-title="Ceph Components" -->
<center><img src="images/ceph-stack.svg" style="width:85%"></center>

NOTE: well known picture, short info on components


<!-- .slide: data-state="normal" id="motivation-goals" data-timing="20s" data-menu-title="Goals" -->
## Motivation

* scale-out vs scale-up <!-- .element class="fragment" -->
* fast self healing <!-- .element class="fragment" -->
* commodity hardware <!-- .element class="fragment" -->
* prevent vendor lock-in <!-- .element class="fragment" -->
* open source where feasible <!-- .element class="fragment" -->
* reduce Total Cost of Ownership (TCO) <!-- .element class="fragment" -->


<!-- .slide: data-state="normal" id="ceph-store-emails-1" data-timing="20s" data-menu-title="Ceph: Options" -->
## Ceph Options

### Filesystem <!-- .element class="fragment" data-fragment-index="1"-->
  * CephFS <!-- .element class="fragment" data-fragment-index="1"-->
  * NFS Gateway via RGW <!-- .element class="fragment" data-fragment-index="1"-->
  * any filesystem on RBD <!-- .element class="fragment" data-fragment-index="1"-->

### Objectstore <!-- .element class="fragment" data-fragment-index="2"-->
  * S3/Swift via RGW <!-- .element class="fragment" data-fragment-index="2"-->
  * RADOS <!-- .element class="fragment" data-fragment-index="2"-->


<!-- .slide: data-state="normal" id="ceph-store-emails-2" data-timing="20s" data-menu-title="Ceph: Option CephFS" -->
## Where to store in Ceph?

<div>
    <img style="width: 35%; left: 60%; position: absolute" alt="CephFS"
         data-src="images/cephfs.svg" />
</div>

### CephFS

* same issues as NFS <!-- .element class="fragment" -->
* mail storage on POSIX layer adds complexity <!-- .element class="fragment" -->
* no option for emails <!-- .element class="fragment" -->
* usable for metadata/caches/indexes <!-- .element class="fragment" -->
<br>
<br>

#### <b>Security</b> <!-- .element class="fragment" -->
* requires direct access to storage network <!-- .element class="fragment" -->
* only for dedicated platform <!-- .element class="fragment" -->


<!-- .slide: data-state="normal" id="ceph-store-emails-3" data-timing="20s" data-menu-title="Ceph: Option RBD" -->
## Where to store in Ceph?

<div>
    <img style="width: 35%; left: 60%; position: absolute" alt="RBD"
         data-src="images/rbd.svg" />
</div>

### RBD

* requires sharding and large RBDs <!-- .element class="fragment" -->
* requires RBD/fs extend scenarios <!-- .element class="fragment" -->
* regular account migration<!-- .element class="fragment" -->
* no sharing between clients <!-- .element class="fragment" -->
* impracticable <!-- .element class="fragment" -->
<br>
<br>

#### <b>Security</b> <!-- .element class="fragment" -->
* no direct access to storage network required <!-- .element class="fragment" -->
* secure through hypervisor abstraction (libvirt) <!-- .element class="fragment" -->


<!-- .slide: data-state="normal" id="ceph-store-emails-4" data-timing="20s" data-menu-title="Ceph: Option RadosGW" -->
## Where to store in Ceph?

<div>
    <img style="width: 35%; left: 60%; position: absolute" alt="RGW"
         data-src="images/rgw.svg" />
</div>

### RadosGW
* can store emails as objects <!-- .element class="fragment" -->
* extra network hops <!-- .element class="fragment" -->
* potential bottleneck <!-- .element class="fragment" -->
* very likely not fast enough <!-- .element class="fragment" -->
<br>
<br>

#### <b>Security</b> <!-- .element class="fragment" -->
* no direct access to Ceph storage network required <!-- .element class="fragment" -->
* connection to RadosGW can be secured (WAF) <!-- .element class="fragment" -->


<!-- .slide: data-state="normal" id="ceph-store-emails-5" data-timing="20s" data-menu-title="Ceph: Option librados" -->
## Where to store in Ceph?

<div>
    <img style="width: 35%; left: 60%; position: absolute" alt="librados"
         data-src="images/librados.svg" />
</div>

### Librados
* direct access to RADOS <!-- .element class="fragment" -->
* parallel I/O <!-- .element class="fragment" -->
* not optimized for emails <!-- .element class="fragment" -->
* how to handle metadata/caches/indexes? <!-- .element class="fragment" -->
<br>
<br>

#### <b>Security</b> <!-- .element class="fragment" -->
* requires direct access to storage network <!-- .element class="fragment" -->
* only for dedicated platform <!-- .element class="fragment" -->
