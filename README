# Nginx Reverse Proxy for Blockchain Nodes on Alastria Networks

This repository holds an example nginx reverse proxy to allow serverless applications that do not have a static IP a way to access a locked down Alastria network blockchain node.

## Requirements

You will need a server that will host this nginx reverse proxy, this could be an AWS EC2 Machine, or a VPS from a different vendor.

You will also need either [Docker](https://docs.docker.com/engine/install/), or for you to set-up a native nginx server on the machine that will run the reverse proxy.

You will also need an Alastria Network Blockchain Node, that should be inaccessible from the outside (by having an IP filter at the infrastructure level, or by having some other restriction on the software level).

## How to use this repository (Docker)

To get started, you will want to clone this repository to the machine either by downloading and uploading directly, or by using git's clone command:
```sh
git clone https://github.com/alastria/reverse-proxy-nginx
```

Once you have cloned the repository, you will want to edit and configure the `nginx.conf` file provided.  
Please note to edit line 57 to point to the correct IP and Port for your node, or this will not work.
By default, this nginx server will run only through HTTP, so if you want to use HTTPS, you will have to either set it up through infrastructure (for example an AWS Application Load Balancer), or directly from Nginx (by getting a valid SSL Certificate and importing it in Nginx.  
[Here's instructions to import a SSL Certificate in Nginx.](http://nginx.org/en/docs/http/configuring_https_servers.html))  
You can generate an SSL Certificate with Certbot, or purchase one from a Certificate Authority (CA).  
You will also want to modify the default API Key provided in Line 12 of the `nginx.conf`, as well as enable it, that way nobody with access to this repo can use that example api key to authenticate to your Nginx reverse proxy.

You can also modify how the authentication is done, as by default it does use API Keys that are hardcoded within the `nginx.conf`, but maybe you want an external authentication server that generates, provides, and manages API Keys dynamically, so that you have a bit more control over the API Keys.

Once you have all the configuration ready, simply run the following command within the directory where the `docker-compose.yaml` file is located, and the Nginx server will be up and running:
```sh
docker compose up -d
```

You will then be able to call the IP or domain name of the reverse proxy as you normally would the node.

## How to use this repository (Native Nginx)

To get started, you will want to download `nginx.conf` from this repository.  

Once you have downloaded the `nginx.conf` file, you will want to edit it to configure the service.  
Please note to edit line 57 to point to the correct IP and Port for your node, or this will not work.
By default, this `nginx.conf` will make it so that the Nginx server only accepts HTTP requests, so if you want to use HTTPS, you will have to either set it up through infrastructure (for example an AWS Application Load Balancer), or directly from Nginx (by getting a valid SSL Certificate and importing it in Nginx.  
[Here's instructions to import a SSL Certificate in Nginx.](http://nginx.org/en/docs/http/configuring_https_servers.html))  
You can generate an SSL Certificate with Certbot, or purchase one from a Certificate Authority (CA).  
You will also want to modify the default API Key provided in Line 12 of the `nginx.conf`, as well as enable it, that way nobody with access to this repo can use that example api key to authenticate to your Nginx reverse proxy.

After configuring the file you downloaded, you will replace your own `nginx.conf` with this new file, as to apply all configuration changes that it makes.  
You can find your `nginx.conf` at `/usr/local/nginx/conf`, `/etc/nginx`, or `/usr/local/etc/nginx` in linux. See [Nginx's official documentation](https://docs.nginx.com/nginx/admin-guide/basic-functionality/managing-configuration-files/) for where to find the config files.  
Once replaced, simply run `sudo systemctl restart nginx` and the reverse proxy should boot up.

You will then be able to call the IP or domain name of the reverse proxy as you normally would the node.