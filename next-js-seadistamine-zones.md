# Next.js  seadistamine Zones

1. Loo alamdomeen `frontend`
2. Määra `mod_proxy` sihtpordiks `xxxx`
3. Logi sisse ssh'ga ja liigu vastava projekti kaustani
4. Lisa `ecosystem.config.js` gitignore
5. `git clone <repo-nimi> .`
6. `npm`
7. `npm run build`
8. Loo `ecosystem.config.js` serverisse
    
    ```jsx
    module.exports = {
      apps: [
        {
          name: "project-name-nextjs",
          cwd: "/data01/virt00000/domeenid/www.domain.com/project-folder",
          script: "./node_modules/next/dist/bin/next",
          args: "start",
          autorestart: true,
          watch: false,
    			max_memory_restart: '256M',
    			env: {
            NODE_ENV: 'production',
            PORT: 3000,
    				// Any other env variables, for example:
            GRAPHQL_URL: 'htts://domain.com/graphql',
            WORDPRESS_PREVIEW_SECRET: 000,
            PREVIEW_PW: '****',
            PREVIEW_USER: 'wp_username',
          },
        },
      ],
    };
    ```
    
9. Loo `.env.local` fail serverisse (ehk leiab parema lahenduse ja saaks buildi pm2 läbi jooksutada)
    
    ```jsx
    GRAPHQL_URL=https://admin.xxx.xx/graphql
    ```
    
10. Loo zones uus Node.js rakendus
11. Lisa rakenduse nimi
12. Lisa ecosystemi asukoht `domeenid/www.xxx.xx/frontend/ecosystem.config.js`
13. Käivita rakendus Zonest, sest muidu keegi ei tea kas see seal on, lisaks peale Zone hooldusi võib leht muidu katki minna.

# Peadomeeni suunamine node appile

1. Mine peadomeeni seaded
2. Suuna `mod_proxy` port `30xx` peale?

# Mis üle kontrollida!

1. Kas peadomeen on suunatud zone serverisse
2. Kas Lets Encrypt sertifitkaate pole vaja uuendada peadomeeni jaoks
    1. Kui on vaja uuendada, kustutada peadomeeni vanad sertifikaadid ja teha uued