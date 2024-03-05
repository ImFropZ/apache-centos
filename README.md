# List of commands run in the video
- `yum install httpd` - Install the Apache web server
- `chcon -Rv --type=httpd_sys_rw_content_t /var/www/a.com/` - Set the SELinux context for the web root directory
- `firewall-cmd ––permanent ––add-port=80/tcp` - Open the firewall port for HTTP
- `firewall-cmd ––reload` - Reload the firewall
- `systemctl start httpd` - Start the Apache web server
- `systemctl reload httpd` - Reload the Apache web server

- `yum install openssl mod_ssl` - Install the SSL module for Apache
- `openssl genrsa -out ca.key 2048` - Generate a private key for the Certificate Authority
- `openssl req -new -key ca.key -out ca.crt` - Generate a certificate signing request for the Certificate Authority
- `openssl x509 -req -days 365 -in ca.crt -signkey ca.key -out ca.crt` - Generate a self-signed certificate for the Certificate Authority
- `cp ca.crt /etc/pki/tls/certs/` - Copy the Certificate Authority certificate to the system certificate directory
- `cp ca.key /etc/pki/tls/private/` - Copy the Certificate Authority private key to the system certificate directory