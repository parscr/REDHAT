Configure email delivery

null client. A null client is a machine that can only send mail. It receives no mail from the network, and it does not deliver any mail locally

postfix-null-client Manual Install.
# yum install postfix

# systemctl start postfix
# systemctl enable postfix

# firewall-cmd --permanent --add-service=smtp
# firewall-cmd --add-service=smtp


# vi /etc/postfix/main.cf

1. myhostname = engs-XXXX.eng.ox.ac.uk 
2. mydomain = eng.ox.ac.uk 
3. myorigin = $mydomain 
4. inet_interfaces = loopback-only 
5. mydestination = 
6. relayhost = [smtp.ox.ac.uk]:25
7. disable_dns_lookups = yes

Line 1. FQDN of the postfix server
Line 2. Domainname of the postfix server
Line 3. Send mail as "user@example.com" (instead of "user@hostname.example.com")
Line 4. Do not accept mail from the network.
Line 5. Leave blank so mail is saved on the central mail server Not clinet
Line 6. Where Postfix should send all outgoing mail
line 7. If set to yes postfix will not perfrom DNS lookups to resolve the hostname

# systemctl restart postfix


# systemctl –l status postfix
# journalctl –xn
# postconf –n
