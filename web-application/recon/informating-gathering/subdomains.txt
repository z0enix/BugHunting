## Passive sources
```
# https://github.com/OWASP/Amass
# https://github.com/OWASP/Amass/blob/master/examples/config.ini
amass enum -passive -d domain.com

# https://github.com/projectdiscovery/subfinder
# https://github.com/projectdiscovery/subfinder#post-installation-instructions
subfinder -d domain.com -all -silent

# https://github.com/tomnomnom/assetfinder
assetfinder example.com

# https://github.com/tomnomnom/waybackurls
# https://github.com/tomnomnom/unfurl
echo domain.com | waybackurls | unfurl -u domains

# https://github.com/lc/gau
# https://github.com/tomnomnom/unfurl
gau --subs example.com | unfurl -u domains

## Cert Transparency
# https://certificate.transparency.dev/
# https://crt.sh/
# https://github.com/glebarez/cero
cero example.com
# https://github.com/UnaPibaGeek/ctfr
python3 ctfr.py -d domain.com

# Active crtsh monitoring
#https://github.com/g0ldencybersec/gungnir
gungnir -r domains.txt

# https://github.com/gwen001/github-subdomains
github-subdomains -d example.com -t tokens.txt -o output.txt

# https://github.com/christophetd/censys-subdomain-finder
python3 censys-subdomain-finder.py example.com

# https://github.com/SmoZy92/Shodomain
python shodomain.py <SHODAN-API-KEY> example.com

# https://github.com/Cgboal/SonarSearch
crobat -s example.com
```

## Active DNS resolution
```
# Generate custom resolvers list, always
# https://github.com/vortexau/dnsvalidator
dnsvalidator -tL https://public-dns.info/nameservers.txt -threads 200

# https://github.com/d3mondev/puredns
puredns resolve subdomains.txt -r ~/Tools/resolvers.txt

## BF
# https://github.com/d3mondev/puredns
puredns bruteforce ~/Tools/subdomains.txt united.com -r ~/Tools/resolvers.txt

# https://github.com/projectdiscovery/shuffledns
shuffledns -d example.com -list example-subdomains.txt -r resolvers.txt
```
## Alterations and permutations
```
#https://github.com/Josue87/gotator
gotator -sub subdomains/subdomains.txt -perm permutations_list.txt -depth 1 -numbers 10 -mindup -adv -md
```

## Crawling
```
# 1st resolve subdomains on valid websites
# https://github.com/projectdiscovery/httpx
cat subdomains.txt | httpx -follow-host-redirects -random-agent -status-code -silent -retries 2 -title -web-server -tech-detect -location -o webs_info.txt
# Clean output
cat webs_info.txt | cut -d ' ' -f1 | grep ".domain.com" | sort -u > websites.txt
# Crawl them
# https://github.com/jaeles-project/gospider
gospider -S websites.txt --js -t 20 -d 2 --sitemap --robots -w -r > urls.txt
# Clean output
# https://github.com/tomnomnom/unfurl
cat urls.txt | sed '/^.\{2048\}./d' | grep -Eo 'https?://[^ ]+' | sed 's/]$//' | unfurl -u domains | grep ".domain.com"
```
## DNS records
```
# https://github.com/projectdiscovery/dnsx
dnsx -retry 3 -a -aaaa -cname -ns -ptr -mx -soa -resp -silent -l subdomains.txt
```

## DNS wordlists
```
# https://gist.githubusercontent.com/six2dez/a307a04a222fab5a57466c51e1569acf/raw
# https://wordlists-cdn.assetnote.io/data/manual/best-dns-wordlist.txt
# https://gist.github.com/jhaddix/f64c97d0863a78454e44c2f7119c2a6a
```

## Search engines
- [Baidu](http://www.baidu.com)
- [Yahoo](http://www.yahoo.com)
- [Google](https://www.google.com)
- [Bing](https://www.bing.com)
- [Yandex](https://www.yandex.ru)
- [Exalead](https://www.exalead.com/search)
- [Dogpile](http://www.dogpile.com)

## Specialized search engines

- [ZoomEye](https://www.zoomeye.org)
- [FOFA](https://fofa.so)
- [Shodan](https://www.shodan.io)
- [ThreatCrowd](https://www.threatcrowd.org)

## Certificate transparency

- [Crt.sh](https://crt.sh/?q=%25target.com)
- [Certspotter.com](https://certspotter.com/api/v0/certs?domain=target.com)
- [Google Transaprency report](https://transparencyreport.google.com/https/certificates)
- [Facebook CT Monitoring](https://developers.facebook.com/tools/ct)
- [Certstream](https://certstream.calidog.io)
- [CertDB](https://certdb.com/)
- [Censys.io](https://censys.io)

## Public datasets

- [Scans.io](https://scans.io)
- [Riddler](https://riddler.io)
- [SecurityTrails](https://securitytrails.com/dns-trails)
- [Common Crawl](http://commoncrawl.org)
- [PassiveTotal / RiskIQ Community API](https://api.passivetotal.org)
- [DNSDB](https://www.dnsdb.info)
- [Forward DNS dataset](https://opendata.rapid7.com/sonar.fdns_v2/)
- [WhoisXML API](https://www.whoisxmlapi.com)
- [PremiumDrops.com](https://premiumdrops.com/lists.html)

## Online DNS tools & DNS aggregators

- [VirusTotal](https://www.virustotal.com/#/home/search)
- [Dnsdumpster](https://dnsdumpster.com)
- [Cloudflare](https://www.cloudflare.com/)
- [Netcraft](http://searchdns.netcraft.com)
- [FindSubdomains](https://findsubdomains.com)
- [viewdns.info](https://viewdns.info/)
- [Site Dossier](https://pentester.land/blog/subdomains-enumeration-cheatsheet/www.sitedossier.com)

## Git repositories

- [Github](https://github.com)
- [Gitlab](https://gitlab.com)

