# Local UDM install instructions

## Update Env File
- Update the file `udm-le.env` with the following entries
```
# Email for LetsEncrypt certificate issuance
CERT_EMAIL='ken@duffenterprises.com'

# The FQDN of your UDMP (comma separated fqdns are supported)
CERT_HOSTS='*.management.duffenterprises.com'

## Create Tar File
```
tar --exclude-vcs -czvf udm-le.tgz udm-le
```

## SCP Tar File
```
scp udm-le.tgz root@udm.management.duffenterprises.com:/mnt/data/
```

## Extract Tar file
```
tar -xvf udm-le.tgz
```

## Run initial install
Run `/mnt/data/udm-le/udm-le.sh initial`. This will handle your initial certificate generation and setup a cron task at `/etc/cron.d/udm-le` to attempt certificate renewal each morning at 0300.