##github-pages-with-subdomain-cloudflare## [SOLVED?]

+I tried to setup a custom sub domain for my github page, with my root domain managed by cloudflare.

+After 4x editing the A-records with github ip-adresses and CNAME record with [profilename.github.io], i verified the custom domain after check i get this 

error:

**Your site's DNS settings are using a custom subdomain, www.example.org , that is set up as an A record. We recommend you change this to a CNAME record pointing to example.github.io. For more information, see documentation (InvalidARecordError).**

But i can visit the site on the subdomain with SSL and Enforce HTTPS is [x]


now i configured my CNAME sub.[profilename.github.io] and www.sub.[profilename.github.io]  proxy status DNS only

after that i saw DNS check succesful - now i see DNS check in Progress -constant- ????? 

---
i saw something about CNAME Flattening 
think this can be the issue!! (I have to study more)
https://developers.cloudflare.com/dns/cname-flattening/set-up-cname-flattening/

bron:

Using a subdomain for your GitHub Pages site
A subdomain is the part of a URL before the root domain. You can configure your subdomain as www or as a distinct section of your site, like blog.example.com.

Subdomains are configured with a CNAME record through your DNS provider. For more information, see Managing a custom domain for your GitHub Pages site.

www subdomains
A www subdomain is the most commonly used type of subdomain. For example, www.example.com includes a www subdomain.

www subdomains are the most stable type of custom domain because www subdomains are not affected by changes to the IP addresses of GitHub's servers.

Custom subdomains
A custom subdomain is a type of subdomain that doesn't use the standard www variant. Custom subdomains are mostly used when you want two distinct sections of your site. For example, you can create a site called blog.example.com and customize that section independently from www.example.com.

https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages#supported-custom-domains

last update github-pages w/... 2025-05-23