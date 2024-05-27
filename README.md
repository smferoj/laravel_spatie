<!-- Spatie for roll management -->
composer require spatie/laravel-permission
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
 php artisan optimize:clear
 php artisan migrate
 => add HasRoles in usermodel

 php artisan make:seeder RoleSeeder

 // Admin layout 