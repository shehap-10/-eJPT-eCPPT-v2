# Introduction To Information Gathering

## subdirectory

- sitemap_index.xml
    - This file is part of a website's sitemap structure and is designed to provide information to search engine crawlers about the organization of various sitemaps on the site. It helps search engines understand the hierarchy and relationships between different sitemaps.
- robots.txt
    - This file serves as a set of instructions for web crawlers (or bots) on how to interact with the content of a website. It specifies which areas of the site should not be crawled or indexed by search engines.

## passive information gathering

- **httrack**: A tool that allows you to download a website from the Internet to a local directory, building recursively all directories, getting HTML, images, and other files from the server to your computer. It can also update an existing mirrored site, and resume interrupted downloads. Example: **`httrack https://example.com`**
- **host**: A command-line tool that performs DNS lookups and displays information about the domain name, IP address, and other records. It can also be used to check the availability and reachability of a host. Example: **`host example.com`**
- **whois**: A tool that queries the whois database for domain registration information, such as the owner, contact details, expiration date, nameservers, and more. It can also be used to check the availability of a domain name. Example: **`whois example.com`**
- **Netcraft**: A web service that provides various information about websites, such as the web server, hosting provider, operating system, SSL certificate, technologies used, and more. It also offers a search engine that lets you explore websites visited by users of the Netcraft extensions. Example: [Netcraft Search](https://searchdns.netcraft.com/)
- **DNSRecon**: A tool that performs DNS enumeration, zone transfer, reverse lookup, brute force, cache snooping, and other DNS reconnaissance tasks. It can also generate reports in various formats, such as XML, JSON, CSV, and HTML. Example: **`dnsrecon -d example.com -t std`**
- **Dnsdumster**: A web service that performs DNS enumeration and displays the results in a graphical way. It uses open source intelligence resources to query for related domain data, such as subdomains, MX records, NS records, and more. Example: [Dnsdumster](https://dnsdumpster.com/)
- **wafw00f**: Analyzes the response of a web page to guess the type of Web Application Firewall (WAF) product it is using.
- **sublist3r**: Enumerates subdomains of websites using various search engines and other sources.
- **theHarvester**: Gathers open-source intelligence (OSINT) on a company or domain, such as names, emails, IPs, subdomains, and URLs.

### **Techniques and Operators for Google Dorks:**

1. **Google Dorks**: Search queries that use specific keywords or operators to find information on Google that is not easily accessible otherwise.
2. **Google Hacking Database**: A collection of Google dorks for different purposes, such as finding exposed files, scripts, or other resources.
3. **intitle:index of**: A Google dork operator that searches for pages with a specific word in the title and a directory listing.
4. **site:** A Google dork operator that searches for pages within a specific domain or site.
5. **.ext**: A Google dork operator that searches for pages with a specific file extension, such as .pdf, .doc, or .xls.
6. **inurl:** A Google dork operator that searches for pages with a specific word or phrase in the URL.
7. **archive:** A Google dork operator that searches for pages that are archived by Google, such as old versions or cached copies.

## Extensions

- **builtwith**: A tool that analyzes a website and reveals the technologies, frameworks, plugins, analytics, advertising, and other components used to build it. It can also provide historical and trend data, as well as competitive intelligence. Example: **`builtwith https://example.com`**
- **whatweb**: A tool that identifies websites based on their HTTP headers, HTML code, cookies, scripts, and other features. It can also perform passive and aggressive scans, and output the results in various formats, such as XML, JSON, SQL, and more. Example: **`whatweb https://example.com`**

![Untitled](Introduction%20To%20Information%20Gathering%201db2dc14155d484fbbbe9dcfb5341824/Untitled.png)

## Active information gathering+

1. **[dnsenum](https://github.com/fwaeytens/dnsenum)**: A Perl script for DNS reconnaissance tasks such as querying DNS records, attempting zone transfer attacks, performing subdomain enumeration, and gathering WHOIS information.
2. **dig**: A command-line tool for DNS queries, displaying results in a readable format. Example: **`dig example.com`**.
3. **[fierce](https://github.com/mschwager/fierce)**:  is a reconnaissance tool for locating non-contiguous IP space. discovering subdomains, IP ranges, and DNS servers using a wordlist and Google. Example: `fierce --domain google.com --subdomains accounts admin ads`
- host Discover
    - Netdiscover is a tool for finding online hosts on a network by sending or sniffing ARP requests. Example: **`netdiscover -r 192.168.1.0/24`**
    - @shahap-10 | @cyberhub | [INE](https://my.ine.com/)
    
    ### Nmap
    
    [Nmap-Cheat-Sheet.pdf](Introduction%20To%20Information%20Gathering%201db2dc14155d484fbbbe9dcfb5341824/Nmap-Cheat-Sheet.pdf)
