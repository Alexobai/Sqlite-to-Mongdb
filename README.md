# Sqlite-to-Mongdb

1. edit .env file:  
  DB_CONNECTION = mongodb   
  MONGO_DB_HOST=127.0.0.1   
  MONGO_DB_PORT=27017  
  MONGO_DB_DATABASE=mongocrud  
  MONGO_DB_USERNAME=  
  MONGO_DB_PASSWORD=  
1. in app/config/database.php:  
  Add in connections:  
  'mongodb' => [   
'driver' => 'mongodb',  
'host' => env('MONGO_DB_HOST', 'localhost'),  
'port' => env('MONGO_DB_PORT', 27017),  
'database' => env('MONGO_DB_DATABASE'),  
'username' => env('MONGO_DB_USERNAME'),  
'password' => env('MONGO_DB_PASSWORD'),  
'options' => []  
],
1. do: composer require jenssegers/mongodb
1. add: Jenssegers\Mongodb\MongodbServiceProvider::class in config/app/php
1. change User model:  
use Illuminate\Notifications\Notifiable;  
use Jenssegers\Mongodb\Auth\User as Authenticatable;  

class User extends Authenticatable {   
use Notifiable;  
protected $connection = 'mongodb';
1. change other models
1. as mongodb do not have bigIncrements or unsinged etc,  
change the table to something like this:  
__$table->index('id');  
$table->unique('email');__
1. change ->id to ->_id
1. when using relation to create data in table, do not call the other table directly but do create method and make the user_id = _id
