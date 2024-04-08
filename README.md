# Practical-Bug-Bounty
This is a brief cheatsheet of practical bug bounty methodology that might (or not 0.0) help

### Some useful links
- https://owasp.org/Top10
- https://cwe.mitre.org/index.html
- https://www.sans.org/top25-software-errors

## Reconnaissance 
### Fingerprinting Web Technologies
This is a small list of websites/plugins that can get some informations about web technologies
- https://builtwith.com/
- https://securityheaders.com/
- wappalyzer
- ``curl -I -L http://example.com/`` ==> -I gives informations about headers, -L automaticly redirects
- ``nmap -p 443 -A example.com``==> Not recommended however

### Directory Busting
This is a non-binding list of some tools that are useful to perform this step. Always be careful about the number of request of the Scope.
- ``ffuf -w /usr/share/wordlist/SomeRandomWordlist.txt -u http://example.com/FUZZ``
- ``dirb http://exxample.com/``
- dirbuster (GUI)

IMPORTANT: Methodology is important, we can use whatever tool fits to us

#### Subdomain Enumeration
- We can use google as follow: site:example.com ==> Then if we find www for example, we can just add "-www" to our request, i.e. site:example.com -www
- https://crt.sh/ ==> %.example.com
- ``subfinder -d example.com -o example`` ==> -o fits for output. It will create an output file
- ``assetfinder example.com`` ==> Powerfull when used with ``grep`` or ``sort`` 
- ``amass enum -d example.com`` ==> Takes more time than other tools
- After we gained a bunch of output files, we can combine them, and then use ``httprobe`` such as: ``cat *file* | httprobe -prefer-https | grep https > examplealive`` ==> This should give us the "living" servers on our list
- ``gowitness file -f examplealive -P *Foldername* --no-http`` ==> IMPORTANT: Make sure to remove "https" from "https://example.com" ==> This will take screenshots of websites which we can explore easily 

### Authentication attacks
#### Broken Access Control
It happens when you have a user's token, and that you send a "PUT" request, but instead of modifying your own datas, you modify another user's data (with the same token for example.)
In burp, the extension named *authorized* can be useful to further examine the task.

### Automated tools
#### Free Tier
- OWASP ZAP
- Arachni
- Wapiti
- Vega
- SqlMap
- Skipfish

#### Commercial
- BurpSuite
- Nessus
- Acunetix
- Appscan
- Veracode
- Netsparker
- Qualys Web Application Scanning (WAS)

Automating the process:
1. Might be good to just click on many links on the website, so the tool can analyse it. Be cautions however of the fact that the tool might repeat many times the same request ==> Be careful about all POST requests...
2. Most of times, automation is out of scope, we really have to check for the conditions of the enterprise.
3. Findings with automation tools are pretty rare, therefore it's not worth losing too much time and effort using them (might be a 1/10 ratio).



