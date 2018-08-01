

Copy the fail2ban action:

```
sudo mv /etc/fail2ban/action.d/cloudflare.conf /etc/fail2ban/action.d/cloudflare.conf.bak
sudo cp fail2ban/cloudflare.conf /etc/fail2ban/action.d/cloudflare.conf
```

Edit the file so that `binban` points to the installation path of this repository.
