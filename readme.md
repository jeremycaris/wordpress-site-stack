# Wordpress Site Stack

## MacOS LEMP stack + mailhog

Install homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install php

```bash
php install
```

Install laravel valet

```bash
composer global require laravel/valet
# Include in PATH
nano ~/.zsh
export PATH="$PATH:~/.composer/vendor/bin"
source ~/.zsh
# alt .bash_profile
valet install
```

Install mysql

```bash
brew install mysql
brew services start mysql
mysql -u root
ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';

# If password is set:
# mysql -u root -p

CREATE DATABASE wp_wordpress;
```

*Creating Database for WordPress - [Reference](https://developer.wordpress.org/advanced-administration/before-install/creating-database/)*

Install phpmyadmin

```bash
brew install phpmyadmin
cd /usr/local/share/phpmyadmin
valet link
valet secure phpmyadmin
```

*Access at https://phpmyadmin.test/, Username: root | Password: password*

Install mailhog

```bash
brew update && brew install mailhog

# Run as a background service launched automatically at login 
brew services start mailhog

# Edit the postfix config file
sudo nano /etc/postfix/main.cf

# Add to the end of the file
# For MailHog
myhostname = localhost
relayhost = [localhost]:1025

# Restart postfix
sudo postfix stop && sudo postfix start

# Send a test message, then check mailhog
date | mail -s "Test Email" your_email@gmail.com
```

*Access mailhog at http://localhost:8025/ (Default: http://0.0.0.0:8025/)*



<br>

## Project setup

```bash
composer install
valet park
valet secure wordpress
```

*Access at https://wordpress.test/, Username: admin | Password: admin*

Optional wp-config.php setting

```php
/** BE Media from Production */
define( 'BE_MEDIA_FROM_PRODUCTION_URL', 'https://sourcesite.com' );
```
