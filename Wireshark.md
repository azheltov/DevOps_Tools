# Wireshark Cheat Sheet

## Basic Wireshark Filters

### Filter by Protocol
- **HTTP traffic**:
  http
- **TCP traffic**:
  tcp
- **UDP traffic**:
  udp
- **DNS traffic**:
  dns
- **ICMP (Ping) traffic**:
  icmp

### Filter by IP Address
- **Source IP**:
  ip.src == 192.168.1.100
- **Destination IP**:
  ip.dst == 192.168.1.101
- **Specific IP (either source or destination)**:
  ip.addr == 192.168.1.100

### Filter by Port Number
- **Specific port** (e.g., HTTP on port 80):
  tcp.port == 80
- **Source port**:
  tcp.srcport == 443
- **Destination port**:
  tcp.dstport == 443

### Filter by Network Range (CIDR)
- **Subnet range (e.g., 192.168.1.0/24)**:
  ip.addr == 192.168.1.0/24

### Filter by MAC Address
- **Source MAC address**:
  eth.src == 00:1A:2B:3C:4D:5E
- **Destination MAC address**:
  eth.dst == 00:1A:2B:3C:4D:5F

### Filter by Protocol Fields
- **Filter by TCP Flags (e.g., SYN)**:
  tcp.flags.syn == 1
- **Filter by TCP retransmissions**:
  tcp.analysis.retransmission
- **Filter by TCP handshake (SYN-ACK)**:
  tcp.flags.syn == 1 && tcp.flags.ack == 1

### Filter by Time Range
- **Packets captured in the last 10 seconds**:
  frame.time_relative >= 10

---

## Capture Filters

### Capture HTTP traffic only
tcp port 80

### Capture traffic from a specific host
host 192.168.1.100

### Capture traffic to/from a specific subnet
net 192.168.1.0/24

### Capture only TCP traffic
tcp

### Capture only UDP traffic
udp

### Capture ICMP (ping) traffic
icmp

---

## Common Wireshark Tasks

### 1. Follow TCP Stream
To analyze the communication between two devices, **right-click** on a packet and select **"Follow" > "TCP Stream"**. This allows you to see the conversation between the two hosts for a specific TCP connection.

### 2. Coloring Rules
Wireshark color-codes packets by default to make analysis easier. To adjust or create custom color rules:
  - Go to **View > Coloring Rules**.
  - Add or modify rules for specific protocols.

### 3. Analyze DNS Requests
To filter and analyze DNS queries:
dns.qry.name == "example.com"
This will show all DNS queries that are requesting `example.com`.

### 4. Display TCP Flags
Filter traffic by specific TCP flags:
- **SYN**:
  tcp.flags.syn == 1
- **ACK**:
  tcp.flags.ack == 1

### 5. Find Large Packets
To find packets larger than a specific size (e.g., 1000 bytes):
frame.len > 1000

### 6. Find Packets with Errors
To find packets with issues, such as TCP retransmissions or duplicate ACKs:
tcp.analysis.flags

### 7. Export Specific Packets
To export selected packets:
  - Highlight the desired packets.
  - Go to **File > Export Specified Packets**.

### 8. Save Packet Capture
After capturing traffic, save the capture for later analysis by going to **File > Save As**.

### 9. Filter by HTTP Request Methods
- **GET Requests**:
  http.request.method == "GET"
- **POST Requests**:
  http.request.method == "POST"

---

## Useful Wireshark Shortcuts

- **Ctrl + E**: Start/stop packet capturing.
- **Ctrl + K**: View capture options (interfaces, filters, etc.).
- **Ctrl + F**: Open the search/filter dialog.
- **Ctrl + Shift + F**: Open the "Find Packet" dialog to search for a specific string, byte, or field.
- **Ctrl + Shift + P**: Preferences window.
- **Ctrl + H**: Show the packet history/statistics.

---

## Analyze Traffic for Issues

### 1. Packet Loss
To identify packet loss or retransmissions, you can use the following filter:
tcp.analysis.retransmission

### 2. Slow Network Performance
Look for high **latency** or **round-trip time (RTT)** by inspecting the `Time` column (enable it by right-clicking on the columns). You can also filter for TCP segments with a high delay:
tcp.analysis.ack_rtt > 0.5
(Where `0.5` represents 500ms RTT.)

### 3. Identify Duplicate Packets
To find duplicate packets (which may indicate an issue with the network):
tcp.analysis.duplicate_ack

---

## TCP Stream Analysis

### Analyze Handshake
To analyze the TCP 3-way handshake:
tcp.flags.syn == 1 || tcp.flags.ack == 1 || tcp.flags.fin == 1
This will show SYN, SYN-ACK, and FIN packets to help you visualize the connection setup and teardown.

### Analyze Throughput
To evaluate throughput or how much data is transferred over time:
  - Go to **Statistics > I/O Graphs**.
  - You can customize the graph to show packet rates, data size, or errors.

---

## Conclusion

This cheat sheet covers many common tasks you'll encounter while using **Wireshark**. 
Mastering filters is key to focusing on relevant traffic, especially when dealing with large captures. 
You can also customize **Wireshark**'s behavior with capture filters, display filters, 
and advanced shortcuts to tailor it to your specific needs.
