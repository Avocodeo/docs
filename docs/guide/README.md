# Guide 

## Development Environment Setup

### Mac 
#### Initial Settings
* Install Homebrew (if not already installed).   
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

* Check if PHP is installed on your machine.        
In a terminal window run the following command.        
`php -v`         
If no results are shown then install PHP by running.        
`brew install php`        

#### Installing Composer       
First open a terminal window. For ease of use, create a folder on the desktop (to hold the installer file) and then cd into that folder.        

Your terminal window should not be set to the directory of new folder on your desktop.

* Insall Composer by copy/pasting the following block of code into your terminal window.      

`php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'a5c698ffe4b8e849a443b120cd5ba38043260d5c4023dbf93e1558871f1f07f58274fc6f4c93bcfd858c6bd0775cd8d1') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"`             

Inside your directory folder (on Desktop) there will now be a file called `composer.phar`.       
This new file will have to be set as a global variable, if not it will be needed everytime a new laravel project is created. It's easier to set it as a global variable and call it anytime it's needed.       

* Set Composer.phar as a global variable by running the following command in your terminal window.    

`mv composer.phar /usr/local/bin/composer`        

Now at any point, you can type `composer` in your terminal window, regardless of the directory you are in, and it will run the composer.phar file.    

#### Install Laravel      
* Run the following command to install Laravel.      

`composer global require "laravel/installer"`         

We now need to set the vendor bin for Laravel.

Enter the following commands.        

`cd ~/.composer`  - This will display the vendor file for Laravel.        
Run the `ls` command. There should be a folder titled `vendor` in this directory, if there is not reinstall Laravel with the composer command above. 

`cd vendor`  - Move directories inside of vendor.      
Run the `ls` command again. There should be a folder titled `Laravel` inside the bin directory. If this is here, the install was done correctly.      

* Add the path variable inside Laravel. 

I am using the Zsh shell on Mac. The following command will open the file using Vim.     

`sudo vi ~/.zshrc`          

Inside Vim click the `i` key to activate insert mode.        
* The first line of the file will start with the keyword `export`          

Add a new line under this keyword - this will be the location we write out the PATH variable.     

Write the following underneath the first export statement in the file. 

`export PATH=~/.composer/vendor/bin:$PATH `     

Then click the `esc` key and type `:wq` to save and exit the Vim editor. 

#### Setting Up Initial Project (Test Project)
In a terminal window, `cd` to any folder you want. This is where we will create a test project to ensure Laravel is working correctly. 

Run `laravel new myfirstproject` where `myfirstproject` is the name you will give to the project. 

At this point Laravel should handle installing all the files and you can open the directory in an editor to start working.


### PC 
1.	Step one is to install the latest version of PHP which can be found on the following website 
  a.	https://www.php.net/downloads.php
  b.	Download the zip file that is thread safe and compatible for Windows 10
  c.	Create a file on your C drive called “php”
  d.	Extract the zip file into the php folder located in your C drive
  e.	Delete the zip file


2.	Install a composer to manage our dependencies
  a.	Visit the following link: https://getcomposer.org/doc/00-intro.md and download the Composer-Setup.exe under the heading Installation – Windows
  b.	Run the composer setup and you will automatically see php.exe is suggested as an option for command line 
  c.	Leave the default settings when installing and after installation, close all file explorer windows, command line prompts and proceed to logoff and then login
  d.	Test usage by opening CMD and typing in “composer -V” without quotes and you should see the composer version and time of installation


3.	Time to install Laravel! 
  a.	Type the following into CMD: composer global require laravel/installer 


4.	Make sure your environmental $PATH variable is set up properly. You can do this by opening command prompt and typing without quotes "PATH" and hitting enter. The last entry displayed should show the composer entry. If not, do the following:
  a.	Click the windows button
  b.	Type in “This PC”
  c.	Right-click the icon and hit properties
  d.	Click Advanced system settings located on the left side of the new window
  e.	Select Environmental Variables located near the bottom 
  f.	Select the Path variable and click edit
  g.	Verify you have the following line C:\Users\<your username>\AppData\Roaming\Composer\vendor\bin tied to your user account on Windows
  h.  Full link for myself: C:\Users\Owners\AppData\Roaming\Composer\vendor\bin
  
  A good tutorial to follow for this is here: https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/
  
  
