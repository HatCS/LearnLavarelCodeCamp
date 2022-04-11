#Laravel (version Laravel v9.6.0 (PHP v8.1.3) )

## Install component
- composer 
- node
- js
- npm
- laravel 
- npm install vue-loader@^16.2.0 --save-dev --legacy-peer-deps


## Create new project (example:https://www.instagram.com/freecodecamp/)


`~$ laravel new freeCodeGram`
`~/freeCodeGram$ php artisan serve
`

## Generating login flow with make:auth

With Boothstrap
```
composer require laravel/ui --dev
php artisan ui bootstrap --auth

```

## Setting Up the Front End with Node and NPM

Необходимо запустить компиляцию js и css:
npm install && npm run dev



## Migrations and Setting Up SQLite

`vim database/database.sqlite`
`php artisan migrate`

## Designing the UI from Instagram

New directory `svg` в каталоге public проекта
Create new file with format .svg
![](https://i.imgur.com/VIOj5v7.png)

` <div><img src="/svg/freeCodeCampLogo.svg" style="max-height: 25px;"></div>`

![](https://i.imgur.com/023nlOJ.png)

```
<a class="navbar-brand d-flex" href="{{ url('/') }}">
<div><img src="/svg/freeCodeCampLogo.svg" style="height: 25px;"></div>
```
![](https://i.imgur.com/yTsPUQu.png)

![](https://i.imgur.com/1jVP4Kk.png)

![](https://i.imgur.com/6ajVUb6.png)

![](https://i.imgur.com/uDbX0EP.png)

```
<div class="row">
    <div class="col-3">
        <img src="https://www.numerama.com/wp-content/uploads/2012/10/anonymous_emblem.png" alt="">
    </div>
    <div class="col-9">

    </div>
```
![](https://i.imgur.com/iL93JV0.png)

![](https://i.imgur.com/w8pwe0c.png)

![](https://i.imgur.com/hcK4cF8.png)

![](https://i.imgur.com/GpUSBtS.png)

![](https://i.imgur.com/w84x4IG.png)

## Adding Username to the Registration Flow
![](https://i.imgur.com/ncsgZac.png)

Добавим разметку в Phpstorm в файле `"register.blade.php`" удалив require из строки  `autocomplete="username">`

![](https://i.imgur.com/MnErpWm.png)

![](https://i.imgur.com/oDWNvQX.png)

Open in phpStorm file 
`/home/osboxes/freeCodeGram/app/Http/Controllers/Auth/RegisterController.php`

и добавим массив имен пользователей
`   'username' => ['required', 'string', 'email', 'max:255', 'unique:users'],`

![](https://i.imgur.com/f4A6BAP.png)

    /**
     * Create a new user instance after a valid registration.
     *
     * @param  array  $data
     * @return \App\Models\User
     */
    protected function create(array $data)
    {
        return User::create([
            'name' => $data['name'],
            'email' => $data['email'],
            'username' => $data['username'],
            'password' => Hash::make($data['password']),
        ]);
    }
    }


Перейдем к файлу `/home/osboxes/freeCodeGram/database/migrations/2014_10_12_000000_create_users_table.php`

Добавим строку кода:
`$table->string('username')->unique();`

В коммандной строке вводим:
`php artisan `

```
osboxes@osboxes:~/freeCodeGram$ php artisan tinker
Psy Shell v0.11.2 (PHP 8.1.3 — cli) by Justin Hileman
>>> 
```

```
osboxes@osboxes:~/freeCodeGram$ php artisan tinker
Psy Shell v0.11.2 (PHP 8.1.3 — cli) by Justin Hileman
>>> User::all();
[!] Aliasing 'User' to 'App\Models\User' for this Tinker session.
=> Illuminate\Database\Eloquent\Collection {#3854
     all: [
       App\Models\User {#4461
         id: 1,
         name: "Test user",
         email: "r0ckx@yandex.ru",
         email_verified_at: null,
         #password: "$2y$10$sN8HLWhemYgapHmV8sRgaeua3X5yxW8UOAHviMeMW86iGboaUaVnu",
         #remember_token: "UFPiAlgq4kkshVZGjOl19CR1IdcRIeq6gdYBzuzICyCkQ2KZIopup5Q9x7Dk",
         created_at: "2022-04-02 12:22:37",
         updated_at: "2022-04-02 12:22:37",
       },
       App\Models\User {#4462
         id: 2,
         name: "New user",
         email: "test2@test.com",
         email_verified_at: null,
         #password: "$2y$10$zIA5Fs5bGGBFGlkHIrSY0OsFSZhtDU4uyRjBPP.ha7Hc4DHx6kEPm",
         #remember_token: null,
         created_at: "2022-04-04 02:49:57",
         updated_at: "2022-04-04 02:49:57",
       },
     ],
   }
```

В данном случае не отображается поле `username`

`osboxes@osboxes:~/freeCodeGram$ php artisan migrate:fresh`

Данная команда очистить базу данных и создаст заново

Добавим в файл
`/home/osboxes/freeCodeGram/app/Models/User.php`
 строку:
 
 ![](https://i.imgur.com/ZVERfDd.png)

Сделаем так чтобы на странице отображалось не имя (name) а имя пользователя (username):

![](https://i.imgur.com/SA7F49H.png)

Найдем файл макета:
`/home/osboxes/freeCodeGram/resources/views/layouts/app.blade.php`

## Creating the Profiles Controller

Файл маршрутов
`/home/osboxes/freeCodeGram/routes/web.php`
Это место где заргеистрированы все ваши маршруты

`/home/osboxes/freeCodeGram/app/Http/Controllers/HomeController.php`
`/home/osboxes/freeCodeGram/resources/views/home.blade.php`

`$ php artisan help make:controller`

![](https://i.imgur.com/vxIU9DQ.png)

![](https://i.imgur.com/FAyYgwx.png)

## RESTful Resource Controller


[https://laravel.com/docs/5.1/controllers#restful-resource-controllers](https://laravel.com/docs/5.1/controllers#restful-resource-controllers)

![](https://i.imgur.com/VBVS4vV.png)

![](https://i.imgur.com/dzvbp8n.png)

![](https://i.imgur.com/FiJelq6.png)


![](https://i.imgur.com/D5IGqSh.png)

## Passing Data to the View
    $user = \App\Models\User::find($user);
     return view('home', [
         'user' => $user,
     ]);
![](https://i.imgur.com/eaOZpTf.png)

 `<div><h1>{{$user->username}}</h1></div>`

![](https://i.imgur.com/SMmJ4EX.png)

![](https://i.imgur.com/bMY1PPA.png) 


## Adding the Profiles Mode, Migration and Table

`php artisan help make:model`

`$ php artisan make:model Profile -m`

Внесем изменения `/home/osboxes/freeCodeGram/database/migrations/2022_04_05_004918_create_profiles_table.php`

![](https://i.imgur.com/tQUOq8t.png)

```
osboxes@osboxes:~/freeCodeGram$ php artisan migrate
Migrating: 2022_04_05_004918_create_profiles_table
Migrated:  2022_04_05_004918_create_profiles_table (65.99ms)
```


## Adding Eloquent Relationships
Внесем изменения
`/home/osboxes/freeCodeGram/app/Models/Profile.php`

```
class Profile extends Model
{
    public function user()
    {
        return $this->belongsTo(User::class);
    }
}
```

![](https://i.imgur.com/llehK03.png)

`php artisan tinker`

Добавим профиль через командную строку

![](https://i.imgur.com/jKBe27R.png)

```
>>> $user = App\Models\User::find(1);
=> App\Models\User {#3528
     id: 1,
     name: "New user2",
     email: "test4@test.com",
     username: "testUser2",
     email_verified_at: null,
     #password: "$2y$10$EWpOlDWnC.ijFunBgXKLPezUfLwTH0mJi21VnwJK7csVpmQxL5HSO",
     #remember_token: "ggBYdhEpC8fTOsKAaWg5pmatFWDe2PsIy916DPf2P1PiulfqhUe7hGsugORZ",
     created_at: "2022-04-04 03:04:04",
     updated_at: "2022-04-04 03:04:04",
   }
>>> $user->profile
=> App\Models\Profile {#4470
     id: 1,
     user_id: 1,
     title: "Cool Title",
     description: "Description",
     url: null,
     created_at: "2022-04-05 01:25:57",
     updated_at: "2022-04-05 01:25:57",
   }
>>> 
```

![](https://i.imgur.com/HNAlLFz.png)

```
$user->profile
>>> $user->profile->url = 'freecodecamp.org';
>>> $user
>>> $user->save();
>>> $user->push();
=> true
>>> 

```
   

## Fetching the Record From The Database

![](https://i.imgur.com/xJF4P6j.png)

![](https://i.imgur.com/5ecL5bn.png)

![](https://i.imgur.com/4KLgfam.png)


## Adding Posts to the Database & Many To Many Relationship

```
osboxes@osboxes:~/freeCodeGram$ php artisan tinker
Psy Shell v0.11.2 (PHP 8.1.3 — cli) by Justin Hileman
>>> 
osboxes@osboxes:~/freeCodeGram$ php artisan make:model Post -m
Model created successfully.
Created Migration: 2022_04_05_040619_create_posts_table
osboxes@osboxes:~/freeCodeGram$ 
```

![](https://i.imgur.com/BwXiHjR.png)

```
osboxes@osboxes:~/freeCodeGram$ php artisan migrate
Migrating: 2022_04_05_040619_create_posts_table
Migrated:  2022_04_05_040619_create_posts_table (72.14ms)
osboxes@osboxes:~/freeCodeGram$ 
```
Прописыаем in User.php

![](https://i.imgur.com/wNYWPtC.png)

Теперь напишем обратное модели Post


![](https://i.imgur.com/9tK5uOQ.png)



```
 <div class="d-flex justify-content-between" >
    <h1>{{$user->username}}</h1>
    <a href="#">Add new Post</a>
 </div>
```

![](https://i.imgur.com/73CDVdH.png)

![](https://i.imgur.com/SedeHQk.png)

![](https://i.imgur.com/nWv1Qeg.png)

![](https://i.imgur.com/z03YHqB.png)

```
osboxes@osboxes:~/freeCodeGram$ php artisan make:controller PostsController
Controller created successfully.
```

![](https://i.imgur.com/I84fIrD.png)

Создадим директорию posts в views

![](https://i.imgur.com/SXCpLjU.png)

![](https://i.imgur.com/MFFkidx.png)

Создадим `profiles`
И поместим файл `/home/osboxes/freeCodeGram/resources/views/home.blade.php` в него 

![](https://i.imgur.com/2zSpfv5.png)

и переименуем в `index.php`

![](https://i.imgur.com/Vhv57z9.png)

![](https://i.imgur.com/7uHNXDQ.png)

![](https://i.imgur.com/g43AZn5.png)


![](https://i.imgur.com/h1twkDY.png)


```
@extends('layouts.app')

@section('content')
<div class="container">
    <div class="row">
        <div class="col-8 offset-2">
            <div class="form-group row">
                <label for="caption" class="col-md-4 col-form-label text-md-end">Post Caption</label>

                <div class="col-md-6">
                    <input id="caption" type="text" class="form-control @error('caption') is-invalid @enderror" caption="caption" value="{{ old('caption') }}"  autocomplete="caption" autofocus>

                    @error('caption')
                    <span class="invalid-feedback" role="alert">
                                        <strong>{{$errors->first('caption')}}</strong>
                                    </span>
                    @enderror
                </div>
            </div>
        </div>
    </div>
</div>
@endsection
```
![](https://i.imgur.com/9jr934V.png)

![](https://i.imgur.com/vBMGuZw.png)

![](https://i.imgur.com/H0rkFu7.png)

![](https://i.imgur.com/ASdlCxd.png)

![](https://i.imgur.com/Dzki3G2.png)

```
div class="container">
       <form action="/p" enctype="multipart/form-data" method="post">]
        <div class="row">
            <div class="col-8 offset-2">

                <div class="row">
                    <h1>Add New Post</h1>
                </div>
                <div class="form-group row">
                    <label for="caption" class="col-md-4 col-form-label">Post Caption</label>

                    <input id="caption"
                           type="text"
                           class="form-control @error('caption') is-invalid @enderror"
                           caption="caption"
                           value="{{ old('caption') }}"
                           autocomplete="caption" autofocus>

                    @error('caption')
                    <span class="invalid-feedback" role="alert">
                            <strong>{{$errors->first('caption')}}</strong>
                        </span>
                    @enderror
                </div>

                <div class="row pt-3">
                    <label for="image" class="col-md-4 col-form-label">Post Image</label>
                    <input type="file", class="form-control-file" id="image" name="image">

                    @error('image')
                    <span class="invalid-feedback" role="alert">
                            <strong>{{$errors->first('image')}}</strong>
                        </span>
                    @enderror
                </div>

                <div class="row pt-3">
                    <button class="btn btn-primary" style="width:150px">Add New Post</button>
                </div>

            </div>
        </div>
    </form>
</div>
@endsection
```

![](https://i.imgur.com/irFImPT.png)

![](https://i.imgur.com/KukTr1G.png)

![](https://i.imgur.com/ix0flT4.png)

Вышло сообщение о выходе срока страницы
Все дело в csrf

Создаем директиву csrf: @csrf
![](https://i.imgur.com/MRYZqHa.png)

![](https://i.imgur.com/l5FxgGl.png)

![](https://i.imgur.com/YmtnXtQ.png)

![](https://i.imgur.com/psE0KZu.png)

![](https://i.imgur.com/Ut3KS9Q.png)

![](https://i.imgur.com/gpBp0G3.png)


![](https://i.imgur.com/3JXx4Kk.png)


![](https://i.imgur.com/uGhwpaT.png)



## Creating Through a Relationship


![](https://i.imgur.com/4ooknGS.png)


![](https://i.imgur.com/nNqwTBN.png)

![](https://i.imgur.com/Bm5s5Tm.png)

Сделаем так чтобы нельзя было видеть посты других пользователей

![](https://i.imgur.com/MUNdMy3.png)

Промежуточное ПО construct, любые изменения потребуют через авторизацию
Данный отрезок кода защищает маршрут.

## Uploading/Saving the Image to the Project

![](https://i.imgur.com/bhrgfs8.png)


![](https://i.imgur.com/TfT47tw.png)

Все загруженные файлы храняться в каталоге:

![](https://i.imgur.com/BlLQWSy.png)

```
osboxes@osboxes:~/freeCodeGram$ php artisan storage:link
The [/home/osboxes/freeCodeGram/public/storage] link has been connected to [/home/osboxes/freeCodeGram/storage/app/public].
The links have been created.
```
![](https://i.imgur.com/rDlJhV0.png)


![](https://i.imgur.com/8rr14qq.png)


![](https://i.imgur.com/OFl3Pql.png)


![](https://i.imgur.com/Oc4ry08.png)


Теперь удалим все посты ранее сделанные:

```
osboxes@osboxes:~/freeCodeGram$ php artisan tinker
Psy Shell v0.11.2 (PHP 8.1.3 — cli) by Justin Hileman
>>> Post::truncate();
[!] Aliasing 'Post' to 'App\Models\Post' for this Tinker session.
=> Illuminate\Database\Eloquent\Builder {#3536}
```

Сделаем функционирование Add post

![](https://i.imgur.com/tDiUBT0.png)

![](https://i.imgur.com/c7C2Pn9.png)

Изменим порядок добавления постов:

![](https://i.imgur.com/nwml6ip.png)

Изменим число постов в форме:

![](https://i.imgur.com/TXYTiCe.png)

![](https://i.imgur.com/6VZEWCr.png)


## Resizing Images with Intervention Image PHP Library

```
$ composer require intervention/image
```
![](https://i.imgur.com/P6rKrBJ.png)

![](https://i.imgur.com/yfaA579.png)

![](https://i.imgur.com/Grd44dD.png)

## Route Model Binding
Пропишем маршруты в web.php


![](https://i.imgur.com/RDVbDHz.png)


В PostController создаем метод show():

![](https://i.imgur.com/6wPfkt5.png)


![](https://i.imgur.com/uBNA7n0.png)

Проверим если введем лишнее


![](https://i.imgur.com/Uk78Npr.png)


![](https://i.imgur.com/Kj5CHgi.png)


![](https://i.imgur.com/SYWoNtD.png)


Теперь имеется возможность переходить в посты при нажатии на картинку

![](https://i.imgur.com/2eS5I4V.png)


## Editing the Profile


![](https://i.imgur.com/Hq0nGOG.png)


![](https://i.imgur.com/GY5ifS5.png)


![](https://i.imgur.com/rJGh1Q3.png)


![](https://i.imgur.com/bNBABtj.png)



![](https://i.imgur.com/Bs9kUOq.png)

![](https://i.imgur.com/yPYCGN8.png)


![](https://i.imgur.com/EogJoCa.png)


![](https://i.imgur.com/sD10K76.png)

Добавим информацию:
`/home/osboxes/freeCodeGram/resources/views/profiles/edit.blade.php`

```
@extends('layouts.app')

@section('content')
<div class="container">

    <form action="/profile/{{ $user->id }}" enctype="multipart/form-data" method="post">
        <div class="row">
            <div class="col-8 offset-2">
                @csrf
                @method('PATCH')

                <div class="row">
                    <h1>Edit Profile</h1>
                </div>
                <div class="form-group row">
                    <label for="title" class="col-md-4 col-form-label">Title</label>

                    <input id="title"
                           type="text"
                           class="form-control @error('title') is-invalid @enderror"
                           name = "titlse"
                           value="{{ old('title') ?? $user->profile->title}}"
                           autocomplete="title" autofocus>

                    @error('title')
                    <span class="invalid-feedback" role="alert">
                            <strong>{{$errors->first('title')}}</strong>
                        </span>
                    @enderror
                </div>

                <div class="form-group row">
                    <label for="description" class="col-md-4 col-form-label">Description</label>

                    <input id="description"
                           type="text"
                           class="form-control @error('description') is-invalid @enderror"
                           name = "description"
                           value="{{ old('description')?? $user->profile->description }}"
                           autocomplete="description" autofocus>

                    @error('description')
                    <span class="invalid-feedback" role="alert">
                            <strong>{{$errors->first('description')}}</strong>
                        </span>
                    @enderror
                </div>
                <div class="form-group row">
                    <label for="url" class="col-md-4 col-form-label">URL</label>

                    <input id="url"
                           type="text"
                           class="form-control @error('url') is-invalid @enderror"
                           name = "url"
                           value="{{ old('url') ?? $user->profile->url}}"
                           autocomplete="url" autofocus>

                    @error('url')
                    <span class="invalid-feedback" role="alert">
                            <strong>{{$errors->first('url')  }}</strong>
                        </span>
                    @enderror
                </div>

                <div class="row pt-3">
                    <label for="image" class="col-md-4 col-form-label">Profile Image</label>
                    <input type="file", class="form-control-file" id="image" name="image">

                    @error('image')
                    <strong>{{$errors->first('image')}}</strong>
                    @enderror
                </div>

                <div class="row pt-3">
                    <button class="btn btn-primary" style="width:150px">Save Profile</button>
                </div>

            </div>
        </div>
    </form>

</div>
@endsection
```

![](https://i.imgur.com/IN5qHpJ.png)


![](https://i.imgur.com/ULdGcxt.png)


![](https://i.imgur.com/mTJevn4.png)



![](https://i.imgur.com/GfGV5vT.png)


Добавим уровень защиты от редактирования при логировании гостем


![](https://i.imgur.com/lLBkrj6.png)

## Restricting/Authorizing Actions with a Model Policy

Для этого создаем политику для профиля

`$ php artisan help make:policy`

`~/freeCodeGram$ php artisan make:policy ProfilePolicy -m Profile`

Создан следующий файл:
`/home/osboxes/freeCodeGram/app/Policies/ProfilePolicy.php`

Изменим метод:
 ```
 public function update(User $user, Profile $profile)
    {
        return $user->id==$profile->user_id;
    }
```

Изменим в файле `ProfileController.php` метод
    ```
public function edit(User $user)
    {
        $this->authorize('update', $user->profile;
        return view('profiles.edit', compact('user'));
    }
```

![](https://i.imgur.com/AlsU0n1.png)

 ```
 в index.blade.php добавим

```
   @can ('update', $user->profile)
                <a href="/profile/{{ $user->id }}/edit">Edit profile</a>
            @endcan
```
![](https://i.imgur.com/EyPCKPU.png)


![](https://i.imgur.com/Jjix2Sr.png)


![](https://i.imgur.com/aGWVnTr.png)



## Editing the Profile Image

![](https://i.imgur.com/8aBKb8l.png)

![](https://i.imgur.com/fFD6TqC.png)

![](https://i.imgur.com/vOq4eSI.png)


![](https://i.imgur.com/AvlSWrB.png)

Добавим поле image в таблицу create.profile.table

![](https://i.imgur.com/v5Lmy7u.png)

```
~/freeCodeGram$ php artisan  migrate:fresh
Dropped all tables successfully.
Migration table created successfully.
Migrating: 2014_10_12_000000_create_users_table
Migrated:  2014_10_12_000000_create_users_table (103.83ms)
Migrating: 2014_10_12_100000_create_password_resets_table
Migrated:  2014_10_12_100000_create_password_resets_table (24.06ms)
Migrating: 2019_08_19_000000_create_failed_jobs_table
Migrated:  2019_08_19_000000_create_failed_jobs_table (24.87ms)
Migrating: 2019_12_14_000001_create_personal_access_tokens_table
Migrated:  2019_12_14_000001_create_personal_access_tokens_table (53.55ms)
Migrating: 2022_04_05_004918_create_profiles_table
Migrated:  2022_04_05_004918_create_profiles_table (22.78ms)
Migrating: 2022_04_05_040619_create_posts_table
Migrated:  2022_04_05_040619_create_posts_table (36.15ms)
```

## Automatically Creating A Profile Using Model Events

Создадим нового пользователя, и оказалось у нас не создается новый профиль пользователя.


![](https://i.imgur.com/iIjOR8B.png)

```
/freeCodeGram$ php artisan  migrate:fresh
Dropped all tables successfully.
Migration table created successfully.
```

![](https://i.imgur.com/XNTm5l1.png)


```
@extends('layouts.app')

@section('content')
<div class="container">

    <div class="row">
        <div class="col-8">
            <img src="/storage/{{ $post->image }}" class="w-100">
        </div>
        <div class="col-4">
            <div class="d-flex align-items-center">
                <div class="p-1">
                    <img src="/storage/{{ $post->user->profile->image}}" class="rounded-circle w-100" style="max-width: 40px;">
                </div>
                <div>
                    <div class="fw-bold">
                        <a href="/profile/{{ $post->user->id}}">
                            <span class="text-dark"> {{ $post->user->username}}
                        </a> 
                        <a href="#" class="p-lg-3"> follow</a>
                    </div>
                </div>
            </div>

            <hr>

            <p> <span div class="fw-bold">
                    <a href="/profile/{{ $post->user->id}}">
                          <span class="text-dark"> {{ $post->user->username}}
                    </a></span> {{ $post->caption }}</p>
        </div>
    </div>

</div>
@endsection
```



## Default Profile Image

![](https://i.imgur.com/fiEY3SO.png)


![](https://i.imgur.com/lVvfHnH.png)


![](https://i.imgur.com/dN8uJfT.png)



![](https://i.imgur.com/EdxSeEc.png)


![](https://i.imgur.com/DXho6e7.png)


![](https://i.imgur.com/gpJNIo0.png)

Тем самым можно войти как пользователь, редактировать профиль, и добалять сообщения.

## Follow/Unfollow Profiles Using a Vue.js Component

![](https://i.imgur.com/fEBfqkn.png)


![](https://i.imgur.com/2ThOB6L.png)


rename in /home/osboxes/freeCodeGram/resources/js/components/FollowButton.vue

change file /home/osboxes/freeCodeGram/vendor/laravel/ui/src/Presets/vue-stubs/app.js


![](https://i.imgur.com/1kqw2SY.png)


Cut                   ` <button class="btn btn-primary ms-4">Follow</button>` with file `index.blade.php`

Paste in app.js

![](https://i.imgur.com/HGhKfS1.png)


change webpack.mix.js

```
mix.js('resources/js/app.js', 'public/js')
    .vue()
    .sass('resources/sass/app.scss', 'public/css');
```

composer require laravel/ui
php artisan ui vue
npm install && npm run dev

yarn add vue@3.2.26
npm i vue@3.2.26

npm run watch // компиляция в реальном времени

Необходимо создать связь между 2мя пользователями

Проверка на работоспособность:

![](https://i.imgur.com/oYUAjfF.png)


![](https://i.imgur.com/kUMsZun.png)


![](https://i.imgur.com/Y7hM6pp.png)


Create new controller

```
/freeCodeGram$ php artisan make:controller FollowsController
Controller created successfully.
```

![](https://i.imgur.com/jU9vHZx.png)


![](https://i.imgur.com/QsY8P4m.png)


![](https://i.imgur.com/Wm23uNL.png)


![](https://i.imgur.com/w7MhrkI.png)


![](https://i.imgur.com/NP4GNNf.png)


![](https://i.imgur.com/E2kJ9wf.png)

## Many To Many Relationship

Необходимо создать промежуточную таблицу:

```
~/freeCodeGram$ php artisan make:migration creates_profile_user_pivot_table --create profile_user
Created Migration: 2022_04_09_115713_creates_profile_user_pivot_table
```
![](https://i.imgur.com/5P4Rvxb.png)

```

~/freeCodeGram$ php artisan migrate
Migrating: 2022_04_09_115713_creates_profile_user_pivot_table
Migrated:  2022_04_09_115713_creates_profile_user_pivot_table (38.01ms)
```

Затем изменим пользовательскую модель user.php

![](https://i.imgur.com/0DQOG5n.png)


Также изменим в профиле:

![](https://i.imgur.com/YqLLwtO.png)

![](https://i.imgur.com/pmKk6K1.png)

![](https://i.imgur.com/UR8zujx.png)


```
osboxes@osboxes:~/freeCodeGram$ php artisan tinker
Psy Shell v0.11.2 (PHP 8.1.3 — cli) by Justin Hileman
>>> $user = User::find(1);
[!] Aliasing 'User' to 'App\Models\User' for this Tinker session.
=> App\Models\User {#3864
     id: 1,
     name: "Test user 2",
     email: "test2@test.com",
     username: "testUser2",
     email_verified_at: null,
     #password: "$2y$10$pme0zJapYx/71XoIs3tahe8cPfHNodplc8cd3S0HGuZSoynyRUkii",
     #remember_token: null,
     created_at: "2022-04-08 08:44:45",
     updated_at: "2022-04-08 08:44:45",
   }
>>> $user = User::find(2);
=> App\Models\User {#4477
     id: 2,
     name: "Test user 3",
     email: "test3@test.com",
     username: "testUser3",
     email_verified_at: null,
     #password: "$2y$10$.M5HxZw4GBS01vBKmG9MdeGh0sep1fu/jH/57.a.CJcYgsOVa.yam",
     #remember_token: "FNl97kq9oX2uwXcKYoJDLnKrFigF2JdAZLCZkL9yQNGZhfAevVPHNbv93eHg",
     created_at: "2022-04-08 09:18:05",
     updated_at: "2022-04-08 09:18:05",
   }
>>> $user->following
=> Illuminate\Database\Eloquent\Collection {#4472
     all: [],
   }
```
Нажмем дважды по кнопке follow

```
>>> $user->fresh()->following
=> Illuminate\Database\Eloquent\Collection {#4489
     all: [
       App\Models\Profile {#4482
         id: 2,
         user_id: 2,
         title: "testUser3",
         description: "Very Cool Description",
         url: "http://freecodecamp.org",
         image: "profile/Ij0pNg6CUNj0Win7LTUFd60HYbOW5KArslA4y39A.jpg",
         created_at: "2022-04-08 09:18:05",
         updated_at: "2022-04-08 09:18:41",
         pivot: Illuminate\Database\Eloquent\Relations\Pivot {#4474
           user_id: 2,
           profile_id: 2,
         },
       },
     ],
   }
```
```
$user = User::find(1);
=> App\Models\User {#4496
     id: 1,
     name: "Test user 2",
     email: "test2@test.com",
     username: "testUser2",
     email_verified_at: null,
     #password: "$2y$10$pme0zJapYx/71XoIs3tahe8cPfHNodplc8cd3S0HGuZSoynyRUkii",
     #remember_token: null,
     created_at: "2022-04-08 08:44:45",
     updated_at: "2022-04-08 08:44:45",
   }
>>> $user->following
=> Illuminate\Database\Eloquent\Collection {#4503
     all: [],
   }
>>> 
```

Визуально изменим статус кнопки follow

![](https://i.imgur.com/AQ94KS3.png)


![](https://i.imgur.com/InTGImU.png)


![](https://i.imgur.com/RS1BGnO.png)



![](https://i.imgur.com/j9zdXjj.png)



![](https://i.imgur.com/6zi6Qtj.png)


![](https://i.imgur.com/EyUSDef.png)


![](https://i.imgur.com/Dhb0EGh.png)


## Calculating Followers Count and Following Count

![](https://i.imgur.com/VKMvTaK.png)

![](https://i.imgur.com/LXrhSam.png)


## Laravel Telescope

`~/freeCodeGram$ composer require laravel/telescope`

`~/freeCodeGram$ php artisan telescope:install   `

```
~/freeCodeGram$ php artisan migrate
```
http://localhost:8000/telescope/redis


## Showing Posts from Profiles The User Is Following

![](https://i.imgur.com/z4r8sik.png)

Изменим на переход в начало 127.0.0.1:8000

![](https://i.imgur.com/PTAT7tN.png)

![](https://i.imgur.com/m4zNJzC.png)


![](https://i.imgur.com/E7Tc5so.png)


Create new file index.blade.php in directory:
`/home/osboxes/freeCodeGram/resources/views/posts/`

![](https://i.imgur.com/Za1LKhB.png)


![](https://i.imgur.com/ppe1IMo.png)



## Pagination with Eloquent

Выведим только первые 5 сообщений:

![](https://i.imgur.com/DtDjB92.png)


![](https://i.imgur.com/mWqh4Qv.png)


## N + 1 Problem & Solution

```
:~/freeCodeGram$ php artisan telescope:clear
Telescope entries cleared!
```

## Make Use of Cache for Expensive Query

![](https://i.imgur.com/KXqoYzl.png)



![](https://i.imgur.com/mfdWAD5.png)



![](https://i.imgur.com/KEhXTSD.png)


## Sending Emails to New Registered Users

Autorize in:
https://mailtrap.io

![](https://i.imgur.com/OnNlI47.png)


Copy data in .env:

![](https://i.imgur.com/7CzyK9G.png)

```
sboxes@osboxes:~/freeCodeGram$ php artisan help make:mail
Description:
  Create a new email class

Usage:
  make:mail [options] [--] <name>

Arguments:
  name                       The name of the class

Options:
  -f, --force                Create the class even if the mailable already exists
  -m, --markdown[=MARKDOWN]  Create a new Markdown template for the mailable [default: false]
      --test                 Generate an accompanying PHPUnit test for the Mail
      --pest                 Generate an accompanying Pest test for the Mail
  -h, --help                 Display help for the given command. When no command is given display help for the list command
  -q, --quiet                Do not output any message
  -V, --version              Display this application version
      --ansi|--no-ansi       Force (or disable --no-ansi) ANSI output
  -n, --no-interaction       Do not ask any interactive question
      --env[=ENV]            The environment the command should run under
  -v|vv|vvv, --verbose       Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
osboxes@osboxes:~/freeCodeGram$ php artisan make:mail NewUserWelcomeMail -m emails.welcome-email
Mail created successfully.
```

![](https://i.imgur.com/BhUlRR1.png)

![](https://i.imgur.com/T1peXtD.png)


![](https://i.imgur.com/bIlmzad.png)

Теперь займемся отправкой электронного письма

![](https://i.imgur.com/W2jrJSg.png)

![](https://i.imgur.com/D7PyhV1.png)








⌨️ (4:21:51) Wrapping Up




⌨️ (4:22:37) Closing Remarks & What's Next In your Learning



