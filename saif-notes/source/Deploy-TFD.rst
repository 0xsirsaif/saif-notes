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