5.	Go to your C:\php folder and find the php.ini-development, php.ini-production 
  a.	Control F to search for ;extension=intl
  b.	Remove the semi-colon in front to allow for extensions 
  c.	Remove all semi-colons from all extensions EXCEPT extension=openssl & extension=mbstring to allow for the use of extensions
  d.	Do this to both files, save and close
  e.	In your address bar in file explorer, type C:\php\php.ini
    i.	Once you hit enter it will open the config file for php
    ii.	Do the same procedure by removing the semi-colon in front of all extensions EXCEPT extension=openssl & extension=mbstring
    iii.	The image below is what all three files should look like
    
    
6.	If you receive a warning for pdo_firebird extension do the following
  a.	Visit this website: https://firebirdsql.org/en/firebird-3-0/#Win64
  b.	Download the 32/64 bit kit ZIP file for manual installation
  c.	Extract the file and search for fbclient.dll
  d.	Copy the file and open the C:\php directory and paste the dll file there
  e.	This will solve the warning message


7.	Open CMD and type Laravel new * where * is the name of your project 
  a.	If you receive a pdo_oci error you will need to download Oracle 12c from the vendors website (optional)

You’re now ready to begin! 
Note: Optional extensions can be installed based off needs

## Management Page Creation

To add a management page into the project the following steps will need to be completed.

`PATH - WFD-API/resources/views/`
Inside the `views` folder, create a new folder for the title of the page that is to be added.

For this walkthrough, `recipes` will be the management page being added.
Inside the new recipes folder     
`PATH - WFD-API/resources/views/recipes/` create two files:
* create.blade.php
* index.blade.php

## create.blade.php
This is the first of two dummy files, as they will load the content for the page out of the `recipes.vue` file - which will be made below.

fill this page with the following:     
```
@extends('layouts.app')

@section('content')
    <v-content>
        this is the page
    </v-content>
@endsection
```

## index.blade.php
This is the second of two files that will be used to initiate a page.

fill this page with the following:     
```
@extends('layouts.app')

@section('content')
    <recipes-index></recipes-index>
@endsection
```

## Create the Recipes model
`PATH - WFD-API/app/`
Inside the app directory create a new model for the item you want to add.

`PATH - WFD-API/app/Recipe.php`
```
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Recipe extends Model
{
    protected $guarded = [];

    protected $with = ['recipe'];

    public function recipe()
    {
        return $this->belongsTo(Recipe::class);
    }
}
```

This sample code sets up the recipe model that will be used later to add page functionality.

This page is boiler plate but the section,
```
    protected $with = ['recipe'];

    public function recipe()
    {
        return $this->belongsTo(Recipe::class);
    }
```
uses a relationship to the `Category.php` model as it references them on the management page. 

## Recipes Controller 
`PATH - WFD-API/app/Http/Controllers/RecipesController.php`
The controller file is where you will add in functionality for the page, such as `create a new recipe` or list the index of recipes.

```
<?php

namespace App\Http\Controllers;

class RecipesController extends Controller
{
    public function index()
    {
        return view('recipes.index');
    }

    public function create()
    {
        return view('recipes.create');
    }
}
```
There are two functions inside this class. 

The first returns the view as `recipes.index` and the second is used to add a button on the page that will allow users to create a new recipe and add it into the database. 

## API Recipes Controller 
`PATH - WFD-API/app/Http/API/Controllers/RecipesController.php`
The controller file inside the API directory is used to add the crud functions to the page, such as `update a recipe` or `delete a recipe`

```
<?php

namespace App\Http\Controllers\API;

use App\Recipe;
use App\Http\Controllers\Controller;

class RecipesController extends Controller
{
    public function index()
    {
        return Recipe::all();
    }

    public function show(Recipe $recipe)
    {
        return $recipe;
    }

    public function create()
    {
        return view('recipes.create');
    }

    public function store()
    {
        $attributes = request()->validate([
            'name' => 'required',
            'category_id' => 'sometimes',
        ]);

        $recipe = Recipe::create($attributes);

        return response()->json([
            'id' => $recipe->id,
            'message' => 'recipe was successfully created'
        ]);
    }

    public function update(Recipe $recipe)
    {
        $attributes = request()->validate([
            'name' => 'required',
            'category_id' => 'sometimes'
        ]);

        $recipe->update($attributes);

        return response()->json([
            'recipe' => $recipe->name,
            'message' => 'recipe updated'
        ]);
    }

    public function destroy(Recipe $recipe)
    {
        $recipe->delete();

        return response()->json([
            'message' => 'recipe was successfully deleted'
        ]);
    }
}
```

This file is a little long so lets break it down further.

The page is boiler plate except for the functions inside the class. 

```
    public function create()
    {
        return view('recipes.create');
    }
```
This function is used to create a new recipe.

