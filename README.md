# YOP VPN
YOP VPN (Your Own Private VPN) is a fast, secure (state-of-the-art cryptography) and open-source VPN solution powered by [WireGuard](https://www.wireguard.com/) — giving you complete control over your online privacy.  
**Host it yourself. Own your traffic. Stay private.**

# Background
I wanted to watch a movie that has become unavailable in the cinemas in my region and I knew that it is available with a streaming subscription I already had but again, not in my region, only in US. As anyone would, I immediately thought of using a VPN service but I didn't want to pay the full month price for a two hour watching experience.

So, I built my own custom VPN with Wireguard. What follows is a quick guide about the script I eventually ended up using, instead of the manual steps.
The potential is huge, please check an extensive use case list at the end.

# Usage

./yopvpn [SERVER_IP]

## Quick steps
- Make sure your SSH key is uploaded to your account in the VPS provider's website
- Create a VPS server with any provider (e.g. DigitalOcean, Linode, Vultr, Hetzner, etc.) - extensive list at https://www.vpsbenchmarks.com/hosters
- Run the above command using the server IP you've just created
- Install the [Wireguard client](https://www.wireguard.com/install) (Win/MacOS/Linux/mobile)
- Import the downloaded file (from Downloads/peer1.conf) in the Wireguard client for desktop devices OR scan the downloaded image (from Downloads/peer1.png) for mobile devices from your Wireguard client

# Security
- Setup your VPS to use your computer's SSH keys (you can generate them by typing "how to generate ssh keys for Win/Mac/Linux" in google and AI will give you the steps)
- Wireguard is setup so that only you (or anyone who has the generated peer configuration file /opt/wireguard/config/peer1/peer1.conf) can connect to your WireGuard VPN.
  - The server generates a unique key pair for each peer (client).
  - Only someone with the private key from peer1.conf can connect as "peer1".
  - No one else can connect unless you give them a peer config or add more peers (and if you share their configs).

# Use Cases

## 🔒 Privacy & Security
Secure Internet Browsing
– Encrypt traffic on public Wi-Fi (cafés, airports, hotels).

Protection from ISPs & Advertisers
– Prevent tracking, DNS snooping, and bandwidth throttling.

Anonymity for Research or Whistleblowing
– Hide user identity while accessing sensitive or censored info.

Secure Communication
– Encrypt VoIP, messaging, and email traffic.

## 🌍 Remote Access & Networking
Access Home/Office Network Remotely
– Connect to home devices (e.g., NAS, printers, servers).

Self-Hosted Services Access
– Securely reach services like Pi-hole, Home Assistant, Nextcloud.

Connect Multiple Devices in a Virtual LAN
– Mesh networking between laptops, phones, and desktops.

Developer-Friendly Remote Dev Environments
– Tunnel into dev servers without exposing them to the public internet.

Cloud-Connected IoT Devices
– Securely route smart devices or Raspberry Pis through the VPN.

## 🚫 Censorship & Geo-Restrictions
Bypass Censorship in Restricted Countries
– Access blocked sites like Google, YouTube, or social media.

Geo-Unblocking for Content Streaming
– Appear as if you’re browsing from a different region or country.

Travel Use
– Keep a consistent, safe internet experience abroad.

## 🧪 Testing, Admin, & DevOps
Secure Server Management
– SSH into cloud infrastructure over a private, encrypted channel.

Internal API Testing or Demo Access
– Expose dev APIs securely without publishing them.

Network Simulation or Testing
– Route traffic to simulate network conditions across geographies.

Private CI/CD Pipelines or Build Systems
– Connect internal build tools without exposing them publicly.

## 👥 Multi-User or Team Use
Small Team Secure VPN
– Set up for a dev team, startup, or small business.

Family VPN
– Share with family members for safe browsing and private access.

Custom Access Control
– Restrict access to certain IPs or services per user.

## 🛡️ Advanced & Niche Use Cases
Kill Switch / Always-On VPN
– Enforce VPN-only internet for secure devices.

Split Tunneling
– Route only selected apps or services through the VPN.

Ad & Tracker Blocking (via DNS routing)
– Use with Pi-hole or AdGuard Home.

BYOVPN (Bring Your Own VPN)
– Host a personal VPN instead of paying for a 3rd party service.

Anonymous Torrenting (ethically)
– Encrypt P2P traffic for privacy-conscious users.

Gaming VPN
– Reduce ping or bypass region locks (with careful config).

## 💡 Educational or Business Use
Educational Tool
– Teach networking, encryption, Linux server admin, or privacy.

Startup or SaaS MVP
– Build a branded VPN service (white-label your stack).

Compliance-Driven Networking
– For teams needing HIPAA/GDPR-safe tunnels to cloud data.
