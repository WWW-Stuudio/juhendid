# .htpasswd parooliga kaitsmine Zones

1. Loo .htpasswd fail serveri kausta (/data01/virt80293)
2. [Genereeri](https://hostingcanada.org/htpasswd-generator/) .htpasswd fail

```bash
peeter:generatedpassword/
```

1. Lisa .htaccess fail vastavasse kausta

```bash
AuthType Basic
AuthName "Password Protected Area"
AuthUserFile /data01/virtxxx/.htpasswd
Require valid-user
```
