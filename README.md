Instructions based on Getting Started section of : https://doc.laravue.dev/guide/#project-structure


### Prerequists

- Laraval 8 requirements [Laravel:Docs](https://laravel.com/docs/8.x/installation)
- Composer
- Git

## Installation

#### Create laraval project with composer

Setup Git

Clone the project with composer
```composer create-project tuandm/laravue
cd laravue```

Change permissions
```sudo chmod -R a+rw ~/public_html/laravue/```

Configure database
```sudo apt install mariadb-server```

```sudo mysql_secure_installation```

Enter current password for root (enter for none): `ENTER`
Set root password? [Y/n] `y`
Remove anonymous users? [Y/n] `y`
Disallow root login remotely? [Y/n] `y`
Remove test database and access to it? [Y/n] `y`
Reload privilege tables now? [Y/n] `y`

```sudo mysql -u root -p```

```CREATE DATABASE blog;
CREATE USER 'userblog'@'localhost' IDENTIFIED BY 'passblog';
GRANT ALL PRIVILEGES ON blog.* TO 'userblog'@'localhost';
FLUSH PRIVILEGES;
EXIT;```

Configure the .env file
```sudo nano ~/public_html/blog/.env```

Database connection configuration
```DB_DATABASE=blog
DB_USERNAME=userblog
DB_PASSWORD=passblog```

Migration and DB seeder (after changing your DB settings in .env)
```php artisan migrate --seed```

Build for development
```sudo npm run dev # or sudo npm run watch```

Start local development server
```php artisan serve```

Now you can open Laravel at http://localhost:8000. After login with provided email/password, you should be able to see the Laravue dashboard