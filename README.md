# Install dependencies
composer install
cp .env.example .env
php artisan key:generate

# Start environment
./vendor/bin/sail up -d

# Run migrations & seeders
./vendor/bin/sail artisan migrate --seed

# Install JS dependencies & run dev server
./vendor/bin/sail npm install
./vendor/bin/sail npm run dev

# Run tests
./vendor/bin/sail artisan test

# Static analysis
./vendor/bin/sail php ./vendor/bin/phpstan analyse

# Code style check
./vendor/bin/sail php ./vendor/bin/pint
