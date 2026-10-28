(Uncomplicated Firewall)

``` bash
sudo ufw status
sudo ufw enable

#Default outgoing policy changed to 'allow'
sudo ufw default allow outgoing

#Disable ssh
sudo ufw deny 22/tcp

#To list down all the active rules in a numbered order
sudo ufw status numbered

sudo ufw delete 2
```