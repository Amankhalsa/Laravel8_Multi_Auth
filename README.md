#Laravel Multi Auth system for user and Admin
====================================
#Some stepsMUlti Auth Steps:-
====================================
*1st Make Admin Controller
=====================	
*2nd make Model Class admin by using below commands
----------------
	For Controller:-
----------------
	

		php artisan make:Controller AdminController
----------------
for ModelL:- 
----------------
		php artisan make:Model Admin -m
=====================
*3rd Copy all data from user migration file and


			paste into admin migration file like this below code:
            $table->id();
            $table->string('name');
            $table->string('email')->unique();
            $table->timestamp('email_verified_at')->nullable();
            $table->string('password');
            $table->rememberToken();
            $table->foreignId('current_team_id')->nullable();
            $table->string('profile_photo_path', 2048)->nullable();
            $table->timestamps();
=====================
*4th Copy data from user model Class and paste into admin Model Class
then change Class name user to admin in admin class

=====================
*5th Run migration comand
		
	
		php artisan migrate 
		Check Database 
=====================
*6th Make Admin Factory 
	

		php artisan make:factory Adminfactory
=====================
*7th copy some data from user factory  like below 


	public function definition()
	paste into return array

            'name' => $this->faker->name(),
            'email' => $this->faker->unique()->safeEmail(),
            'email_verified_at' => now(),
            'password' => '$2y

	$10$92IXUNpkjO0rOQ5byMi.Ye4oKoEa3Ro9llC/.og/at2.uheWG/igi', // password
            'remember_token' => Str::random(10),

=====================
*8th then user model classes in admin model class 
		

		use App\Models\User;
		use Illuminate\Support\Str;
=====================
*9th open seeder file and uncomment out and change name User to Admin


	like this :-> 
        \App\Models\Admin::factory()->create();


=====================
*10th to insert data run seeder command 


	php artisan migrate --seed
----------------------------------------------------------------------------
*11th After take rest Create Guard 
		

		Opne Config folder and open auth file then edit or add some below code
		under guard copy web code and edit using admin like below 
		1st 
-------------------------------------
     'admin' => [
            'driver' => 'session',
            'provider' => 'admins',
        ],
-------------------------------------
*2nd  add provider like below 
-------------------------------------
 

	       'admins' => [
	            'driver' => 'eloquent',
	            'model' => App\Models\Admin::class,
	        ],
-------------------------------------
*3rd add password like same  way 
-------------------------------------
   
   
           'admins' => [
            'provider' => 'admins',
            'table' => 'password_resets',
            'expire' => 60,
            'throttle' => 60,
        ],
--------------------------------------
*Take rest 
--------------------------------------


	12th open sublime text press controll key search 
	Authsessioncontroller file  admin controller 

*After creating Guard  steps

------------------------------
	i missed this if need can comment me 


*…or create a new repository on the command line
*echo "# Laravel8_Multi_Auth" >> README.md
*git init
*git add README.md
*git commit -m "first commit"
*git branch -M main
*git remote add origin https://github.com/Amankhalsa/Laravel8_Multi_Auth.git
*git push -u origin main
*…or push an existing repository from the command line
*git remote add origin https://github.com/Amankhalsa/Laravel8_Multi_Auth.git
*git branch -M main
*git push -u origin main




<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 1500 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](https://patreon.com/taylorotwell).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Cubet Techno Labs](https://cubettech.com)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[Many](https://www.many.co.uk)**
- **[Webdock, Fast VPS Hosting](https://www.webdock.io/en)**
- **[DevSquad](https://devsquad.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[OP.GG](https://op.gg)**
- **[CMS Max](https://www.cmsmax.com/)**
- **[WebReinvent](https://webreinvent.com/?utm_source=laravel&utm_medium=github&utm_campaign=patreon-sponsors)**
- **[Lendio](https://lendio.com)**
- **[Romega Software](https://romegasoftware.com)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
