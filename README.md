# minecraftbots
apt install ipset
ipset create blacklist hash:ip
iptables -I INPUT -m set --match-set blacklist src -j DROP
iptables -I FORWARD -m set --match-set blacklist src -j DROP
