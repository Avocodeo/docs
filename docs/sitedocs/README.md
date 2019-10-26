# Management Page Creation

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