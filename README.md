# Basic 4G config to setup a LTE modem

## If custom APN e.g. Zettanet then first create a wireless profile

```
request modem wireless create-profile profile-id 2 cl-1/0/0 slot 1 access-point-name splns357 authentication-method none
```

## Interface config

```
set interfaces cl-1/0/0 dialer-options pool 1
set interfaces cl-1/0/0 act-sim 1
set interfaces cl-1/0/0 cellular-options sim 1 select-profile profile-id 2
set interfaces cl-1/0/0 cellular-options sim 1 radio-access automatic
set interfaces dl0 description dl0_4G
set interfaces dl0 unit 0 family inet dhcp-client lease-time infinite
set interfaces dl0 unit 0 family inet negotiate-address
set interfaces dl0 unit 0 dialer-options pool 1
set interfaces dl0 unit 0 dialer-options always-on
set interfaces dl0 unit 0 dialer-options dial-string “*99#”
```
## Juniper Doco

https://www.juniper.net/documentation/en_US/junos/topics/topic-map/security-interface-config-lte-interfaces.html#id-lte-mini-pim-overview
