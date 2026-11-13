# Secure VPN for Remote Access (Lab Project)

A small VMware lab that builds and tests a VPN with both site-to-site and client-to-site access, using open-source tools only. This is a learning lab on virtual machines. It is not a production deployment.

**Author:** Kshitij Rajesh Randhire

The lab design, configuration, testing and screenshots are my own work. I used Claude (an AI assistant) only to help draft and edit the wording of the documents.

**Tools:** OpenVPN, strongSwan, Easy-RSA/OpenSSL, Google Authenticator (PAM), iptables, rsyslog, fail2ban, iperf3, Wireshark, VMware, Kali Linux, Ubuntu 24.04

## What was built

- **Site-to-site:** strongSwan IKEv2/IPsec between `gw-hq` and `gw-branch` (AES-256, HMAC-SHA2-256, MODP-2048)
- **Client-to-site:** OpenVPN with TLS 1.3, AES-256-GCM, tls-crypt, certificate authentication and TOTP MFA (Linux and Windows clients)
- **Access control:** iptables rules limiting VPN users to the HQ subnet, with denied traffic logged
- **Certificates:** Easy-RSA CA, certificate revocation list, revocation test
- **Monitoring:** rsyslog forwarding to a central log host, fail2ban, OpenVPN status file
- **Performance:** iperf3 tests with and without the VPN (1, 5 and 10 streams)
- **Policy:** VPN usage policy, incident response steps, GDPR and HIPAA alignment mapping

## Repository layout

| Path | Contents |
|---|---|
| `00_Index_Traceability.docx` | Index, requirement-to-evidence traceability matrix, limitations |
| `D1` to `D6` `.docx` | The six deliverables |
| `D3A_Windows_OpenVPN_Test_Report.docx` | Windows client test appendix |
| `PDF/` | PDF copies of every document |
| `Evidence/` | 38 screenshots (E01 to E38) and `screenshot_index.md` |

## Known limitations

The lab runs on one host with three VMs, and the HQ and branch LANs are simulated with dummy interfaces. It uses a single client certificate and account, a single-tier CA, client-side compliance checks, unencrypted syslog (TCP 514), and no alerting or dashboards. Load balancing is two OpenVPN instances on one gateway, chosen by the client. Each document labels items as implemented, limited, or only recommended.

## Planned next steps

1. Separate HQ and branch network segments with real hosts
2. Per-user certificates and accounts with role-based access rules
3. Server-side posture enforcement (for example a `client-connect` script) in place of the client-side script
4. Zabbix or ELK monitoring with alert rules and log retention; syslog over TLS
5. Multi-client load tests, an investigation of the iperf3 retransmissions, and a second gateway for real failover
6. Two-tier PKI with an offline root, and a test that ends live sessions after revocation
