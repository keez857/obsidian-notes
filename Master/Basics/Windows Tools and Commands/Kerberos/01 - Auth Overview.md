![[VRr2B6w.png]]

1) `AS-REQ`
The client requests an Authentication Ticket or Ticket Granting Ticket (TGT).

2) `AS-REP`
The Key Distribution Center verifies the client and sends back an encrypted TGT.

3) `TGS-REQ`
The client sends the encrypted TGT to the Ticket Granting Server (TGS) with the Service Principal Name (SPN) of the service the client wants to access.

4) `TGS-REP` 
The Key Distribution Center (KDC) verifies the TGT of the user and that the user has access to the service, then sends a valid session key for the service to the client.

5) `AP-REQ` 
The client requests the service and sends the valid session key to prove the user has access.

6) `AP-REP`
The service grants access