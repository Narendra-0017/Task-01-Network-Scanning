# **Task 1 – Local Network Port Scanning**

**Tools Used:** Nmap, Wireshark
**Network Range Scanned:** `10.87.88.0/24`
**Command Used:**

```
nmap -sS 10.87.88.0/24
```

---

## **Scan Results Summary**

### **Active Hosts Found:**

| IP Address   | Device    | Open Ports          | Services                    |
| ------------ | --------- | ------------------- | --------------------------- |
| 10.87.88.224 | Router    | 53                  | DNS                         |
| 10.87.88.89  | My Laptop | 135, 139, 445, 5357 | MSRPC, NetBIOS, SMB, WSDAPI |

**Scan output file:** `scan.txt`

---

## **Wireshark Analysis**

### **1. SYN Packets (Nmap scan requests)**

**Filter used:**

```
tcp.flags.syn == 1 and tcp.flags.ack == 0
```

Shows Nmap sending SYN packets to probe ports using a half-open TCP SYN scan.

**Screenshot:** `wireshark_syn.png`

---

### **2. SYN-ACK Packets (Open ports responding)**

**Filter used:**

```
tcp.flags.syn == 1 and tcp.flags.ack == 1
```

SYN-ACK responses indicate **open ports** on scanned devices.

**Screenshot:** `wireshark_synack.png`

---

### **3. RST Packets (Closed ports responding)**

**Filter used:**

```
tcp.flags.reset == 1
```

RST packets indicate **closed ports** rejecting the connection attempt.

**Screenshot:** `wireshark_rst.png`

---

## **Files Included**

* `scan.txt`
* `wireshark_syn.png`
* `wireshark_synack.png`
* `wireshark_rst.png`
* `README.md`

---

## **Conclusion**

The scan identified two active hosts and revealed both open and closed ports.
Wireshark confirms the behavior of a TCP SYN scan through captured SYN, SYN-ACK, and RST packets.
