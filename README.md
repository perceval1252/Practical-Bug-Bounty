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
