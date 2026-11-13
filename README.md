<div align="center">

# 🔐 SECURELINK VPN GATEWAY

### Secure VPN for Remote Access: Site-to-Site and Client-to-Site Lab

![OpenVPN](https://img.shields.io/badge/OpenVPN-TLS%201.3-EA7E20?style=for-the-badge&logo=openvpn&logoColor=white)
![strongSwan](https://img.shields.io/badge/strongSwan-IKEv2%2FIPsec-1E88E5?style=for-the-badge)
![Encryption](https://img.shields.io/badge/Encryption-AES--256--GCM-2E7D32?style=for-the-badge)
![MFA](https://img.shields.io/badge/MFA-TOTP-8E24AA?style=for-the-badge)
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Kali](https://img.shields.io/badge/Kali-Linux-268BEE?style=for-the-badge&logo=kalilinux&logoColor=white)
![Status](https://img.shields.io/badge/Status-Lab%20Project-F9A825?style=for-the-badge)

**Author:** Kshitij Rajesh Randhire

</div>

---

> [!NOTE]
> A VMware lab that builds and tests a VPN with site-to-site and client-to-site access, using open-source tools only. It is a learning lab on virtual machines, **not a production deployment**.

## ✨ Highlights

| 🔒 Encryption | 🛡️ Authentication | 📊 Tested |
|:---:|:---:|:---:|
| TLS 1.3 + AES-256-GCM | Certificates + TOTP MFA | iperf3 with 1, 5 and 10 streams |
| IPsec IKEv2, AES-256 | Certificate revocation (CRL) | Linux and Windows clients |
| tls-crypt control channel | iptables access control | 38 evidence screenshots |

## 🧱 What was built

- 🌐 **Site-to-site:** strongSwan IKEv2/IPsec between `gw-hq` and `gw-branch` (AES-256, HMAC-SHA2-256, MODP-2048)
- 💻 **Client-to-site:** OpenVPN with TLS 1.3, AES-256-GCM, tls-crypt, certificate authentication and TOTP MFA (Linux and Windows)
- 🚧 **Access control:** iptables rules limiting VPN users to the HQ subnet, with denied traffic logged
- 📜 **Certificates:** Easy-RSA CA, certificate revocation list, revocation test
- 📡 **Monitoring:** rsyslog forwarding to a central log host, fail2ban, OpenVPN status file
- ⚡ **Performance:** iperf3 tests with and without the VPN
- 📋 **Policy:** VPN usage policy, incident response steps, GDPR and HIPAA alignment mapping

## 🛠️ Tools

`OpenVPN` `strongSwan` `Easy-RSA` `OpenSSL` `Google Authenticator (PAM)` `iptables` `rsyslog` `fail2ban` `iperf3` `Wireshark` `VMware` `Kali Linux` `Ubuntu 24.04`

## 📁 Repository layout

| Path | Contents |
|---|---|
| 📘 `00_Index_Traceability.docx` | Index, requirement-to-evidence traceability matrix, limitations |
| 📗 `D1` to `D6` `.docx` | The six deliverables |
| 🪟 `D3A_Windows_OpenVPN_Test_Report.docx` | Windows client test appendix |
| 📕 `PDF/` | PDF copies of every document |
| 🖼️ `Evidence/` | 38 screenshots (E01 to E38) and `screenshot_index.md` |

## ⚠️ Known limitations

> [!WARNING]
> The lab runs on one host with three VMs, and the HQ and branch LANs are simulated with dummy interfaces.

It uses a single client certificate and account, a single-tier CA, client-side compliance checks, unencrypted syslog (TCP 514), and no alerting or dashboards. Load balancing is two OpenVPN instances on one gateway, chosen by the client. Each document labels items as implemented, limited, or only recommended.

## 🚀 Planned next steps

1. Separate HQ and branch network segments with real hosts
2. Per-user certificates and accounts with role-based access rules
3. Server-side posture enforcement (for example a `client-connect` script) in place of the client-side script
4. Zabbix or ELK monitoring with alert rules and log retention; syslog over TLS
5. Multi-client load tests, an investigation of the iperf3 retransmissions, and a second gateway for real failover
6. Two-tier PKI with an offline root, and a test that ends live sessions after revocation

## ✍️ Authorship

The lab design, configuration, testing and screenshots are my own work. I used Claude (an AI assistant) only to help draft and edit the wording of the documents.
