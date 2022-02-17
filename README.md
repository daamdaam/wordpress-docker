# Requirements
Docker needs to be installed

docker-compose needs to be installed

Extract the database zip file located in the db_backup folder

Update the docker-compose by setting the dbnames to that of the name of the database backed up

# CLI Commands 
run docker image on CLI:
docker-compose down --volumes && docker-compose up

## to access the Wordpress files:
docker exec -it site /bin/bash

## to access the database:
docker exec -it db /bin/bash

## to copy files from docker instance to host (local machine)
docker cp site:/var/www/html/wp-content/index.php . (this example copies the index.php file from the wp-content folder into the cwd on host)

## to remove containers for each
Sometimes you may find you need to remove the containers as you want to rebuild, you can do this with the below:

docker container rm db (removes the db container)
docker container rm site (removes the site container)

## to tidy up
run the command:
docker container rm db site -f

to remove the containers for db and site, incase you want to create a new set of containers with the same tag (maybe you want to run another wordpress docker instance :).

# troubleshooting

## 1
if an issue with docker service not starting, try running:
sudo chown $(whoami):$(whoami) /var/run/docker.sock

## 2
The SQL siteurl and sitepath(?) may need changing from the full url to localhost.


