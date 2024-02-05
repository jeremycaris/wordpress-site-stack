# Wordpress - Local Development Environment

## First-time setup

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
# if password is set
# mysql -u root -p
```

Install phpmyadmin

```bash
brew install phpmyadmin
cd /usr/local/share/phpmyadmin
valet link
valet secure phpmyadmin
```

## Project setup

```bash
composer install
valet park
valet secure wordpress
```

Optional

```php
/** BE Media from Production */
define( 'BE_MEDIA_FROM_PRODUCTION_URL', 'https://sourcesite.com' );
```