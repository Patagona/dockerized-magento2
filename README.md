# Docker image for Magento 2

Reference: https://github.com/alexcheng1982/docker-magento2

Environments are copied from the same repo.

### Manual Plugin installation

Reference: https://bitbucket.org/patagonalogeecom/magento-2.0/src/master/

To work with this Pricemonitor integration, the extension can be installed in a few minutes 
by going through these following steps:

- Step 1: If previous version is already installed, first remove folder **/<magento-root>/app/code/Patagona**.
- Step 2: Unzip required version located in **Versions/Manual**.
- Step 3: Upload unziped content to root of Magento 2 shop.
  - See the section: How to upload the unziped content to the root of the Magento 2 in this dockerized application?
- Step 4: Disable the cache in admin panel under System >> Cache Management
- Step 5: Enter the following at the command line in Magento 2 root folder (upgrade database):
```
php bin/magento setup:upgrade
```
- Step 6: Enter the following at the command line in Magento 2 root folder (generate dependency map):
```
php bin/magento setup:di:compile
```
- Step 7: Enter the following at the command line in Magento 2 root folder (deploy static content):
```
php bin/magento setup:static-content:deploy
```
- Step 8: Optionally you might need to fix permissions on your Magento installation
- Step 9: After opening Magento 2 admin panel, Pricemonitor icon is shown in the menu.

After installation is over, Pricemonitor configurations can be set by clicking on the Pricemonitor icon on 
the main menu on the left side of the screen.

### How to upload the unziped content to the root of the Magento 2 in this dockerized application?
- Step 1: Upload the zip file in the [custom-plugins](https://github.com/Patagona/docker-magento2/tree/master/custom-plugins)
- Step 2: Run the following command and then copy the unziped content to root of Magento 2 i.e /var/www/html
```
docker exec -it <container-id> /bin/bash
```
