
1. create droplet on DO
2. ssh into droplet to make sure its working, [link](obsidian://open?vault=notes&file=Coding%2FCourses%2FFrontendMasters%20Full%20Stack%2FHow%20to%20ssh%20into%20your%20server)
3. buy domain on [namecheap](https://www.namecheap.com/)
4. Go to [domain list](https://ap.www.namecheap.com/domains/list/) and click on manage on the specific domain.
5. Scroll down to _nameservers_ and pick _custom DNS_ add in the following three
	1. ns1.digitalocean.com
	2. ns2.digitalocean.com
	3. ns3.digitalocean.com
6. Go back to DO, select the project that houses the droplet and click on the triple dot at the end, select _add a domain_.
7. Add your just purchased domain, e.g. `acdev.lol` point it to your droplet
8. Click on the domain, at the _Create new record_ section you will see _hostname_ and _will direct to_. 
	1. for hostname type `@` then for will direct to choose the droplet
	2. same thing but for hostname this time type `www`
9. Use `nslookup <domain>` to make sure its working 