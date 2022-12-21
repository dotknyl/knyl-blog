---
layout: "../../layouts/PostLayout.astro"
title: "Set up Wildcard SSL for Godaddy domain with Let's Encrypt"
description: "Using Certbot to set up SSL for godaddy domain"
pubDate: "Dec 22 2022"
---

Let's Encrypt is a free, automated, and open certificate authority brought to you by the nonprofit Internet Security Research Group (ISRG). That's why I use this Certificate Authority for my website and other wildcard domains (\*.knyl.me).

To get a Let’s Encrypt certificate, you’ll need an ACME client software, and most people use [Certbot](https://certbot.eff.org/).

## Installation

1. **Update DNS Settings**

   &ensp;DNS domain to your server.

   ```
   ----------------------------------------
   |  Type  |  Name  |        Data        |
   ----------------------------------------
   |    A   |    @   |  <your server IP>  |
   |    A   |    *   |  <your server IP>  |
   ----------------------------------------
   ```

   The second record is used for wildcard domain, if you just want to get certificate for you original domain, you should add 2 type A records: `@` and `www`.

2. **Install Certbot**

   Enter [Certbot's website](https://certbot.eff.org/), choose the software and system.

   ![Choose Certbot Environtment](/blog/certbot-1.jpg)

   Follow the instructions to install Certbot.

3. **Install Certbot GoDaddy DNS**

   Certbot does not have an ofical DNS plugin for GoDaddy, to continue you need to install a third party plugin here:
   [https://github.com/miigotu/certbot-dns-godaddy](https://github.com/miigotu/certbot-dns-godaddy)

   ```bash
       pip install certbot-dns-godaddy
   ```

4. **GoDaddy Cridentials**

    Use of this plugin requires a configuration file containing godaddy API credentials, obtained from your [developer.godaddy.com](https://developer.godaddy.com)

    Create credentials file on your server:

**credentials.ini**

```
    dns_godaddy_secret      = 0123456789abcdef0123456789abcdef01234567
    dns_godaddy_key = abcdef0123456789abcdef01234567abcdef0123

```

5. **Validate domain**

   Please use this command:

   ```bash
       sudo certbot certonly
       --authenticator dns-godaddy
       --dns-godaddy-credentials <path_to_credentials.ini>
       --dns-godaddy-propagation-seconds 90
       --keep-until-expiring --non-interactive --expand
       --server https://acme-v02.api.letsencrypt.org/directory
       -d 'example.com'
       -d '*.example.com' # remove if you don't need validate wildcard domain
   ```
    When the progress was finished, your certificates would be stored at **/etc/letsencrypt/live/example.com**

6. **Renew**

- Test automatic renewal:

```bash
    sudo certbot renew --dry-run
```

- Renew:

```bash
    sudo certbot renew
```

## Conclusion

Here are all steps to set up Wildcard SSL for Godaddy domain with Let's Encrypt. I hope this article helpful for you.
