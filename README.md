# How To Update Cloudpanel GeoIP 

In case anyone else wonders about this:

> [!GEOIP On CloudPanel Nginx]
> Cloudpanel Nginx uses the v1 GEOIP module with "legacy GeoiP" database. It is located here "/etc/nginx/geoip/GeoIP.dat". To update that, Maxmind is USELESS. Luckily the friendly guys at MailFud got you covered.
>
> > [!NOTE]  
> Highlights information that users should take into account, even when skimming.
> >
> >
> >

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]  
> Crucial information necessary for users to succeed.

> [!WARNING]  
> Critical content demanding immediate user attention due to potential risks.

> [!CAUTION]
> Negative potential consequences of an action.

This will run an automatic udpate from their service:

```bash
wget -q --no-clobber -O /etc/nginx/geoip/GeoIP.dat.gz https://mailfud.org/geoip-legacy/GeoIP.dat.gz && gunzip -f /etc/nginx/geoip/GeoIP.dat.gz
```

or as a weekly cron:
```bash
0 0 * * 0 wget -q --no-clobber -O /etc/nginx/geoip/GeoIP.dat.gz https://mailfud.org/geoip-legacy/GeoIP.dat.gz && gunzip -f /etc/nginx/geoip/GeoIP.dat.gz && systemctl restart nginx
```
