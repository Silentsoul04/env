# asn, whois

```bash
# RIPE - RIR API database
whois -h whois.arin.net -v 1.2.3.4
# :( Outdated
curl 'https://api.hackertarget.com/aslookup/?q=1.2.3.4'
# Query by number
curl 'https://stat.ripe.net/data/as-overview/data.json?resource=AS1234'
# Query by country
curl 'https://stat.ripe.net/data/country-asns/data.json?resource=de'
# Query all
curl 'https://stat.ripe.net/data/ris-asns/data.json?list_asns=true'
```

- https://bgpview.io/
- http://whoxy.com
- http://viewdns.info/
- https://domainbigdata.com/
- https://www.godaddy.com/whois

- https://web.archive.org/web/*/https://who.is/whois/thomascook.com
- || https://www.apnic.net/static/whowas-ui/

- https://securitytrails.com/blog/asn-lookup

# dns

```bash
dig -t AXFR foo.com
host -a foo.com
```

- https://host.io/
- https://securitytrails.com/domain/0x00sec.org/dns

```bash
subfinder -silent -d 0x00sec.org | dnsprobe -silent | awk  '{ print $2 }'  | sort -u | tee -a ips.txt
org=$(curl -s <https://ipinfo.io/$ip> | jq -r '.org')
title=$(timeout 2 curl -s -k -H "Host: 0x00sec.org" <https://$ip/> | pup 'title text{}')
```

- https://delta.navisec.io/a-pentesters-guide-part-5-unmasking-wafs-and-finding-the-source/
- https://susam.in/blog/sinkholed/

# redirects

- YouTube => Invidious
- Twitter => Nitter
- Instagram => Bibliogram
- Google Maps => OSM

```javascript
javascript:void(window.open('https://web.archive.org/web/*/'+location.href.replace(/\/$/,%20'')));
```

# blacklists

- https://pulsedive.com/submit/
- https://www.abuseipdb.com/report

# company

- http://opencorporates.com
- state databases
    - https://businesssearch.sos.ca.gov/

# person

- http://truepeoplesearch.com

### business resources

- linkedin
- [Find Other Websites Owned By The Same Person](http://analyzeid.com/)

### social networks

- http://tweetbeaver.com

# ssl

- [crt\.sh | Certificate Search](https://crt.sh/)
- http://certdb.com/

# subdomains

- https://findsubdomains.com/
- https://pentest-tools.com/information-gathering/find-subdomains-of-domain
- https://github.com/tomnomnom/waybackurls

# google search

```
inurl:MyOrg.com 'login: *' 'password= *' filetype:xls
site:www.MyOrg.com inurl:administrator_login.asp
https://www.google.com/search?q=intitle:%22index%20of%22
```

# email

- [Trumail | Free Email Verification API](https://trumail.io/)

```
telnet mail.abccorp.com 25
HELO example.com
MAIL FROM: testing@example.com
RCPT TO: your_email@somedomain.com
RCPT TO: another_email@somedomain.com
```

```bash
curl emailrep.io/john.smith@gmail.com
```

# exif data

- http://exif.regex.info/exif.cgi

# geo location

- https://extreme-ip-lookup.com/
- https://censys.io/ipv4?q=
- https://beta.shodan.io/search?query=google.com

```bash
# Ours
curl -4 https://ipinfo.io | jq -r '.ip'
# Theirs
curl ipinfo.io/54.90.107.240
greynoise 54.90.107.240
shodan host 216.58.210.206
```

# source code

- https://publicwww.com/
- https://nerdydata.com/
- https://searchcode.com/?q=

### github

- https://www.gitlogs.com/
- http://gitmostwanted.com/
- http://www.gharchive.org/
- http://10degres.net/github-tools-collection/

- https://github.com/search?q=user%3Afoo+fork%3Atrue&type=Repositories
- https://docs.github.com/en/github/searching-for-information-on-github/searching-for-repositories#search-by-repository-name-description-or-contents-of-the-readme-file
- https://api.github.com/repos/AdoptOpenJDK/openjdk11-binaries/tags?per_page=100&page=2

# web history

- https://web.archive.org
    - e.g.
    - https://web.archive.org/web/20200810173036if_/https://github.com/jaffarahmed/CREST-Exam-Prep
    - https://web.archive.org/web/*/https://raw.githubusercontent.com/jaffarahmed/CREST-Exam-Prep/master/*
        - https://raw.githubusercontent.com/jaffarahmed/CREST-Exam-Prep/master/Breakout%201%20%2B%20UNIX1.pdf
- https://archive.is
- hybrid analysis
- google/yandex cache
    - http://webcache.googleusercontent.com/search?q=cache:foo
- wget -r -k -np
- https://github.com/ArchiveTeam/grab-site
- https://github.com/pirate/ArchiveBox/wiki/Configuration
    - CHROME_USER_DATA_DIR
- https://linkchecker.github.io/linkchecker/
- https://www.npmjs.com/package/broken-link-checker-local

- https://delta.navisec.io/author/navisec/
- https://inteltechniques.com/JE/OSINT_Packet_2019.pdf
- https://github.com/jivoi/awesome-osint
- https://github.com/lockfale/osint-framework
- https://github.com/sinwindie/OSINT
- https://osint.link/
- https://twitter.com/OSINTtechniques
- https://0xpatrik.com/osint-domains/
- https://medium.com/@Peter_UXer/osint-how-to-find-information-on-anyone-5029a3c7fd56

# phone contacts

- https://www.bellingcat.com/resources/how-tos/2019/04/08/using-phone-contact-book-apps-for-digital-research/

# cross-reference

- https://aleph.occrp.org/

# +

[DEF CON 15 \- Moore and Valsmith \- Tactical Exploitation \- YouTube](https://www.youtube.com/watch?v=_WebzmDgJ5Q)
smtp bounce discloses ip
application in-memory credentials reused
ip id scanning [sequence analysis] - if large delta between id increments, large count of packets sent (e.g. backups)
    16-bit value that is unique for every datagram for a given source address, destination address, and protocol, such that it does not repeat within the maximum datagram lifetime (MDL)
    https://www.cellstream.com/reference-reading/tipsandtricks/314-the-purpose-of-the-ip-id-field-demystified
    https://tools.ietf.org/html/rfc6864
null-byte in hostname discloses index
authentication relays between protocols (e.g. ntlm to smtp, img src with unc path to trigger smb connection and mitm smb negotiation)

