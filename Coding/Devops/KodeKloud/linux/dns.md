- first checks `/etc/hosts`. Static hostname-to-IP mappings.
- then checks `/etc/resolv.conf`. DNS nameserver configurations
- The order can be switched by editing `/etc/nsswitch.conf`, specifically this line `hosts: files dns`. 
	- `files` means `/etc/hosts`. 
	- `dns` means `/etc/resolv.conf`

### /etc/resolve.conf example 
```
nameserver 127.0.0.53
search ap-northeast-2.compute.internal
```
- `nameserver 127.0.0.53` means the dns server is at `127.0.0.53`
- `search ...` means when you do `ping web` the system will first try `web`, and if that fails, it will try appending the search domain: `web.ap-northeast-2.compute.internal`.

## domain

1. **`com`** → **Top-Level Domain (TLD)**
    - The highest level in the DNS hierarchy (e.g., `.com`, `.org`, `.net`).
2. **`google.com`** → **Root Domain (or Primary Domain)**
    - The main registered domain name (combining the SLD + TLD).
    - Often called the **"apex domain"** or **"bare domain"**.
3. **`apps`** → **Subdomain (Third-Level Domain)**
    - A subdivision of the root domain (e.g., `mail.google.com`, `drive.google.com`).

**Full URL:** `apps.google.com`
    - **TLD:** `.com`
    - **Root Domain:** `google.com`
    - **Subdomain:** `apps`

## Record Types
- A - maps domain name to ip v4
- AAAA - maps domain name to ip v6
- CNAME - maps domain to domain

**CNAME cannot coexist** with other records
1. **A/AAAA records** (to point directly to an IP)
    - Example:
        example.com      A      192.0.2.1  
        example.com      AAAA   2001:db8::1      
    - Use case: When your server has a **static IP address**.
        
2. **CNAME record** (to alias to another domain)
    - Example:
        example.com      CNAME  myapp.herokudns.com.  
    - Use case: When using a **third-party service** (Heroku, GitHub Pages, Cloudflare, etc.) that provides a domain.

For _subdomains_, you can mix _cname_ and other records
```
example.com       A       192.0.2.1      (Root domain → IP) 
www.example.com   CNAME   example.com    (Subdomain → Alias)
```

## tools
- `ping google.com`
- `nslookup google.com`
- `dig google.com`