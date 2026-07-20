# Tailscale and SSH Configuration

## Objective

The goal of this project was to securely administer the Ubuntu Server VM from another device without exposing SSH directly to the public internet.

## Devices Connected

- Ubuntu Server VM
- Ubuntu cybersecurity laptop
- Windows gaming PC

All Devices were connected to the same Tailscale network.

## Tailscale Installation

Tailscale was installed on the Ubuntu systems using:

```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

The device was connected to the tailnet using:

```bash
sudo tailscale up
```

Connectivity was verified with:

```bash
tailscale status
```

---

## SSH Server Configuration

The initial SSH connection attempt returned:

```text
Connection refused on port 22
```

This confirmed that the server was reachable throug Tailscale, but no SSH service was listening

OpenSSH Server was isntalled using:

```bash
sudo apt update
sudo apt install opensshh-server
```

---

## SSH Key Authentication

An Ed25519 SSH key was generated on the Ubuntu laptop:

```bash
ssh-keygen -t ed25519
```

The public key was copied to the Ubuntu Sever VM:

```bash
ssh-copy-id username@server-hostname
```

---

## SSH Client Alias

To simplify connections, an SSH alias was added to a config file. 
Configuration:

```text
Host homelab
	HostName server-hostname
	User user
	IdentityFile *location of key*
```

The server can now be accessed with a single command:

```bash
ssh homelab
```

---

## Security Benefits

This configuratino provides several security improvements:

- no port forwarding requried on the home router
- SSH traffic travels entirely through the encrypted Tailscale network.
- Public-key authentication replaces repeated password entry.
- Remote administration is limited to approved devices on the tailnet.
- The server is not exposed to internet-side SSH scans or brute-force attacks.

---

## Troubleshooting

### Connection Refused 

**Symptom**

```text
Connection refused on port 22
```

**Cause**

The Ubuntu Server VM was reachable through Tailscale, but the OpenSSH Server package was not installed or running.

**Resolution**

```bash
sudo apt install openssh-server
```

---

## Lessons Learned

This project demonstrated several important Linux administration concepts:

- Installing and configuring services with `apt`.
- Managing system services with `systemctl`.
- Using Tailscale to create a secure private network.
- Configuring OpenSSH Server for remote administration
- Implementing SSH key authentication.
- Simplifying administration through SSH aliases.
- Troubleshooting connectivity by separating network issues from service configuration issues.

---

## Result

The Ubuntu Server VM can no be securely administered from the Ubuntu laptop using:

```bash
ssh homelab
```


