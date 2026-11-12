# Screenshot Index

Project: Establishing a Secure Virtual Private Network (VPN) for Remote Access
Deliverables: D1 VPN Architecture Design, D2 Encryption & Authentication Plan, D3 VPN Client Configuration Guide, D4 Monitoring & Logging Plan, D5 Performance & Scalability Report, D6 Policy & Compliance Documentation.

Server logs are in UTC. The Kali client clock shows local time, 4 hours behind UTC.

| ID · File | What it shows | Deliverable |
|---|---|---|
| E01 · 01_ipsec_established_esp | IPsec site-to-site tunnel ESTABLISHED (IKEv2, AES-256, HMAC-SHA2-256, MODP-2048), 10.10.1.0/24 to 10.10.2.0/24, ping 0% loss, ESP packets in tcpdump | D1, D2 |
| E02 · 02_cert_inventory_modulus_redacted_key | Certificate and key inventory (paths, permissions), certificate/key match by modulus hash, redacted key block | D2 |
| E03 · 03_gw-hq_cert_modulus_crl | gw-hq server certificate details, issuer, validity, EKU; CRL contents | D2 |
| E04 · 04_client_profile | client.ovpn client profile | D3 |
| E05 · 05_client_connect_compliant_split_tunnel | Compliant client connects: server certificate verified, TLS 1.3, AES-256-GCM, only 10.10.1.0/24 pushed | D2, D3 |
| E06 · 06_split_tunnel_route | Client routing table with a single pushed route | D1, D3 |
| E07 · 07_server_mfa_accepted_push_route | Server log: TOTP code accepted, route pushed | D2 |
| E08 · 08_mfa_wrong_code_client_authfailed | Wrong TOTP code rejected with AUTH_FAILED (client side) | D2 |
| E09 · 09_mfa_pam_config_authlog | PAM configuration for MFA; auth.log with accepted codes and one invalid code | D2 |
| E10 · 10_ip_br_a_server_conf_grep | Server interfaces and key server.conf settings | D1, D2 |
| E11 · 11_access_control_iptables_vpn_deny | FORWARD rules for both tunnels, packet counters, VPN-DENY log lines | D1, D2, D4 |
| E12 · 12_access_control_client_blocked | Client reaches 10.10.1.1; traffic to 10.10.2.1 is blocked | D2 |
| E13 · 13_compliance_fail | Device compliance check fails, connection blocked | D3 |
| E14 · 14_compliance_pass_connect | Device compliance check passes, VPN starts | D3 |
| E15 · 15_compliance_script_source_iperf_run2 | vpn-connect.sh source, key file permissions, iperf3 second run | D3, D5 |
| E16 · 16_services_active_listeners | Both OpenVPN instances active, UDP 1194 and 1195 listening | D1, D5 |
| E17 · 17_fail2ban_listeners_hash_vpn_path | fail2ban ban and unban, listeners, SHA-256 hash on server, SSH login from 10.8.0.2 | D2, D4 |
| E18 · 18_sha256_scp_client_side | SHA-256 hash on client, file copied through the tunnel | D2 |
| E19 · 19_status_file_connected_client | OpenVPN status file listing the connected client | D4 |
| E20 · 20_iperf3_run1 | iperf3 first run: no VPN baseline and VPN with 1, 5 and 10 streams | D5 |
| E21 · 21_load_balancing_1194 | client-lb profile connects to instance 1 (UDP 1194) | D5 |
| E22 · 22_load_balancing_1195 | client-lb profile connects to instance 2 (UDP 1195) | D5 |
| E23 · 23_revocation_revoke_and_crl | Certificate revoked, CRL regenerated, serial listed | D2, D6 |
| E24 · 24_revocation_server_log_accept_reject | Server log: revoked certificate accepted before revocation, rejected after | D2, D6 |
| E25 · 25_revocation_client_rejected | Client side: TLS key negotiation fails with the revoked certificate | D2, D6 |
| E26 · 26_ca_cert | Self-signed root CA certificate (SecureLink-VPN-CA, CA:TRUE, valid Oct 27 2026 to Oct 24 2036), SHA-256 fingerprint, CRL contents | D2 |
| E27 · 27_rsyslog_forward_config_gw-hq | rsyslog forwarding rule on gw-hq: OpenVPN, sshd, sudo, charon and kernel messages sent to gw-branch (192.168.232.132) over TCP 514 | D4 |
| E28 · 28_rsyslog_test_message_and_received_logs_gw-branch | Test message from gw-hq received on gw-branch; per-service log files stored under /var/log/remote/gw-hq/ (Oct 31 2026, UTC) | D4 |
| E29 · 29_win_openvpn_version | Windows client: OpenVPN 2.7.8 (OpenSSL 3.6.5, DCO) installed | D3, D3A |
| E30 · 30_win_cert_transfer_scp | Windows client: CA, client certificate, key and tls-crypt key copied from gw-hq with scp | D3A |
| E31 · 31_win_profile_verify | Windows client: client.ovpn paths corrected, key directives verified | D3A |
| E32 · 32_win_credentials_prompt | OpenVPN GUI user name and TOTP prompt | D3A |
| E33 · 33_win_connect_route_ping | Windows client: server certificate verified, TLS 1.3, AES-256-GCM, single route, ping to 10.10.1.1 succeeds, 10.10.2.1 blocked | D2, D3A |
| E34 · 34_win_wrong_code_authfailed | Windows client: wrong TOTP code, "Wrong credentials", AUTH_FAILED | D2, D3A |
| E35 · 35_win_server_journal_mfa | gw-hq journal: accepted codes, invalid verification code, AUTH_FAILED (UTC) | D2, D3A |
| E36 · 36_win_wireshark_encrypted_udp1194 | Wireshark on VMnet8: only OpenVPN P_DATA_V2 packets on UDP 1194 | D2, D3A |
| E37 · 37_win_wireshark_no_plain_icmp | Wireshark filter icmp: 0 of 56 packets displayed (tunnelled traffic not readable) | D2, D3A |
| E38 · 38_win_posture_defender_firewall | Windows manual posture check: Defender, real-time protection and firewall profiles enabled | D3A |
