# VPSDNS.co.za
A self-managed DNS resolver publically available for use based in South Africa.

# Public Hyperlocal Secure DNS Resolver (South Africa)

A high-performance, privacy-focused public DNS resolver architecture designed for low-latency, cryptographically secure name resolution within South Africa. 

Our dual-edge infrastructure pairs high-efficiency Nginx reverse-proxying for TCP-based layers with direct user-space UDP worker binding for next-generation QUIC handling, upstreamed to a hardened Technitium DNS core.

## ⚡ Real-World Performance Metrics
Captured via steady-state `dnspyre` regression testing (20 QPS across 4 concurrent threads hitting South African routing paths):

* **DNS-over-QUIC (DoQ):** ~30.36 ms mean latency | 39.85 ms $p99$ tail execution constraint.
* **DNS-over-TLS (DoT):** ~31.18 ms mean latency | 52.43 ms $p99$ tail execution constraint.
* **DNS-over-HTTPS (DoH):** ~37.90 ms mean latency (Edge-accelerated via Cloudflare).

## 🔒 Security & Privacy Policy
* **Zero Logging:** Client source IP addresses are processed entirely in-memory and are never written to persistent disks or database logs.
* **DNSSEC Validation:** Full cryptographic verification of upstream root zones to prevent DNS cache poisoning and man-in-the-middle hijacking.
* **Threat Intelligence Filtering:** Integrated blocklists updated every 24 hours to automatically drop malicious botnets, phishing links, and malware delivery vectors at the edge.

## ⚙️ Connection Endpoints & DNS Stamps

### 1. DNS-over-QUIC (DoQ)
* **Address:** `quic://doq.vpsdns.co.za:853`
* **Stamp:** `sdns://BAcAAAAAAAAADTEwMi4yMTQuMTAuODIgsz-TIivw3iPvQ_LMMbM65bYyD8n6RJZogCA-bZ1aKLMQZG9xLnZwc2Rucy5jby56YQ`

### 2. DNS-over-TLS (DoT)
* **Address:** `dot.vpsdns.co.za:853`
* **Stamp:** `sdns://AwcAAAAAAAAADTEwMi4yMTQuMTAuODIgsz-TIivw3iPvQ_LMMbM65bYyD8n6RJZogCA-bZ1aKLMQZG90LnZwc2Rucy5jby56YQ`

### 3. DNS-over-HTTPS (DoH)
* **Address:** `https://doh.vpsdns.co.za/dns-query`
* **Stamp:** `sdns://AgMAAAAAAAAAAAAcZG9oLnZwc2Rucy5jby56YQovZG5zLXF1ZXJ5`