```
    public function store()
    {
        $attributes = request()->validate([
            'name' => 'required',
            'category_id' => 'sometimes',
        ]);

        $recipe = Recipe::create($attributes);

        return response()->json([
            'id' => $recipe->id,
            'message' => 'recipe was successfully created'
        ]);
    }
```
This function will store a new recipe in the database. It's using the attributes list in the model `name` and `category_id` as the headers that will be inserted. These are also used in the tests section to build and run the and insert test. 

```
    public function update(Recipe $recipe)
    {
        $attributes = request()->validate([
            'name' => 'required',
            'category_id' => 'sometimes'
        ]);

        $recipe->update($attributes);

        return response()->json([
            'recipe' => $recipe->name,
            'message' => 'recipe updated'
        ]);
    }
```
This function when called on a specific row will open a modal and allow the user to enter a new name and select a new category for the recipe. This category comes from the relationship that was created in the model.

```
    public function destroy(Recipe $recipe)
    {
        $recipe->delete();

        return response()->json([
            'message' => 'recipe was successfully deleted'
        ]);
    }
```
This function when called on a specific row will remove the recipe from the database and then display a message alerting the user it has been completed successfully.

## Routing functions to the management page
`PATH - WFD-API/routes/api.php`

Here we will be linking the functions made above to the routes of the application.

```
Route::get('/recipes', 'API\RecipesController@index');
Route::post('/recipes', 'API\RecipesController@store');
Route::get('/recipes/{recipe}', 'API\RecipesController@show');
Route::patch('/recipes/{recipe}', 'API\RecipesController@update');
Route::delete('/recipes/{recipe}', 'API\RecipesController@destroy');
```

Adding in these lines will allow the functions made above to be called on the page. This connects `routes` the functions.

## Adding page to routes.js
`PATH - WFD-API/resources/js/routes.js`      
Since this is a single page application we will have to add a path to the view so it can be loaded. 

add in the import statement for the view at the top.      
`import Recipes from './views/Recipes'`

next, inside the export default add in a sections for the name and path of the page.

```
    {
        path: '/recipes',
        name: 'recipes',
        component: Recipes
    },
```
Here we are providing the name, component and path to this view so it can be included in the single page application (SPA) build.

## Adding the page to the sidebar
`PATH - WFD-API/resources/components/App.vue` 

To add the page into the sidebar simply create a new entry `v-navigation-drawer`       
```
          <v-list-item to="/recipes" class="text-decoration-none">
            <v-list-item-action>
              <v-icon color="black" size="48">mdi-book-open-page-variant</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>Recipes</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
```

This entry has a `text-decoration` where an icon can be choose. In the example the `mdi-book-open-page-variant` is the title of the icon. This can be switched for a new one to change what is shown in the sidebar. 

The `v-list-item-title` will be the name shown in the side bar. At the very top of this code snippet the line     
`v-list-item to="/recipes"` references the view that will be loaded when the tab is clicked.

## Creating the .vue page
`PATH - WFD-API/resources/views/Recipes.vue`        
This is where the page will be built out. Pages are designed with the Vue JS library. There is a wide selection of pre-built components that can be inclided use or components can be built. 

