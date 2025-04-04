# IPv4 ACL Configuration

## Basic Router Configuration

### R0
```
hostname R0
int fa0/0
ip add 192.168.3.1 255.255.255.0
no shut

int fa0/1
ip add 192.168.1.1 255.255.255.0
no shut

ip route 192.168.2.0 255.255.255.0 192.168.3.2
```

### R1
```
hostname R1
int fa0/0
ip add 192.168.3.2 255.255.255.0
no shut

int fa0/1
ip add 192.168.2.1 255.255.255.0
no shut

ip route 192.168.1.0 255.255.255.0 192.168.3.1
```

## ACL1 - Block 2.101 but permit 2.100 from accessing 1/0 network

### R0
```
access-list 1 deny host 192.168.2.101
access-list 1 permit host 192.168.2.100
int fa0/1
ip access-group 1 out
```

## ACL 99 - Permit PC3 and PC2, deny PC1 access to 1/0 network

### R0
```
int f0/1
no ip access-group 1 out

access-list 99 deny host 192.168.2.100
access-list 99 permit any

int f0/1
ip access-group 99 out
```

## Extended ACLs

### ACL3 - Deny PC1 from accessing 1.0 network, permit others

#### R0
```
int e0/0/0
ip add 192.168.4.1 255.255.255.0
no shut
```

#### R1
```
ip route 192.168.4.0 255.255.255.0 192.168.3.1
```

#### R0
```
int f0/1
no ip access-group 99 out
```

#### R1
```
access-list 100 deny ip host 192.168.2.100 192.168.1.0 0.0.0.255
access-list 100 permit ip any any
int f0/1
ip access-group 100 in
```

## ACL4 - Permit 2.0 network to access 1.254 webserver, deny 1.100 PC

#### R1
```
int f0/1
no ip access-group 100 in

access-list 101 permit tcp 192.168.2.0 0.0.0.255 host 192.168.1.254 eq
