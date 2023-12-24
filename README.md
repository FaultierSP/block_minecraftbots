Banning known ip addresses of Minecraft bots from scanning your server. Uses Debian onboard tools.

```
apt install ipset ipset-persistent
ipset create blacklist hash:ip
iptables -I INPUT -m set --match-set blacklist src -j DROP
iptables -I FORWARD -m set --match-set blacklist src -j DROP
```

Modify ~/.bashrc:
```
alias banip='ipset add blacklist -exist'
source ~/.bashrc
```

Then:
```
banip <IP>

ipset save blacklist -f ipset-blacklist
sudo ipset restore -! < ipset-blacklist
```

Manuals:
https://linux.die.net/man/8/ipset
https://confluence.jaytaala.com/display/TKB/Using+ipset+to+block+IP+addresses+-+firewall
