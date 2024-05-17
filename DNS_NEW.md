![image](https://github.com/nani05190682/Linux/assets/87597729/f145c533-0155-4b07-8339-c43b4f69da32)




![image](https://github.com/nani05190682/Linux/assets/87597729/96299b48-afed-405e-9270-87f8bd560534)




![image](https://github.com/nani05190682/Linux/assets/87597729/10569110-bf97-40d1-b1e4-9ea1eba79c32)








Configure DNS:

Pakages Required: bind, bind-utils


Configuration File: /etc/named.conf ; 

/etc/named.rfc1912.zone ; 

/etc/resolv.conf


Port: 53


Service: named




Step1: Install bind, bind-utils packages
			# yum install bind bind-utils
Step2: Modify named.conf file ## deleting unwanted entries in named.conf file
			# vim /etc/named.conf
				### delete from logging to root.key ( lastline)

Step3: Append /etc/named.rfc1912.zone with /etc/named.conf
			# cat /etc/named.rfc1912.zones >> /etc/named.conf 

Step4: Modify /etc/named.conf
			# vim /etc/named.conf



options {
        listen-on port 53 { 127.0.0.1; 192.168.44.10; };
        listen-on-v6 port 53 { ::1; };
        directory       "/var/named";
        dump-file       "/var/named/data/cache_dump.db";
        statistics-file "/var/named/data/named_stats.txt";
        memstatistics-file "/var/named/data/named_mem_stats.txt";
        secroots-file   "/var/named/data/named.secroots";
        recursing-file  "/var/named/data/named.recursing";
        allow-query     { localhost; any; };


zone "glotech.com" IN {
        type master;
        file "forward_zone";
        allow-update { none; };
};


Step5: goto “/var/named” and create forward_zone file:

		# cd /var/named
		# cp named.localhost forward_zone
Step6: Change the ownership of forward_zone file to “named”
		 # chown named:named forward_zone
		# -rw-r----- 1 named named 152 May 20 10:04 forward_zone

Step7: Modify forward_zone file
			# vim forward_zone
			$TTL 1D
@       IN SOA  glotech.com. rname.invalid. (
                                        060987  ; serial
                                        1D      ; refresh
                                        1H      ; retry
                                        1W      ; expire
                                        3H )    ; minimum
        NS      glotech.com.
glotech.com. IN A       192.168.44.10
server IN	A	192.168.44.10
client IN       A       192.168.44.11
client2 IN      A       192.168.44.12
client3 IN      A       192.168.44.13
client4 IN      A       192.168.44.14

Step8: Update /etc/resolv.conf file
		search
		nameserver 

Step9: restart named service
			# systemctl restart named
			# systemctl enable named

Step10: Client side configuration

Step8: Update /etc/resolv.conf file
		search glotech.com
		nameserver server_ip

	
Validation:
	# host glotech.com
	# nslookup glotech.com













