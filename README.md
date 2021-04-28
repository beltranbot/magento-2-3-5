1. build docker images and run containers
    docker-compose up
2. dowload the version of magento you want to use from: https://magento.com/tech-resources/download
3. extract the content in the root of the repository within a /magento directory
4. in the web browser, go to localhost/magento (by default the container will listen to port 80 in the host machine, if you want to change it you can do so in the docker-compose.yml file) and start the installation process.
    - NOTE: when asked for the database host, you should input "mysql"
    - other database settings can be found in the .env file
    - When the installation is finished, do NOT enter the admin yet.
5. install composer dependencies
    - access the container with bash
        docker exec -ti magento_magento_1 /bin/bash
    - within the container, navigate to the magento/ directory
        cd magento
    - install/check composer dependencies
        composer install
6. flush cache
        php bin/magento cache:flush
7. Optionally you can activate developer mode with:
        php bin/magento deploy:mode:set developer
8. Now you can access the magento admin
