# BUILD YOUR IMAGES
## Build your database image :
> **$>** docker build --target db -t db-pmb .

## Build your app image :
> **$>** docker build --target app -t app-pmb .

## Upload your images to your repository
:warning: **replace "localhost:5000" by your registry URL if needed**

> **$>** docker tag pmb-db:latest localhost:5000/pmb-db:latest
**\$>** docker tag pmb-app:latest localhost:5000/pmb-app:latest
**\$>** docker push localhost:5000/pmb-db:latest
**\$>** docker push localhost:5000/pmb-app:latest

## Deploy your PayMyBuddy instance :
Fill in the startup/db_root_pwd.txt and startup/pmb_pwd.txt with the passwords you will use for managing the DBMS and the app database.
Add the password contained in startup/pmb_pwd.txt in the startup/.env file.
> **$>**  docker compose -f docker-compose.yml up -d

# Enjoy your application
Take a look at http://<YOUR_DEPLOYMENT_IP>:8008
### Here is a whole new world
![Home](images/pmb_home.png)
### You can connect to your buddies...
![Connection](images/pmb_connect.png)
### Pay them (and get paid :smiley: )
![Transaction](images/pmb_transaction.png)
### Make deposits or get your money
![Balance](images/pmb_balance.png)
