## Laravel
- JSON file

# 0.
- (lepj be a mappadba)

# 1. -Létrehozás

composer create-project laravel/laravel Vezeteknev_Keresztnev_Backend
⬇
(szinten lepj be a mappaba)

# 2. -Adatbázis

Xampp

.env -> DB_CONNECTION=mysql
hashtegaek törlés és db név átállítása

# 3. -Táblák

database/migrations

php artisan make:model [nev(egyeszam,nagybetu)] --all
⬇
$table->string("[oszlopnev],length:");
$table->integer("");
$table->date("");
$table->softDeletes();

# 4. -Feltöltés adatokkal

- database/seeders/[nev]Seeder.php

[nev](behivni az osztalyt)::create(
    //bemasolni egy JSON elemet
    // : -> =>
)

- database/seeders/DatabaseSeeder.php

example kikommentelni

#$this->call(
    [
        BookSeeder::class
    ]
)

php artisan migrate
yes

php artisan migrate:fresh --seed

# 5. -lekérdezés GET

php artisan install:api
yes

routes/api.php

Route::resource("/[nev]",[nev]Controller::class);

php artisan route:list

app/http/controllers/[nev]Controller.php

- function index
#$[nev]=[Nev]::all();
return response()->json([$[nev],"msg"=> "lekeres sikeres."]);

# 6. -POST

- function store
#$[nev] = [Nev]::create($request->all());
return response()->json([$[nev] "msg"=>"created succesfully"])

app/http/Requests/store[nev]request.php

- function rules
return[
//pelda:"["title"]" => ["string","max:50","required"]
//date
]

authorize->true

app/http/Requests/update[nev]request.php

- function rules
return[
    //ugyanaz mint fent
]

authorize->true



# 7. -DELETE/UPDATE

- function update
#$[nev]=>update($request->all());
return response()->json([$[nev] "msg"=>"updated succesfully"])

- function destroy
#$[nev]=>delete();
return response()->json([$[nev] "msg"=>"deleted succesfully"])

app/http/models/book.php

- class [nev] extends Model
{
    use SoftDeletes(belinkeltetes)
    protected $fillable = [
        //oszlopnevek
        "title",
        "author",
        stb..
    ]
}

# 8. -Ellenorzes

php artisan serve
127.0.0.1:8000
POSTMAN
uj workspace
uj kollekcio - rest api basics

GET: 127.0.0.1:8000/api/[nev]
POST:127.0.0.1:8000/api/[nev]
Body->x-www-form->bulk edit
//bemasolni az adott elemet es kkiszedni az osszes space-t kis nagybetu erzekeny
bulk edit vege
PUT:127.0.0.1:8000/api/[nev]/[id]
//bemasolni ugyanugy,atirni azt amit kell,id nem fog megvaltozni
DEL:127.0.0.1:8000/api/[nev]/[id]

# 9. -Export
POSTMAN->projekt ...->more->export