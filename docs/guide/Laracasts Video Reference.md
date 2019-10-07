# Review of Laracasts Video Commands

## Getting Started with Routes

Php artisan is what gives you all the commands.

Serve --> serves  application on basic PHP development server
Php artisan serve in terminal to get up and running.

Ex 1. Simple Route
```
Route::get(‘pagename’, function()  {
	return view(‘viewname’); 
});
```

Get (‘XXXX’) asks for what will be in the url. (‘/’) is the home page. So inside you would return view(‘home’);

--------------------------------

## Creating a Layout across all views (for headers, footers, sign up, etc.

`@yield (‘AREA_NAME’)` this allows you to register a section for that content.

You do this by `@extends(‘layout’)`. 

Example 2. Yieilding an Area name

```
index.html file

@yield ('content')

```

INSIDE YOUR VIEW file

```

@section('content')
    <h1> Content </h1>
@endsection

```

Whatever you put inside the section block will put it inside the @yield area that has the same name in any file.

@endsection is necessary to end the section area.

---------------------

## Dynamic Aspects within a layout

For title to be dynamic

`<title> @yield(‘title’) <title>`

You can also pass a second parameter as a default value if nothing is given.

And then in each page, you do:

`@section(‘title’,’pagename’)`

First parameter is for the title section, the second parameter is the value if you want to do it inline rather than a section block.

------------------------------

## Passing Data to Views

In the routes file is where it is done. Inside the view function, you can do a fetch request or hard code in the data in an array, and you pass that array into the get function as a second parameter.

Example 1: Passing Data to Views. 
```
Route::get(‘/about’, function() {
	$tasks = [whatever data you want, each item comma separated. ];

return view(‘page to send to’, [‘tasks’ => $tasks]);
});
```

In the above example, we are passing in the first parameter of the page we are routing to, the second parameter is a php array that sends in ‘tasks’ as the variable $tasks created in the function. 

***There is an alternative return syntax that is acceptable as well. This will be displayed Below.***

Example Alternate Return:

```
Return view(‘page_to_go_to’)->withTasks($tasks)->withFoo(‘foo’);
```

What is important to note with this alternative syntax is that, each “with” statement is declaring what the variable sent to that page is called. ->withTasks will declare Tasks as the variable in the page you are sending too and inside the parenthesis will be the value that you are passing into that page (be it a string, array of data, etc.)

In the view that you want the data, you use php to output the data. Or you can use blade that will make it easier using their syntax that will compile down to php.

Example: Receiving data in view using blade syntax

```
@foreach ($tasks as $task)
	{{ $task }}
@endforeach
```

Using the {{ $variable_name }} format is used as it is using the htmlspecialchars function to sanitize the data that you are passing. If you have full control of the data and you are certain you can trust it that you want to include script tags or etc. you will use {!! !!}. 

-------------------------
## Creating a controller

`Php Artisan make:controller NAME_OF_CONTROLLER`

The idea is to move the routes into  a controller class, and each one is a function. To create a home route. Go to app, HTTP, controllers inside the project folders.

```
Route::get(‘/’, ‘PagesController@home’); 
Route::get(‘/about’, ‘PagesController@about); 
Route::get(‘/contact’, ‘PagesController@contact); 
```

This will call the home function of the pages controller. 

Inside the controller class that extends controller, the function is.

```
Public function  home() {
	//insert the route
	Return view(‘/’, data);
}
```

For basic static pages, it is okay to name the page the same as the route, but usually that is not the case. In larger projects, you will use multiple controllers.

-------------------------
## Querying the database

Eloquent models represent a row in a database. This is called active record pattern. 

.env file represents all of your configuration and private details like API keys, Sessions, DB passwords, etc.

`Php artisan migrate`

In Laravel, we represent the tables and all of our alterations for the tables as classes. It allows you to quickly describe a scheme for table and just use an API.

If you need to  undo the migration, run:

`php artisan migrate:rollback`

Ensuring that you do all the migration changes through a class allows for easy pulling of a  database for multiple users rather than making a change locally but when someone tries to use the database, it reverts to the code file, not the phpMyAdmin changes.

`Php artisan migrate:fresh` --> never run in production, but can be done locally. This drops all the tables and refreshes  it from the code.

`Php artisan make:migration create_projects_table `

This will create the table file, inside it will be defaulted to Scheme::create as php has some magic and detects that you want to create and it sets that.

`Scheme:table is how you update a table.`

When you run migrate, it will run the up method. When you run migrate:rollback it will run the down() method. Inside the down method, you are doing everything to undo  what you are doing in the up method.


`Php artisan make:model` will be the singular record of whatever your table is.

Ex. Projects table

```
Php artisan make:model Project    this will create a single record

Php artisan tinker is how you insert records into the tables with data.
Ex. Php artisan tinker

App\Project::all(); will fetch all records from the Projects table.

App\Project::first();

App\Project::latest()->first();
```
All would give null since we don’t have any projects yet. So we need to create one.


```
$project = new App\Project
// this creates a variable called project and instantiates a new project.

$project-> title = ‘My first project’;
$project-> description = ‘Description;

$project to view the record.

$project->save();
```