More information about [Vue JS Components](https://vuejs.org/v2/guide/components.html).

Here is the full source code for the Recipes.vue page that can be used as a sample.
```
<template>
  <v-card>
    <v-card-title>
      Recipes
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="recipes"
      :search="search"
      :loading="loading"
      loading-text="Loading Recipes... Please wait"
    >
      <template v-slot:item.action="{ item }">
        <v-icon small class="mr-2" @click="editItem(item)">mdi-pencil</v-icon>
        <v-icon small @click="deleteItem(item)">mdi-delete</v-icon>
      </template>
      <template v-slot:no-data>
        <v-btn color="primary" @click="initialize">Reset</v-btn>
      </template>
    </v-data-table>
    <v-dialog v-model="dialog" max-width="500px">
      <template v-slot:activator="{ on }">
        <v-btn color="primary" dark class="mb-2" v-on="on">New Item</v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="headline">{{ formTitle }}</span>
        </v-card-title>

        <v-card-text>
            <v-container>
                <v-row>
                    <v-col cols="12" md="6">
                        <v-text-field v-model="editedItem.name" label="Recipe Name"></v-text-field>
                    </v-col>
                    <v-col cols="12" md="6">
                        <v-select v-model="editedItem.category" :items="categories" label="Category" item-text="name" item-value="id" return-object prepend-icon="mdi-scale-balance"></v-select>
                    </v-col>
                </v-row>
            </v-container>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="close">Cancel</v-btn>
          <v-btn color="blue darken-1" text @click="save">Save</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-snackbar v-model="snackbar" :timeout="snackbarTimeout">
      {{ snackbarText }}
      <v-btn color="blue" text @click="snackbar = false">Close</v-btn>
    </v-snackbar>
  </v-card>
</template>

<script>
    export default {
        data () {
            return {
                search: '',
                headers: [
                    {
                        text: 'Name',
                        align: 'left',
                        sortable: false,
                        value: 'name',
                    },
                    { text: "Category", value: "category.name" },
                    { text: 'Created At', value: 'created_at' },
                    { text: 'Updated At', value: 'updated_at' },
                    { text: 'Actions', value: 'action', sortable: false },
                ],
                recipes: [],
                categories: [{
                    text: 'Salt',
                    value: 1
                }],
                editedIndex: -1,
                editedItem: {
                    name: '',
                    category: '',
                },
                defaultItem: {
                    name: '',
                    category_id: '',
                },
                loading: true,
                dialog: false,
                snackbar: false,
                snackbarText: '',
                snackbarTimeout: 2000,
            }
  },
  computed: {
    formTitle() {
      return this.editedIndex === -1 ? "New Recipe" : "Edit Recipe";
    }
  },
  watch: {
    dialog(val) {
      val || this.close();
    }
  },
  created() {
    this.getRecipes();
    this.getCategories();
  },
  methods: {
    getRecipes: function() {
      axios
        .get("api/recipes")
        .then(response => {
          this.recipes = response.data;
          this.loading = false;
        })
        .catch(function(error) {
          console.log(error);
        });
    },

    getCategories: function() {
      axios
        .get("api/categories")
        .then(response => {
          this.categories = response.data;
        })
        .catch(function(error) {
          console.log(error);
        });
    },

    editItem(item) {
      this.editedIndex = this.recipes.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialog = true;
    },

    deleteItem(item) {
      const index = this.recipes.indexOf(item);
      confirm("Are you sure you want to delete this recipe?") &&
        this.recipes.splice(index, 1);
      axios.delete("api/recipes/" + item.id);
      this.snackbarText = "Recipe deleted";
      this.snackbar = true;
    },

    close() {
      this.dialog = false;
      setTimeout(() => {
        this.editedItem = Object.assign({}, this.defaultItem);
        this.editedIndex = -1;
      }, 300);
    },
    save () {
        if (this.editedIndex > -1) {
            Object.assign(this.recipes[this.editedIndex], this.editedItem);
            this.snackbarText = "Recipe updated";
            this.snackbar = true;
            axios.patch('api/recipes/' + this.editedItem.id, {
                name: this.editedItem.name,
                category_id: this.editedItem.category.id
            })
                .then(function (response) {
                    console.log(response);
                })
        } else {
            axios.post('api/recipes', {
                name: this.editedItem.name,
                category_id: this.editedItem.category.id
            })
            .then(function (response) {
                console.log(response);
            });
            this.recipes.push({'name' :  this.editedItem.name, 'category.name' : this.editedItem.category.name });
            this.snackbar = true;
            this.snackbarText = "Recipe created";
        }
        this.close()
    },
}
};
</script>
```

The top half features the components that build the visual look of the page. 
For instnace, adding a pencil icon to the table row.
```
      <template v-slot:item.action="{ item }">
        <v-icon small class="mr-2" @click="editItem(item)">mdi-pencil</v-icon>
        <v-icon small @click="deleteItem(item)">mdi-delete</v-icon>
      </template>
```

or loading in the table headers.
```
    <v-data-table
      :headers="headers"
      :items="recipes"
      :search="search"
      :loading="loading"
      loading-text="Loading Recipes... Please wait"
    >
```

At the bottom is where we call the fuctions on page so they can perform their actions.
```
    editItem(item) {
      this.editedIndex = this.recipes.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialog = true;
    },
```
Here the `editItem` is called on the recipe row allowing for modification. 

```
    deleteItem(item) {
      const index = this.recipes.indexOf(item);
      confirm("Are you sure you want to delete this recipe?") &&
        this.recipes.splice(index, 1);
      axios.delete("api/recipes/" + item.id);
      this.snackbarText = "Recipe deleted";
      this.snackbar = true;
    },
```
Here the `deleteItem` is called to remove the row from the database.

These pages can be altered as needed but should adhear to the code and design guidelines in order to maintain a specific overall look and feel.

## Tools 

* PHP storm PC/Mac
* Vagrant / Homestead PC
* MYSQL Workbench PC
* Sequel PRO Mac
* iTerm2 Mac
* Cmder / Gitbash PC
