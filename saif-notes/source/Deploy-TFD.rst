The First Date: Deployment
===========================

Proxy and Reverse Proxy
************************


Traefik
********


Domains and DNS In DigitalOcean
********************************
* To set up a domain name, you need to purchase a domain name from a domain name registrar and then set up **DNS records** for it.
* Registrars typically offer services to manage DNS records as well, but once you have purchases a domain, most registrars will allow you to manage your DNS records with other providers.
* You can manage your DNS records from the DigitalOcean Control Panel. 
* ``whois [domain.name]`` to find the Registrar of that domain, on the **Registrar URL line**.
* To use DigitalOcean DNS, you’ll need to update the nameservers used by your domain registrar to DigitalOcean’s nameservers instead.
* Once your domain is pointed to DigitalOcean’s nameservers, you can begin managing its DNS records from the Control Panel.
* ``nslookup [domain.name]`` a program to query Internet domain name servers.
* `https://docs.digitalocean.com/tutorials/dns-registrars/ <https://docs.digitalocean.com/tutorials/dns-registrars/>`_
* `DNS Lookup <https://www.digitalocean.com/community/tools/dns>`_  
* ``dig @ns1.digitalocean.com <YOUR-DOMAIN> NS`` to verify your domain’s delegation for DigitalOcean. 


Frappe/Erpnext Containers Deployment - DigitalOcean
*******************************************************
* Images: ``bench``, for dev. ``nginx``. ``socketio``. ``worker``.
* Compose Services: ``configurator``. ``backend``. ``db``/ ``redis`` (optional). ``frontend`` nginx serves JS/CSS assets and routes incoming requests. ``proxy`` Traefik Proxy?. ``websocket``. ``queue-short``/ ``queue-default``/ ``queue-long``. ``scheduler``.
* Overrides: ``overrides/compose.proxy.yaml``. ``overrides/compose.erpnext.yaml``:Replaces all Frappe images with ERPNext ones. ``overrides/compose.https.yaml``: Automatically sets up Let's Encrypt certificate and https. ``overrides/compose.mariadb.yaml``. ``overrides/compose.redis.yaml``.
* we also have to setup ``.env``: copy ``example.env`` to ``.env``?

* A single server with a static IP attached to it.

1. Install Docker and Docker-compose

* ``curl -fsSL https://get.docker.com | bash``: Install Docker
* ``curl -SL https://github.com/docker/compose/releases/download/v2.7.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose``: download and install Compose standalone
* ``chmod +x /usr/local/bin/docker-compose``: Apply executable permissions to the standalone binary in the target path for the installation.
* That's It.

2. ``git clone https://github.com/frappe/frappe_docker``: Clone Repo
3. ``cd frappe_docker``
4. ``mkdir ~/.gitops``: Create configuration and resources directory

* Register Domain in DigitalOcean
- Error ? ``domain xxx is already exists`` you are trying to host the domain which is already hosted in our server?
- 