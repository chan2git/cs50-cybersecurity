# Lecture 2: Securing Systems
The below notes are based on HarvardX's CS50 - Introduction to Cybersecurity, Lecture 2: Securing Systems You can watch at: https://www.youtube.com/watch?v=9phdZjF8qOk


### HTTP
Hypertext Transfer Protocol. A protocol or conventions that dictate how devices can remotely communicate with a remote server. HTTP is not encrypted, therefore it is susceptible to machine in the middle attacks. Further, the attacker in the middle could also inject additional code into the data that is being sent to the recipients


### Packet Sniffing
When an attacker views or altars the packets of data that is traveling between parties. 

Example of packets

Searching for cats
```
GET /search?q=cats HTTP/3
Host: example.com
```

Checking out with credit card number
```
POST /checkout HTTP/3
Host: example.com

number=4242424242424242
```

In the above examples, an attacker could sniff the packets and deduce that the user is searching for a specific query or is passing along credit card information for a purchase.

Attackers could be on the same Wi-Fi network as the victim, or be within approximate location as there are tools that are able to sniff all nearby packets even if they are not on the same local network.

### Cookies

A string value that a browser/server sends back to the client that acts as like a hand-stamp. It allows the client to continue browsing while on the same session, allowing the server to remember things like items in your cart, logged in status, etc. Cookies can be held for a range of times depending on server settings. Cookies are vulnerable to cookie session hijacking. If an attacker is able to sniff unencrypted packets and view the cookie data, the attacker could replicate their own data packet but with your cookie string value.


### HTTPS

An encrypted version of HTTP. Some information about the data is still viewable, like IP addresses of the recipients, but the sensitive information is encrypted.

### Certificate

A web server's public key that has been digitally signed by trusted third parties. When a user visits a website, it downloads the server's certificate and calculates a hash value. The public key of the certificate authority is then used to decrypt the signature which is then used to compare with the hash value. If it is the same, then it provides authenticity.

### Certificate Authority (CA)

The third parties whose purpose is to digitally sign server certificates.


### SSL Stripping
An attacker in the middle could modify unsecured data packets being transmitted and alter them to redirect the recipient. 


### HSTS

Hypertext Strict Transport Security. A server configuration that enforces TLS/HTTPS to browsers. In example, a user may type in http://example.com or www.example.com or example.com, the browser will be told by the server to change to https://example.com. Configurations could even preload HTTPS in browser source code, which would eliminate the window of oppurtunity of potential machine in the middle attacks as the browser knows to initiate HTTPS connection despite users initially typing HTTP in the URL.

### VPN

Allows parties to establish an encrypted channel. Useful for corporate environments where companies can ensure all data is encrypted no matter what services employees are using. Parties will often appear to be pinging from the VPN's location and not their actual geography.


### SSH

Allows machines/servers to connect to each and execute remote commands. SSH is an encrypted protocol.

### Port
A unique number that has been agreed upon by the world and is specified for a specific service/protocol. For example, Port 80 is HTTP, Port 443 is HTTPS, Port 22 is SSH, etc.

### Port Scanning
The process of enumerating and discovering ports that are actively open or listening.

### Firewall
A software or application that determines rules for inbound/outbound connections


### IP Address

Numeric unique address for computers/servers/domains, akin to a postal address.


### Deep Packet Inspection

When a firewall inspects the data packet and conducts actions based on the information within the packet.


### Proxy

A server or device that implements a connection in the middle of parties, who's purpose is to inspect data/packet/traffic and respond accordingly (allow, drop, etc.)


### URL Rewriting
A proxy could rewrite the URL the user is trying to visit by running it through the proxy's domain first. When used by a company/university/etc., it may be used for filtering and logging purposes.


### Malware
Software that conducts malicious activity. A virus is a type of malware that attaches itself to a host. A worm is a type of malware that can travel and infect other hosts on it's own. A botnet is a type of malware where it tries to infect a collective group of hosts where a C2 server can then issues commands (e.g. DDoS attack).


### Zero Day Attacks
An exploit that has not yet been identified, therefore it cannot be patched or mitigated yet.