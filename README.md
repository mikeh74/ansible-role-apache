# Apache2 Role

An Ansible role for installing and configuring Apache2 on Ubuntu systems with
support for virtual hosts, SSL/TLS, and custom modules.

## Requirements

- Ubuntu 22.04 LTS (Jammy), 24.04 LTS (Noble), or compatible
- Ansible 2.4 or higher
- `community.general` collection for apache2_module

## Role Variables

### Apache Configuration

```yaml
apache_packages:
  - apache2
```
List of packages to install for Apache. Defaults to `apache2`.

```yaml
apache_modules:
  - rewrite
  - ssl
```
List of Apache modules to enable. Defaults to `rewrite` and `ssl`.

```yaml
apache_service: apache2
```
Name of the Apache service for starting/restarting. Defaults to `apache2`.

### Virtual Hosts

```yaml
virtual_hosts:
  - name: example
    server_name: example.com
    server_admin: admin@example.com
    document_root: /var/www/example
```

Optional list of virtual hosts to configure. Each virtual host supports:
- `name` (required): Identifier for the site configuration file
- `server_name` (required): Domain name for the virtual host
- `server_admin` (required): Administrator email address
- `document_root` (required): Path to the site's document root

**Note**: Each virtual host automatically gets its own log files:
- `/var/log/apache2/{name}-error.log`
- `/var/log/apache2/{name}-access.log`

### SSL/TLS Configuration

```yaml
ssl_cert_path: /etc/ssl/certs/example.crt
ssl_key_file: /etc/ssl/private/example.key
ssl_chain_file: /etc/ssl/certs/chain.crt  # Optional
```

When `ssl_cert_path` and `ssl_key_file` are defined, an SSL virtual host is
automatically created on port 443. The role validates that certificate files
exist before configuring SSL.

## Features

- ✓ Installs and configures Apache2
- ✓ Enables custom Apache modules
- ✓ Creates HTTP and HTTPS virtual hosts
- ✓ Per-site log files
- ✓ Apache 2.4 syntax (Require directives)
- ✓ SSL certificate validation
- ✓ Configuration validation before restart
- ✓ Idempotent operations

## Example Playbooks

### Basic Apache Installation

```yaml
- hosts: webservers
  roles:
    - role: apache
```

### Apache with Virtual Hosts

```yaml
- hosts: webservers
  roles:
    - role: apache
      vars:
        apache_modules:
          - rewrite
          - ssl
          - headers
        virtual_hosts:
          - name: mysite
            server_name: mysite.com
            server_admin: webmaster@mysite.com
            document_root: /var/www/mysite
```

### Apache with SSL

```yaml
- hosts: webservers
  roles:
    - role: apache
      vars:
        ssl_cert_path: /etc/ssl/certs/mysite.crt
        ssl_key_file: /etc/ssl/private/mysite.key
        ssl_chain_file: /etc/ssl/certs/chain.pem
        virtual_hosts:
          - name: mysite
            server_name: mysite.com
            server_admin: admin@mysite.com
            document_root: /var/www/mysite
```

## Dependencies

None

## License

MIT

## Author

mhorrocks
