# Firewall Configuration Task

## Objective

Configure and test basic firewall rules to allow or block traffic using Windows Firewall or UFW (Uncomplicated Firewall) on Linux.

---

## Tools Used
- Linux: UFW (Uncomplicated Firewall) 
- Remote testing performed from Windows machine using `curl`
  
  ---

## Steps Performed

### 1. Install UFW on Kali Linux

```bash
sudo apt update
sudo apt install ufw -y
```

### 2.  Enable UFW
```bash
sudo ufw enable
```

### 3. Check UFW status and current rules
```bash
sudo ufw status numbered
```

### 4. Add a rule to block inbound traffic (say port 8080)
```bash
sudo ufw deny 8080
```

### 5. Verify new firewall rules
```bash
sudo ufw status numbered
```

### 6. Test the rule by attempting to connect to that port locally or remotely(For ex- Windows machine)
-To know the ip address of your kali machine:
```bash
ip a
```
-Open Windows CMD and run: curl http://[your_ip]:8080
```bash
curl http://10.0.2.15:8080
```

### 7. Confirm SSH port 22 is allowed
```bash
sudo ufw status numbered
```

### 8. Remove the block rule to restore original firewall state
```bash
sudo ufw delete 2
sudo ufw delete 4
```

### 9. Verify final rules
```bash
sudo ufw status numbered
```

## Summary
A firewall is a security tool that monitors and controls incoming and outgoing network traffic based on pre-defined rules. It acts as a barrier between trusted and untrusted networks.

In this task, we used UFW (Uncomplicated Firewall) on Linux to:
- Allow traffic on port 22 (SSH) to enable remote connections.

- Block traffic on port 8080 to test access restrictions.

How it filters traffic:

- When a packet arrives, the firewall checks its source, destination, and port.

- It compares these against the rules defined by the user.

- If a rule matches, it either allows or denies the packet.

- If no rule matches, the default policy (typically "deny") is applied.

By modifying the firewall rules, we were able to control access to services and simulate basic network protection.
