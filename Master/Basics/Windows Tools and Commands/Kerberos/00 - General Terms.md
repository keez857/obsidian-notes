### Kerberos
Replaced NTLM, considered more secure

---

`TGT - Ticket Granting Ticket`
A ticket-granting ticket is an authentication ticket used to request service tickets from the TGS for specific resources from the domain.

`KDC - Key Distribution Center`
 The Key Distribution Center is a service for issuing TGTs and service tickets that consist of the Authentication Service and the Ticket Granting Service.

`AS - Authentication Service `
The Authentication Service issues TGTs to be used by the TGS in the domain to request access to other machines and service tickets.

`TGS - Ticket Granting Service`
The Ticket Granting Service takes the TGT and returns a ticket to a machine on the domain.  
    
`SPN - Service Principal Name`
A Service Principal Name is an identifier given to a service instance to associate a service instance with a domain service account. Windows requires that services have a domain service account which is why a service needs an SPN set.

`KDC LT Key - KDC Long Term Secret Key`
The KDC key is based on the KRBTGT service account. It is used to encrypt the TGT and sign the PAC.

`Client LT Key - Client Long Term Secret Key`
The client key is based on the computer or service account. It is used to check the encrypted timestamp and encrypt the session key.

`Service LT Key - Service Long Term Secret Key`
The service key is based on the service account. It is used to encrypt the service portion of the service ticket and sign the PAC.

`Session Key`
Issued by the KDC when a TGT is issued. The user will provide the session key to the KDC along with the TGT when requesting a service ticket.

`PAC - Privilege Attribute Certificate`
The PAC holds all of the user's relevant information, it is sent along with the TGT to the KDC to be signed by the Target LT Key and the KDC LT Key in order to validate the user.