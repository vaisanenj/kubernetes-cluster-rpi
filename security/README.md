### Pihole
Pihole is an open-source DNS based filtering sulotion that focus blocking ads and malicious domains before your devices can even connect to them. Pihole alose increases performance by blocking unwanted advertisements.
[Boost your network security with pihole](https://air-gap.com.au/boost-your-network-security-with-pi-hole/)

In my deploy-pihole.yaml file I added extra command and arguments for container. With these arguments I am able to add add lists and regex matches to expand pihole default blocklist.

### Unbound 
In Pihole website they have great article about unbound and how it increase your security.
**A standard Pi-hole installation will do it as follows:**

    Your client asks the Pi-hole Who is pi-hole.net?
    Your Pi-hole will check its cache and reply if the answer is already known.
    Your Pi-hole will check the blocking lists and reply if the domain is blocked.
    Since neither 2. nor 3. is true in our example, the Pi-hole forwards the request to the configured external upstream DNS server(s).
    Upon receiving the answer, your Pi-hole will reply to your client and tell it the answer to its request.
    Lastly, your Pi-hole will save the answer in its cache to be able to respond faster if any of your clients queries the same domain again.

**After you set up your Pi-hole as described in this guide, this procedure changes notably:**

    Your client asks the Pi-hole Who is pi-hole.net?
    Your Pi-hole will check its cache and reply if the answer is already known.
    Your Pi-hole will check the blocking lists and reply if the domain is blocked.
    Since neither 2. nor 3. is true in our example, the Pi-hole delegates the request to the (local) recursive DNS resolver.
    Your recursive server will send a query to the DNS root servers: "Who is handling .net?"
    The root server answers with a referral to the TLD servers for .net.
    Your recursive server will send a query to one of the TLD DNS servers for .net: "Who is handling pi-hole.net?"
    The TLD server answers with a referral to the authoritative name servers for pi-hole.net.
    Your recursive server will send a query to the authoritative name servers: "What is the IP of pi-hole.net?"
    The authoritative server will answer with the IP address of the domain pi-hole.net.
    Your recursive server will send the reply to your Pi-hole which will, in turn, reply to your client and tell it the answer to its request.
    Lastly, your Pi-hole will save the answer in its cache to be able to respond faster if any of your clients queries the same domain again.
    
[Pihole Guides - unbound](https://docs.pi-hole.net/guides/dns/unbound/)

### OpenVPN
A Virtual Private Network (VPN) provides securely encrypted internet connection to your private network over the public internet. VPN protection is an important piece of a layered security protocol that's protect your data. Using VPN service gives ability to remotely access your local network resources outside.

[What is A VPN - OPENVPN](https://openvpn.net/what-is-a-vpn/)
