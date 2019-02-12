### Procedure to install certificate on Ubuntu 14.04

Trying to run new certbot will fail:

```
dkz@blueInk:/etc/nginx/sites-available$ sudo certbot --nginx
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator nginx, Installer nginx

Which names would you like to activate HTTPS for?
-------------------------------------------------------------------------------
1: ultimheat.co.th
2: www.ultimheat.co.th
3: curabara.com
4: www.curabara.com
5: publibase.com
6: www.publibase.com
7: ultimheat.com
8: admin-museum.ultimheat.com
9: dico-chauffage.ultimheat.com
10: downloads.ultimheat.com
11: museum.ultimheat.com
12: museum2.ultimheat.com
13: museum22.ultimheat.com
14: www.ultimheat.com
15: uultimheat.com
16: tapp.wecanf.net
-------------------------------------------------------------------------------
Select the appropriate numbers separated by commas and/or spaces, or leave input
blank to select all options shown (Enter 'c' to cancel): 1
Obtaining a new certificate
Performing the following challenges:
Client with the currently selected authenticator does not support any combination of challenges that will satisfy the CA.
Client with the currently selected authenticator does not support any combination of challenges that will satisfy the CA.
```

# work-around.

```
dkz@blueInk:/etc/nginx/sites-available$ sudo certbot --authenticator webroot --installer nginx \
>   --webroot-path /home/pol3z/git-u4/blueink -d ultimheat.co.th
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator webroot, Installer nginx
Obtaining a new certificate
Performing the following challenges:
http-01 challenge for ultimheat.co.th
Using the webroot path /home/pol3z/git-u4/blueink for all unmatched domains.
Waiting for verification...
Cleaning up challenges
Deployed Certificate to VirtualHost /etc/nginx/sites-enabled/ultimheat.co.th for set(['ultimheat.co.th', 'www.ultimheat.co.th'])

Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
-------------------------------------------------------------------------------
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
-------------------------------------------------------------------------------
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 1

-------------------------------------------------------------------------------
Congratulations! You have successfully enabled https://ultimheat.co.th

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=ultimheat.co.th
-------------------------------------------------------------------------------

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/ultimheat.co.th/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/ultimheat.co.th/privkey.pem
   Your cert will expire on 2019-05-13. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot again
   with the "certonly" option. To non-interactively renew *all* of
   your certificates, run "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le


```
