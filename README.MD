# 🌳 Web Development Environment
This is my personal environment of containers used in PHP development basically.  
If you noticed already, it is a rip off Laradock, but I thought Laradock was way complicated to use, and I want it something to just pull out of somewhere and start using, then I created this and now I'm sharing with anyone who wants it too.  

## 🧰 How To Use It  
You can make a fork, pull or just download this project.  
The structure must be the following:
```
.
├── Projects
│   ├── webdev
│   ├── project1
│   ├── project2
│   ├── project3
│   └── project4
```

All your projects will be linked as a volume in the containers.  

So, there is 1 Nginx container which will serve all your websites, you'll need to configure every website with a .conf file placed inside `./nginx/sites-available/`. There are various examples inside `./nginx/sites-available/`.  

After the project it's in your local machine, run the following commands:  
```
# Copy the example environment variables...
cp .env.example .env

# After executing this command, configure your [createdb.sql] file to create your databases...
cp ./mysql/8.0/docker-entrypoint-initdb.d/createdb.sql.example ./mysql/8.0/docker-entrypoint-initdb.d/createdb.sql

# Build and run the containers...
docker-compose up -d

# Start coding!
```

### PHP  
There are 2 containers for each PHP version (Will add it more), one is the FPM for Nginx, and the other is a CLI which the container keeps running without executing anything. You can use this one for installing dependencies with Composer, or executing background functions.  

### MySQL  
To use MySQL pay attention to the variables in the .env, the default user is "default" with password "secret", you can edit those if you wish.  
To create your databases copy the file `./mysql/8.0/docker-entrypoint-initdb.d/createdb.sql.example` to the same place as `createdb.sql`. Running the container for the first time it will auto-execute this file to create all the databases. Read the example for more info.  

### MariaDB
Same thing as MySQL.

### Redis  
There is no secret with this one, it's all default.  
The password it's in the .env file.  

### PostgreSQL
🚧 WIP.

### Node  
I'm currently working on it...  
It does have a Node container, but Angular it's still quite wacky.  

### Email  
Will be adding an email service soon...

## 🤝 Want to Contribute?  
Just create a pull request, no big deal.  
