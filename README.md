1. build docker images and run containers
    docker-compose up
2. in the web browser, go to localhost/magento and start the installation process.
    - NOTE: when asked for the database host, you should input "mysql"
    - other database settings can be found in the .env file
    - When the installation is finished, do NOT enter the admin yet.
3. install composer depenencies
    docker-compose run composer composer install
4. flush cache
    docker-compose run composer php bin/magento cache:flush
5. Optionally you can activate developer mode with:
    php bin/magento deploy:mode:set developer
