```
http {
    limit_req_zone $binary_remote_addr zone=one:10m rate=50r/s;

    server {
        listen 80;

        # Serve static files directly from the root URL
        location / {
            root /var/www/public;
            try_files $uri $uri/ @backend;
        }

        # Rate limit only dynamic endpoints
        location /api/ {
            limit_req zone=one burst=20 nodelay;
            proxy_pass http://backend;
        }

        # Proxy all other requests to the backend
        location @backend {
            proxy_pass http://backend;
        }
    }
}
```

### How NGINX Selects a `location` Block

NGINX evaluates `location` blocks in the following order:
1. **Exact Match (`location = /path`)**:
    - If a request exactly matches a `location` block defined with `=`, NGINX uses that block immediately.
    - Example: `location = /api/login` will only match `/api/login`, not `/api/login/` or `/api/login/other`.
2. **Prefix Match (`location /path`)**:
    - NGINX looks for the longest matching prefix among all `location` blocks.
    - Example: `location /api/` will match `/api/login`, `/api/users`, etc.
3. **Regex Match (`location ~ /regex/`)**:
    - If no exact or prefix match is found, NGINX evaluates regex-based `location` blocks in the order they appear in the configuration.
4. **Default Match (`location /`)**:
    - If no other `location` block matches, NGINX falls back to the default `location /`.