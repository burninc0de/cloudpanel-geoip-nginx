# How To Update Cloudpanel GeoIP Database

In case anyone else is wondering about this:

> [!TIP]
>  Cloudpanel Nginx uses the older GEOIP Nginx module with "legacy GeoiP" database.
>
It is located here:

```
/etc/nginx/geoip/GeoIP.dat
```

> [!WARNING]  
> If you want to update your database, Maxmind is USELESS, since they do not offer or allow downloads of legacy GeoIP databases.

Luckily the friendly fellow at [Mailfud](https://mailfud.org/geoip-legacy/) got you covered.

> Here you can find regularly updated versions of the discontinued GeoIP legacy databases. Many distributions still use old GeoIP libraries, so you might find these useful. I use these on many systems myself, so consider the files and site stable.

## Update Your CloudPanel GeoIP Database

```bash
wget -q --no-clobber -O /etc/nginx/geoip/GeoIP.dat.gz https://mailfud.org/geoip-legacy/GeoIP.dat.gz && gunzip -f /etc/nginx/geoip/GeoIP.dat.gz
```

Make sure to restart nginx afterwards:

```
systemctl restart nginx
```
## Automated Weekly Updates
```bash
0 0 * * 0 wget -q --no-clobber -O /etc/nginx/geoip/GeoIP.dat.gz https://mailfud.org/geoip-legacy/GeoIP.dat.gz && gunzip -f /etc/nginx/geoip/GeoIP.dat.gz && systemctl restart nginx
```
