<!-- .slide: data-state="section-break" id="section-break-3" data-timing="10s" -->
# Ceph


<!-- .slide: data-state="normal" id="ceph-overview" data-timing="20s" data-menu-title="Ceph Components" -->
<center><img src="images/ceph-stack.svg" style="width:85%"></center>

NOTE: well known picture, short info on components


<!-- .slide: data-state="normal" id="motivation-goals" data-timing="20s" data-menu-title="Goals" -->
## Motivation

* Scale-out vs Scale-up
* Fast self healing
* Commodity hardware
* Prevent vendor lock-in
* Open Source where feasible
* Reduce Total Cost of Ownership (TCO)


<!-- .slide: data-state="normal" id="ceph-store-emails-1" data-timing="20s" data-menu-title="Ceph: Options" -->
## Ceph Options

### Filesystem
  * CephFS
  * NFS Gateway via RGW
  * Any filesystem on RBD

### Objectstore
  * S3/Swift via RGW
  * RADOS


<!-- .slide: data-state="normal" id="ceph-store-emails-2" data-timing="20s" data-menu-title="Ceph: Option CephFS" -->
## Where to store in Ceph?

<div>
    <img style="width: 35%; left: 60%; position: absolute" alt="CephFS"
         data-src="images/cephfs.svg" />
</div>

### CephFS

* same issues as NFS
* mail storage on POSIX layer adds complexity
* no option for emails
* usable for metadata/caches/indexes


<!-- .slide: data-state="normal" id="ceph-store-emails-3" data-timing="20s" data-menu-title="Ceph: Option RBD" -->
## Where to store in Ceph?

<div>
    <img style="width: 35%; left: 60%; position: absolute" alt="RBD"
         data-src="images/rbd.svg" />
</div>

### RBD

* needs sharding and large RBDs
* needs account migration
* needs RBD/fs extend scenarios
* no sharing between clients
* impracticable


<!-- .slide: data-state="normal" id="ceph-store-emails-4" data-timing="20s" data-menu-title="Ceph: Option RadosGW" -->
## Where to store in Ceph?

<div>
    <img style="width: 35%; left: 60%; position: absolute" alt="RGW"
         data-src="images/rgw.svg" />
</div>

### RadosGW
* can store emails as objects
* extra network hops
* potential bottleneck
* very likely not fast enough


<!-- .slide: data-state="normal" id="ceph-store-emails-5" data-timing="20s" data-menu-title="Ceph: Option librados" -->
## Where to store in Ceph?

<div>
    <img style="width: 35%; left: 60%; position: absolute" alt="librados"
         data-src="images/librados.svg" />
</div>

### Librados
* direct access to RADOS
* parallel I/O
* not optimized for emails
* how to handle metadata/caches/indexes?

