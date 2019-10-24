# Sqlite-to-Mongdb

1. edit .env file:
  DB_CONNECTION = mongodb /
  MONGO_DB_HOST=127.0.0.1 /
  MONGO_DB_PORT=27017/
  MONGO_DB_DATABASE=mongocrud/
  MONGO_DB_USERNAME=/
  MONGO_DB_PASSWORD=
1. in app/config/database.php:/
  Add in connections:/
  'mongodb' => [ /
'driver' => 'mongodb',/
'host' => env('MONGO_DB_HOST', 'localhost'),/
'port' => env('MONGO_DB_PORT', 27017),/
'database' => env('MONGO_DB_DATABASE'),/
'username' => env('MONGO_DB_USERNAME'),/
'password' => env('MONGO_DB_PASSWORD'),/
'options' => []/
],
1.
