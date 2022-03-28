# Migrate site with TAR command

```bash
tar cvf - * | ssh -C user@remotehost 'cd kataloog && tar xvf -'
```
