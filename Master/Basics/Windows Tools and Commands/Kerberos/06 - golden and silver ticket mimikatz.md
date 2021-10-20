### gold vs silver tickets

**Silver Tickets**
more discreet, limited to service that is targeted

**Golden Tickets**
access to any Kerberos service

---

### krbtgt vs TGT

**KRBTGT** - service account for KDC. if you impersonate this account and create golden ticket, you can then create service ticket for anything.

**TGT** - ticket to service account issued by KDC. Can only access that service the TGT  is from. For example a SQLservice ticket.


---

### the attack

works by dumping the TGT of any user (preferably domain admin)

you generally want a golden ticket for krbtgt or
silver ticket for a particular service or domain admin

With a valid SID and NTLM hash you can craft a golden ticket

---

