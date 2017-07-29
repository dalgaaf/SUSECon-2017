<!-- .slide: data-state="section-break" id="section-break-4" data-timing="10s" -->
# Dovecot and Ceph


<!-- .slide: data-state="normal" id="librmb-dovecot" data-timing="20s" data-menu-title="Dovecot" -->
## Dovecot

<div>
    <img style="height: 25%; left: 60%; position: absolute" alt="CephFS"
         data-src="images/dovecot_logo.svg" />
</div>

### Open source project (LGPL 2.1, MIT)

### 72% market share (openemailsurvey.org, 02/2017)

### Objectstore plugin available (obox)
* supports only REST APIs like S3/Swift
* not open source
* requires Dovecot Pro
* large impact on TCO


<!-- .slide: data-state="normal" id="dovecot-obox" data-timing="20s" data-menu-title="librmb" -->
## Dovecot Pro obox Plugin

<div>
     <img style="height: 75%; left: 15%; position: absolute" alt="obox architecture overview"
          data-src="images/dovecot-obox-plugin-architecture-normal.svg" />
</div>


<!-- .slide: data-state="normal" id="librmb-DT" data-timing="20s" data-menu-title="DT's approach" -->
## DT's approach
<div>
     <img style="height: 60%; left: 60%; position: absolute" alt="Partner"
          data-src="images/partner.png" />
</div>

* no open source solution on the market
* closed source is no option
* develop / sponsor a solution
* open source it
* partner with `Tallence AG` for development
* partner with `SUSE` for Ceph


<!-- .slide: data-state="normal" id="librmb-DT-1" data-timing="20s" data-menu-title="Ceph Dovecot Plugin" -->
## Ceph plugin for Dovecot
<div>
     <img style="height: 70%; left: 60%; position: absolute" alt="Ceph Plugin basics"
          data-src="images/dovecot-plugin-simple.svg" />
</div>

### First Step: hybrid approach

### Emails
* Store in RADOS Cluster

### Metadata and indexes
* Store in CephFS

### Be as generic as possible
* Split out code into libraries
* Integrate into corresponding upstream projects


<!-- .slide: data-state="normal" id="librmb-DT-2.0" data-timing="20s" data-menu-title="librmb" -->
## Librados mailbox (librmb)

### Generic email abstraction on top of librados

### Out of scope:
* User data and credential storage
  * target are huge installations where usually are already solutions in place

* Full text indexes
  * There are solutions already available and working outside email storage


<!-- .slide: data-state="normal" id="librmb-DT-2.1" data-timing="20s" data-menu-title="librmb" -->
## Librados mailbox (librmb)

<div>
     <img style="height: 75%; left: 8%; position: absolute" alt="librmb architecture overview"
          data-src="images/dovecot-plugin-architecture-normal.svg" />
</div>


<!-- .slide: data-state="normal" id="librmb-DT-2.2" data-timing="20s" data-menu-title="librmb - Mail Object Format" -->
## librmb - Mail Object Format

### Mails are immutable regarding the RFC-5322 content

### RFC-5322 content stored in RADOS directly

### Immutable attributes used by Dovecot stored in RADOS xattr
* rbox format version
* GUID
* Received date
* Save date
* POP3 UIDL
* POP3 order

### writable attributes are stored in Dovecot index files


<!-- .slide: data-state="normal" id="librmb-DT-2.3" data-timing="20s" data-menu-title="rados-dict" -->
## RADOS Dictionary Plugin

### make use of Ceph omap key/value store
### RADOS namespaces
 * `shared/<key>`
 * `priv/<key>`

### used by Dovecot to store metadata, quota, ...


<!-- .slide: data-state="normal" id="librmb-DT-3" data-timing="20s" data-menu-title="librmb" -->
## It's open source!

### License:
* ### `LGPLv2.1`

### Language:
* ### `C++`

### Location: 
* ### <a href="https://github.com/ceph-dovecot/">github.com/ceph-dovecot/</a>


<!-- .slide: data-state="normal" id="ceph-requirements" data-timing="20s" data-menu-title="Ceph requirements" -->
## Ceph Requirements

### Performance
* Write performance for emails is critical
* metadata/index read/write performance

### Cost
* Erasure Coding (EC) for emails
* Replication for CephFS

### Reliability
* MUST survice failure of disk, server, rack and even fire compartments


<!-- .slide: data-state="normal" id="ceph-version" data-timing="20s" data-menu-title="Ceph version" -->
## Which Ceph Release?

<div>
     <img style="height: 55%; left: 50%; position: absolute" alt="ceph luminous"
          data-src="images/ceph-luminous.png" />
</div>

### Required Features
* Bluestore
  * should be at least 2x faster than filestore
* CephFS
  * Stable release
  * Multi-MDS
* Erasure coding


<!-- .slide: data-state="normal" id="ceph-suse" data-timing="20s" data-menu-title="SUSE Products" -->
## SUSE Products to use

### SLES 12-SP3 and SES 5
<div>
     <img style="height: 80%; left: 15%; position: absolute" alt="ceph luminous"
          data-src="images/SUSE_Products.png" />
</div>
