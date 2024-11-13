1. go to Cloudflare dashbord, in the tab `account home` click add a domain.
2. go to namecheap dashboard, find nameservers under domain tab, add the nameservers provided by Cloudflare.
3. Make sure `DNSSEC` under advanced DNS is turned off.
4. If there is any errors follow the next steps
	1. First, check your SSL/TLS settings in Cloudflare:
	    - Go to SSL/TLS tab
	    - Under "Overview", ensure it's set to "Full" (not Flexible or Full Strict)
	    - If your origin server doesn't have a valid SSL certificate, use "Flexible" instead
	2. Check your SSL/TLS Edge Certificates:
	    - Go to SSL/TLS > Edge Certificates
	    - Enable "Always Use HTTPS"
	    - Under "Automatic HTTPS Rewrites", turn it ON
	3. Check your Page Rules:
	    - Go to Rules > Page Rules
	    - Make sure you don't have conflicting redirect rules
	    - If you have any rules for HTTP to HTTPS redirects, you might want to temporarily disable them
