# VPSDNS.co.za
A self-managed DNS resolver publically available for use based in South Africa.

# Public Hyperlocal Secure DNS Resolver (South Africa)

A high-performance, privacy-focused public DNS resolver architecture designed for low-latency, cryptographically secure name resolution within South Africa. 

Our dual-edge infrastructure pairs high-efficiency Nginx reverse-proxying for TCP-based layers with direct user-space UDP worker binding for next-generation QUIC handling, upstreamed to a hardened Technitium DNS core.

## ⚡ Real-World Performance Metrics
Captured via steady-state `dnspyre` regression testing (20 QPS across 4 concurrent threads hitting South African routing paths):

* **DNS-over-QUIC (DoQ):** ~30.02 ms mean latency | 46.14 ms $p99$ tail execution constraint.
* **DNS-over-TLS (DoT):** ~29.08 ms mean latency | 54.53 ms $p99$ tail execution constraint.
* **DNS-over-HTTPS (DoH):** ~31.56 ms mean latency | 37.75ms $p99$ tail execution constraint.

* **Resolver Network & Latency Context:** Latency metrics are typically captured via a persistent testing client located in George, WC routing directly to the central resolver in Johannesburg, GP (approx. 1,150 km fiber path distance). Under typical network environments, latency is primarily limited by physical fiber distance (approx. 1ms RTT per 100km of transit). If you are accessing this resolver from within Gauteng or the surrounding regions, your real-world status timings are designed to scale down significantly—typically yielding sub-5ms resolution speeds under normal routing conditions depending on upstream ISP routing.

## 🔒 Security & Privacy Policy
* **Zero Logging:** Client source IP addresses are processed entirely in-memory and are never written to persistent disks or database logs.
* **DNSSEC Validation:** Full cryptographic verification of upstream root zones to prevent DNS cache poisoning and man-in-the-middle hijacking.
* **Unfiltered & Natural:** We do not implement content filtering, blocklists, or resolution modifications. You receive raw DNS responses.

## ⚙️ Connection Endpoints & DNS Stamps

### 1. DNS-over-QUIC (DoQ)
* **Address:** `quic://doq.vpsdns.co.za:853`
* **Stamp:** `sdns://BAcAAAAAAAAADTEwMi4yMTQuMTAuODIgsz-TIivw3iPvQ_LMMbM65bYyD8n6RJZogCA-bZ1aKLMQZG9xLnZwc2Rucy5jby56YQ`

### 2. DNS-over-TLS (DoT)
* **Address:** `dot.vpsdns.co.za:853`
* **Stamp:** `sdns://AwcAAAAAAAAADTEwMi4yMTQuMTAuODIgsz-TIivw3iPvQ_LMMbM65bYyD8n6RJZogCA-bZ1aKLMQZG90LnZwc2Rucy5jby56YQ`

### 3. DNS-over-HTTPS (DoH)
* **Address:** `https://doh.vpsdns.co.za/dns-query`
* **Stamp:** `sdns://AgcAAAAAAAAADTEwMi4yMTQuMTAuODIgsz-TIivw3iPvQ_LMMbM65bYyD8n6RJZogCA-bZ1aKLMQZG9oLnZwc2Rucy5jby56YQovZG5zLXF1ZXJ5`
