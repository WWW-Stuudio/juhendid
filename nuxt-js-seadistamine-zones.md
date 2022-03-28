# Nuxt.js  seadistamine Zones

1. Loo alamdomeen `frontend`
2. Määra `mod_proxy` sihtpordiks `3000`
3. Logi sisse ssh'ga ja liigu kaustani frontend
4. Lisa `ecosystem.config.js` gitignore
5. `git clone <repo-nimi> .`
6. `yarn`
7. `yarn build`
8. Loo `ecosystem.config.js` serverisse
    
    ```jsx
    module.exports = {
      apps: [
        {
          name: 'application-name',
          cwd: '/data01/virtXXXXX/domeenid/www.xxx.ee/frontend',
          exec_mode: 'cluster',
          instances: 'max',
          script:
            '/data01/virtXXXXX/domeenid/www.xxx.ee/frontend/node_modules/nuxt/bin/nuxt.js',
          args: 'start',
    	env: {
    		BASE_URL: 'https://admin.xxx.ee/index.php/wp-json/www-api/v1',
    		NUXT_PORT: 3000
    	}
        }
      ]
    }
    ```
    
9. Loo `.env` fail serverisse (ehk leiab parema lahenduse ja saaks buildi pm2 läbi jooksutada)
    
    ```jsx
    BASE_URL=https://admin.xxx.ee/index.php/wp-json/www-api/v1
    ```
    
10. Loo zones uus Node.js rakendus
11. Lisa rakenduse nimi
12. Lisa ecosystemi asukoht `domeenid/www.domeen.ee/frontend/ecosystem.config.js`
13. Lisa mälukasutuseks ~256MB
14. Käivita rakendus Zonest, sest muidu keegi ei tea kas see seal on, lisaks peale Zone hooldusi võib leht muidu katki minna.

# Peadomeeni suunamine node appile

1. Mine peadomeeni seaded
2. Suuna `mod_proxy` port `3000` peale?

# Mis üle kontrollida!

1. Kas peadomeen on suunatud zone serverisse
2. Kas Lets Encrypt sertifitkaate pole vaja uuendada peadomeeni jaoks
    1. Kui on vaja uuendada, kustutada peadomeeni vanad sertifikaadid ja teha uued