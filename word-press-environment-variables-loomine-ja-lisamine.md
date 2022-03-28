# WordPress environment variables loomine ja lisamine

Enne alustamist veendu, et sinu arvutisse on installitud  [Composer](https://getcomposer.org/) *dependency management* tööriist.

1. Ava WordPress oma arvutis
2. Loo WordPress juurkataloogi `composer.json` fail.
3. Lisa faili `{}` märgendid ja salvesta fail.
4. WordPressi juurkataloogis kirjuta käsureale `composer require vlucas/phpdotenv` ja vajuta enter.
5. Loo `.env` fail WordPress juurkataloogi
6. Lisa `.env` faili järgmised read ja täida need vastavalt sinu seadistustega:
    
    ```json
    DB_NAME=andmebaasi_nimi
    DB_USER=andmebaasi_kasutajanimi
    DB_PASSWORD=andmebaasi_kasutaja_parool
    DB_HOST=andmebaasi_host
    ```
    
7. Ava `wp-config.php` fail.
8. Lisa faili algusesse järgmised read:
    
    ```php
    if ( file_exists(__DIR__ . '/vendor/autoload.php') ) {
    	require_once __DIR__ . '/vendor/autoload.php';
    	$dotenv = Dotenv\Dotenv::createImmutable(__DIR__);
    	$dotenv->load();
    }
    ```
    
9. Lisa .env muutujad  wp-config.php faili:
    
    ```php
    /** The name of the database for WordPress */
    define( 'DB_NAME', $_ENV['DB_NAME'] );
    
    /** MySQL database username */
    define( 'DB_USER', $_ENV['DB_USER'] );
    
    /** MySQL database password */
    define( 'DB_PASSWORD', $_ENV['DB_PASSWORD'] );
    
    /** MySQL hostname */
    define( 'DB_HOST', $_ENV['DB_HOST'] );
    ```
    
10. Tee `git commit` ja `git push main`.
11. Logi läbi SSH sisse virtuaalserverisse.
12. Liigu juurkataloogi, kus WordPress asub või asuma hakkab.
13. Tee `git pull`.
14. Kirjuta käsureale `composer install` ja vajuta enter.
15. Lisa serverisse .env fail ja täida `DB_NAME, DB_USER, DB_PASSWORD, DB_HOST` serveri andmetega.

### PS!

Lisaküsimus, millele ma vastust veel ei tea on see, et kas *Authentication Unique Keys and Salts* muutujad peaksid ka olema .env failis või mitte*.* Endale justkui tundub, et vist turvalisuse kaalutlustel peaks?!