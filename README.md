# ansible
configuration as code for my servers

## overview

when run together, this configure firewall, dns, vpn, and k3s nodes amung my system of cloud servers. They can all reach eachother over my wireguard vpn network, were my master node in my apartment acts as my hub ( hub configuration not present here )

### docker

install docker, deploy docker-compose template

### domain

install ddclient, register server with [name].rileysnyder.org address

### firewall

install ufw, allow 80, 22, 443

### k3s

install k3s, attach to main cluster

### minio

install minio

### postgres_bak

backup postgres db

### wireguard

install wireguard, connect to main network

### hosts.yml (not shown)

```
all:
  vars:
    k3s_url: https://10.253.0.10:6443
    k3s_token: <redacted> 
    wg_public_key: <redacted> 
  children:
    cloud:
      hosts:
        oc0:
          ansible_host: oc0.rileysnyder.org
          ansible_user: ubnutu 
          dns_domain: oc0 
          dns_user: <redacted> 
          dns_password: <redacted>  
          wg_id: 5
          wg_private_key: <redacted> 
          wg_shared_key: <redacted> 
        oc1:
          ansible_host: oc1.rileysnyder.org
          ...
```