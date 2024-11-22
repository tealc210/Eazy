# BUILD YOUR IMAGES
## Build your database image :
docker build --target db -t db-pmb .

## Launch a database container :
docker run --name db-pmb db-pmb

## Build your app image :
docker build --target packager --build-arg db_pwd=<YOUR_DB_PASSWORD_HERE> --build-arg db_instance=<YOUR_DB-PMB_CONTAINER_IP> -t app-pmb .

## Remove the database container:
docker stop db-pmb && docker rm db-pmb

## Upload your images to your repository
replace "localhost:5000" by your registry URL if needed):

docker tag pmb-db:latest localhost:5000/pmb-db:latest
docker tag pmb-app:latest localhost:5000/pmb-app:latest
docker push localhost:5000/pmb-db:latest
docker push localhost:5000/pmb-app:latest

## Deploy your PayMyBuddy instance :
Fill in the db_root_pwd.txt and pmb_pwd.txt with the passwords used previously.
docker compose -f docker-compose.yml up -d

# Enjoy your application
![Home](images/pmb_home.png)
![Connection](images/pmb_connect.png)
![Transaction](images/pmb_transaction.png)
![Balance](images/pmb_balance.png)
