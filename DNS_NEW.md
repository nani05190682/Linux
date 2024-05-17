![image](https://github.com/nani05190682/Linux/assets/87597729/f145c533-0155-4b07-8339-c43b4f69da32)




![image](https://github.com/nani05190682/Linux/assets/87597729/96299b48-afed-405e-9270-87f8bd560534)




![image](https://github.com/nani05190682/Linux/assets/87597729/10569110-bf97-40d1-b1e4-9ea1eba79c32)



# Configure DNS

**Packages Required:** `bind`, `bind-utils`

**Configuration Files:**
- `/etc/named.conf`
- `/etc/named.rfc1912.zone`
- `/etc/resolv.conf`

**Port:** 53

**Service:** `named`

## Steps

### Step 1: Install bind and bind-utils packages

```bash
# yum install bind bind-utils
```

### Step 2: Modify named.conf file
Delete unwanted entries in `named.conf`.

```bash
# vim /etc/named.conf
```
Delete from `logging` to `root.key` (last line).

### Step 3: Append /etc/named.rfc1912.zone to /etc/named.conf

```bash
# cat /etc/named.rfc1912.zones >> /etc/named.conf
```

### Step 4: Modify /etc/named.conf

```bash
# vim /etc/named.conf
```

Append the following content:

```conf
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
};

zone "glotech.com" IN {
    type master;
    file "forward_zone";
    allow-update { none; };
};
```

### Step 5: Create forward_zone file

Navigate to `/var/named` and create `forward_zone` file:

```bash
# cd /var/named
# cp named.localhost forward_zone
```

### Step 6: Change ownership of forward_zone file to “named”

```bash
# chown named:named forward_zone
# -rw-r----- 1 named named 152 May 20 10:04 forward_zone
```

### Step 7: Modify forward_zone file

```bash
# vim forward_zone
```

Append the following content:

```conf
$TTL 1D
@       IN SOA  glotech.com. rname.invalid. (
                                060987  ; serial
                                1D      ; refresh
                                1H      ; retry
                                1W      ; expire
                                3H )    ; minimum
    NS      glotech.com.
glotech.com. IN A       192.168.44.10
server IN    A          192.168.44.10
client IN    A          192.168.44.11
client2 IN   A          192.168.44.12
client3 IN   A          192.168.44.13
client4 IN   A          192.168.44.14
```

### Step 8: Update /etc/resolv.conf file

```conf
search glotech.com
nameserver 192.168.44.10
```

### Step 9: Restart named service

```bash
# systemctl restart named
# systemctl enable named
```

### Step 10: Client-side configuration

Update `/etc/resolv.conf` file on the client:

```conf
search glotech.com
nameserver 192.168.44.10
```

## Validation

```bash
# host glotech.com
# nslookup glotech.com
```


















