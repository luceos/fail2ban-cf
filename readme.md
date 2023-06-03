- add real ip from cloudflare inside nginx; see `/etc/nginx/conf.d/cloudflare-real-ip.conf`
- add nginx req http limiting which throttles requests to max 3 or bursted at 5; see `/etc/nginx/nginx.conf`
- tightened fail2ban for ssh
- added a new jail for fail2ban based on the nginx req http limiting logs, see `/etc/fail2ban/jail.d/nginx-req-limit.conf` which will check for hits that go beyond the throttle of 3 to 5 requests per second per ip within 60 seconds and if it finds 10 or more it will ban the ip in the firewall of the droplet for a duration of 10 minutes

Copy the fail2ban action:

```
sudo mv /etc/fail2ban/action.d/cloudflare.conf /etc/fail2ban/action.d/cloudflare.conf.bak
sudo cp fail2ban/cloudflare.conf /etc/fail2ban/action.d/cloudflare.conf
```

Edit the file so that `binban` points to the installation path of this repository.
