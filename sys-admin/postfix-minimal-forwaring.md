### Setup Postfix for Minimal Forwarding

##### Install Postfix

```
sudo apt-get install postfix
```

##### Configure Postfix

Edit `/etc/postfix/main.cf` to contain:
```
virtual_alias_domains = [DOMAIN_NAME]
virtual_alias_maps = hash:/etc/postfix/virtual
```

Edit `/etc/postfix/virtual` to contain:
```
[NAME]@[DOMAIN_NAME]    [FORWARD_NAME]@[FORWARD_DOMAIN_NAME]
```

##### Poke Postfix

postmap /etc/postfix/virtual
service postfix reload

##### References

http://www.cyberciti.biz/faq/linux-unix-bsd-postfix-forward-email-to-another-account/
