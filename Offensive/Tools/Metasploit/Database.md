``` bash
systemctl start postgresql

#need to be postgres user
sudo msfdb init

#OPTIONAL: delete db
sudo msfdb delete

msfconsole
#check db connection
> db_status

```