# BUILD YOUR IMAGES
## Build your database image :
> **$>** docker build --target db -t db-pmb .
![Build1](images/build_db.png)

## Build your app image :
> **$>** docker build --target app -t app-pmb .
![Build2](images/build_app.png)

## Upload your images to your repository
:warning: **replace "localhost:5000" by your registry URL if needed**

> **$>** docker tag db-pmb:latest localhost:5000/db-pmb:latest
**\$>** docker tag app-pmb:latest localhost:5000/app-pmb:latest

![Tag](images/tag_images.png)
> **$>** docker push localhost:5000/db-pmb:latest
**\$>** docker push localhost:5000/app-pmb:latest

![Push](images/push_images.png)

## Deploy your PayMyBuddy instance :
Fill in the startup/db_root_pwd.txt and startup/pmb_pwd.txt with the passwords you will use for managing the DBMS and the app database.
Add the password contained in startup/pmb_pwd.txt in the startup/.env file.
![Creds](images/add_creds.png)

> **$>**  docker compose -f docker-compose.yml up -d
![Deploy](images/deploy.png)

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
