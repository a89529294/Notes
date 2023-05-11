To understand the big picture:
1.  You bought a domain name from domain registrar (Namecheap) and a virtual server (Droplet on Digital Ocean). Virtual server is exposed to the public internet and has an IP address that anybody can use to reach it.
2.  You need to instruct your domain registrar to associate your domain name with the IP address of your server, so when anybody types your domain name in a browser (or in general makes a request through URL that contains your domain name), DNS servers know what IP address should be given to the requester to proceed. In case of Digital Ocean there are two ways:
    1.  You can set up the connection between domain name and IP address in the domain registrar [admin UI](https://www.namecheap.com/support/knowledgebase/article.aspx/319/2237/how-can-i-set-up-an-a-address-record-for-my-domain/).
    2.  You can instruct registrar to [delegate](https://docs.digitalocean.com/tutorials/dns-registrars/) the [setup to Digital Ocean](https://docs.digitalocean.com/products/networking/dns/how-to/manage-records/).
3.  After you've done all that, you now need to instruct your virtual server to accept HTTPS and (optionally) HTTP connections so people can actually interact with your server through browser (or other means). In case of Digital Ocean Droplets you will probably need to [setup the firewall](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-20-04) (unless it comes already pre-configured) to allow external access to ports 443 (for HTTPS traffic) and (optionally) 80 (for HTTP traffic). As part of the Droplet setup you probably need to allow access to port 22 also (so you can control your Droplet by connecting to it via SSH).
4.  Now you need something on your virtual server to actually process those requests that the firewall let in. This is where your app comes in.
    1.  Depending on your deployment model you might want to have a [reverse proxy/gateway](https://medium.com/intrinsic-blog/why-should-i-use-a-reverse-proxy-if-node-js-is-production-ready-5a079408b2ca) as a first thing that will process these incoming requests. Most popular is probably [Nginx](https://www.nginx.com/), but it's configuration is so frustratingly annoying that I'd suggest to use something like [Kong](https://konghq.com/) (which is based on Nginx anyway but has a more manageable way of configuring). The gateway will then pass requests to your app.  
5.  Finally, your app. First you need to deliver the app to the virtual server somehow. There are multiple ways to do that:
    1.  You can manually copy the build artefacts (or the source code) through SSH. Be wary that if you copy the source code, then you need to have the tools installed on your virtual server that can actually build that source code (e.g. NodeJS).
    2.  You can setup FTP to do the same.
    3.  You can pull the source code from a GIT repository to do the same (only for source code though).
    4.  You can setup a service like Dropbox that will simplify the delivery of files to your virtual server.
    5.  You can pack your build artefacts into a container image and then use container engine like [Docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04) or [Podman](https://podman.io/getting-started/installation) on your virtual server to download and run the image.
    6.  You can setup a CI/CD pipeline on your source control provider (e.g. GitHub Actions or Azure DevOps Pipelines) that automates any of the above.
    7.  Probably something else that I didn't think about.
6.  Now you need to actually run your app in way that allows you to not manually restart it each time it crashes or the server restarts.
    1.  If you delivered the bare build artefacts or have built it from source code on the spot, you'll probably need to look at [systemd](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units). It will take care of the lifecycle of your app.
    2.  If you use a container engine, you'll need to [instruct it](https://docs.docker.com/config/containers/start-containers-automatically/) to do the same.
7.  Hopefully, at this point your app is finally running and can receive and process requests from the internet.

If that sounds like a lot of shit to figure out, it actually is :) Alternatively you can use Platform-as-a-Service (PaaS) solution to do all that work for you. Digital Ocean has [App Platform](https://docs.digitalocean.com/products/app-platform/) where it can connect to your repo and automatically build your code, pack it into a container, fire up the virtual server and deploy the container on it without the need of you manually doing all these steps yourself. Digital Ocean is not the only one to offer such PaaS, as others have mentioned, you can also check [fly.io](https://fly.io/), [Render](https://render.com/) and probably some others that I don't know much about. You can also check the big guys like AWS, GCP or Azure, but smaller dedicated PaaS services should be easier to figure out.

----------

Forgot to mention that to serve HTTPS traffic you'll need to manage SSL-certificates.

If you're using PaaS solution, they are probably managed for you (although you'll need to provide the proof of domain ownership by adjusting DNS records in a certain way, PaaS service will provide you the details).

If you're on your own, a popular and free way to do that is to use [Let's Encrypt](https://letsencrypt.org/). The setup depends on what reverse proxy/gateway you use, if any. Here are some examples how to do that:
-   [No reverse proxy](https://itnext.io/node-express-letsencrypt-generate-a-free-ssl-certificate-and-run-an-https-server-in-5-minutes-a730fbe528ca) (setup HTTPS in expressjs directly).
-   [Nginx](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04).
-   [Kong](https://docs.konghq.com/hub/kong-inc/acme/).

General idea is that you (well, not exactly you, but Let's Encrypt's agent software [certbot](https://certbot.eff.org/pages/about)) generate a cryptographic key pair, encrypt some stuff with the private key and then allow the Let's Encrypt to download the stuff and decrypt it with a public key to prove that you own the domain and also have the keys. This process is called the "challenge". Let's Encrypt will then mark you as a trusted domain, and will give you an SSL certificate that you can use to manage your HTTPS traffic. certbot will periodically renew the certificate to make sure it doesn't expire and your website doesn't break because of that.