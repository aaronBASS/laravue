Instructions based on Getting Started section of: https://doc.laravue.dev/guide/#project-structure


## Prerequists

- Laraval 8 requirements [Laravel:Docs](https://laravel.com/docs/8.x/installation)
- Composer
- Git

# Installation

## Create laraval project with composer

Update & Upgrade
```
sudo apt-get update
sudo apt-get upgrade
```

Create project directory
```
sudo mkdir ~/public_html/laravue/
sudo chmod -R a+rw ~/public_html/laravue/
cd ~/public_html/laravue/
```

Configure `Git`

Add to gitconfig file:
```
[user]
	name = username
	email = your@email.com
```


Clone the project with composer
```
sudo composer create-project tuandm/laravue
sudo chown -R www-data:www-data ~/public_html/laravue/
sudo usermod -a -G www-data username
sudo find ~/public_html/laravue/ -type f -exec chmod 644 {} \;
sudo find ~/public_html/laravue/ -type d -exec chmod 755 {} \;
cd laravue
```

Configure database
```
sudo apt install mariadb-server
sudo mysql_secure_installation
sudo apt-get update
```

Enter current password for root (enter for none): `ENTER`
Set root password? [Y/n] `y`
Remove anonymous users? [Y/n] `y`
Disallow root login remotely? [Y/n] `y`
Remove test database and access to it? [Y/n] `y`
Reload privilege tables now? [Y/n] `y`

```sudo mysql -u root -p```

```
CREATE DATABASE laravue;
CREATE USER 'larauser'@'localhost' IDENTIFIED BY 'larapass';
GRANT ALL PRIVILEGES ON laravue.* TO 'larauser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

Configure the .env file
```
sudo nano ~/public_html/laravue/.env
```

Database connection configuration
```
DB_DATABASE=blog
DB_USERNAME=userblog
DB_PASSWORD=passblog
```
Go to laravel project directory and install
```
cd ~/public_html/laravue/
sudo apt-get install php-mbstring php-dom
composer install 
```

Migration and DB seeder (after changing your DB settings in .env)
```
sudo apt-get install php7.4-mysql
php artisan migrate --seed
```

Install dependency
npm install

Build for development
```
sudo npm run dev # or sudo npm run watch
```

Generate php aritisan key
```
php artisan key:generate
```

Start local development server
```
php artisan serve
```

Now you can open Laravel at http://localhost:8000. After login with provided email/password, you should be able to see the Laravue dashboard