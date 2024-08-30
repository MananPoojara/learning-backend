## What is Caddy

- Caddy Webserver, often simply referred to as “Caddy”,
- Is a web server written in Go (Golang) that is known for its automatic HTTPS capabilities,
- Ease of use, and extensibility. Its primary distinguishing feature is its ability to set up and renew SSL/TLS certificates automatically from :
  Let’s Encrypt,
  zeroSSl

## Working Of ACME(Automatic Certificate Management Environment) Protocol

![image.png](./images/image%20copy.png)

- Caddy utilizes the ACME (Automatic Certificate Management Environment) protocol to communicate with certificate authorities like Let’s Encrypt.
- It maintains an internal certificate storage to cache and manage these certificates.
- For challenges, it usually uses the HTTP and TLS-ALPN challenges, setting up temporary routes to fulfill them.
- Certificate renewals are automated and are handled before they expire, with Caddy managing potential failures to ensure continuous availability.

# Configuration

- So In Caddy We Have CaddyFile for hosting you site and all things that caddy give us
- The Caddyfile uses a domain-centric configuration style.
- So make one CaddyFile like i does in below image

- Also We can use JSON For all of this i show you difference in next step it's just small formate and syntax so it's your choice
- Caddy’s internals actually work with a JSON configuration. When using a Caddyfile, Caddy translates it into this JSON structure. This JSON structure is a direct representation of Caddy’s runtime structures.

Install Caddy [here](https://caddyserver.com/docs/install)

i am using Arch Linux

```sh
pacman -Syu caddy
```

and you can visit "/etc/caddy" ther is CaddyFile already exist you can edit that file

### But Before doing That just Stop Caddy Service first

- Command of Caddy

```
  > caddy start
  > caddy stop
  > caddy run
  > caddy reload
  > caddy fmt --overwrite (checking error before starting service)
```

- we also have to decide whether your workflow is API-based or CLI-based. (You can use both the API and config files on the same server, but we don't recommend it: best to have one source of truth.)

- So Caddy hase APIs and also you can configur using CaddyFile it's CLI Based so for now on i am using CaddyFile

make one blank CaddyFile

```sh
nano CaddyFIle
```

Then Paste below code in the file

```sh
app.localhost {
        root * /srv/www
        file_server
}
```

- Here we give Path where my site's files are stored(html,js,...)
- and file_server is directive If you want to learn more about directives how we use them to load balancing backends so follow
- [Here](https://caddyserver.com/docs/caddyfile/concepts#directives)

### Now Loading CaddyFile

> caddy adapt (adapting Caddyfile to server)
> caddy adapt --config path/Caddyfile
> caddy run

Now Go To Broser write app.Localhost and see here
![image.png](./images/image%20copy%202.png)

we can see connection secure We have our SSL Certificate :)
![image.png](./images/image%20copy%203.png)

You Can Look At this logs
![image.png](./images/image%20copy%204.png)
