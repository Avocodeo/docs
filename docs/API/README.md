# WFD-API

#### How does our API separate critical systems from the users?
  * The WFD-API acts as a traditional application programming interface; it acts as a piece of middleware between the user (web app) and the critical systems that are in place. 
    * This is done by visiting custom pages that act as query builders and perform certain functions on the database, preventing the user from directly manipulating the database through the web interface.
  * These HTTP requests will trigger functions within the controllers for each page for viewing and manipulating data. 
  

#### How does Laravel use the API?
  * API deals with the database end of the web app. It acts as another layer of custom “middleware” to separate end users from the raw data used. Laravel interacts with the API in order to retrieve/store relevant data, which then gets parsed and formatted depending on the user’s request.
  * The API performs different functions depending on which HTTP request was performed. Laravel interprets these requests and routes the command through various API functions that perform certain tasks. The typical “GET” request will fetch all relevant data and will display it to the user in raw JSON format, while a “POST or “PATCH” request will add a new entry or will edit/modify an existing entry.

* Explain how the API can help with development.

  * Through the use of ‘php artisan tinker’
  
  * ```App\Project::first()``` - This will dump the first entry within the table “project” in the database
  
  * ```App\Project::all()``` - This will dump the entire table “projects”
  
#### How can you access it?
* As it currently stands, the web app is hosted locally on developer systems. Because of this, the following links are local and will not work unless the app is hosted locally. To access the API directly, visit one of the following pages:
  * Users - http://127.0.0.1:8000/api/users
  * Ingredients - http://127.0.0.1:8000/api/ingredients
  * Inventories - http://127.0.0.1:8000/api/inventories
  * Measurements - http://127.0.0.1:8000/api/measurements
  * Recipes - http://127.0.0.1:8000/api/recipes

## Example of API call - Ingredients

  * Each call to the API is dictated by the controller page associated with this API endpoint. As a result, certain fields are returned in raw JSON format right from the database. Here is an example of visiting the page "http://127.0.0.1:8000/api/ingredients":
  
```
[
    {
        "id": 1,
        "name": "salt",
        "measurement_id": 1,
        "created_at": "2019-10-25 04:44:43",
        "updated_at": "2019-10-25 04:44:43",
        "measurement": {
            "id": 1,
            "name": "Gallons",
            "abbreviation": "gal",
            "type_id": 2,
            "created_at": "2019-10-25 04:44:43",
            "updated_at": "2019-10-25 04:44:43",
            "type": {
                "id": 2,
                "name": "Volume",
                "created_at": "2019-10-25 04:44:43",
                "updated_at": "2019-10-25 04:44:43"
            }
        }
    },
    {
        "id": 2,
        "name": "pepper",
        "measurement_id": 1,
        "created_at": "2019-10-25 04:44:43",
        "updated_at": "2019-10-25 04:44:43",
        "measurement": {
            "id": 1,
            "name": "Gallons",
            "abbreviation": "gal",
            "type_id": 2,
            "created_at": "2019-10-25 04:44:43",
            "updated_at": "2019-10-25 04:44:43",
            "type": {
                "id": 2,
                "name": "Volume",
                "created_at": "2019-10-25 04:44:43",
                "updated_at": "2019-10-25 04:44:43"
            }
        }
    }
]
```

## Example of API call – Users
* When performing a “GET” request on the page “API/Users”

```
[
  {
    "id": 2,
    "name": "Braden Beatty",
    "isAdmin": 0,
    "email": "haag.estell@example.org",
    "email_verified_at": "2019-10-25 04:44:43",
    "created_at": "2019-10-25 04:44:43",
    "updated_at": "2019-10-25 04:44:43"
  }
]
```
  * Notice how the API did not return password fields. The API is returning on the data necessary for the user to see and make decisions, and the password field is not necessary. The API is preventing the user from seeing unauthorized information. Sensitive fields like password information should never be returned, and is handled by the back end the API that handles authentication.
  * This is also returned when using the “php artisan tinker” command which opens an interactive shell to the API that can fetch the same data
 
```
$php artisan tinker
Psy Shell v0.9.9 (PHP 7.3.10 — cli) by Justin Hileman
>>> App\Ingredient::first()
=> App\Ingredient {#3127
     id: 1,
     name: "salt",
     measurement_id: 1,
     created_at: "2019-10-25 04:44:43",
     updated_at: "2019-10-25 04:44:43",
     measurement: App\Measurement {#3083
       id: 1,
       name: "Gallons",
       abbreviation: "gal",
       type_id: 2,
       created_at: "2019-10-25 04:44:43",
       updated_at: "2019-10-25 04:44:43",
       type: App\MeasurementType {#3094
         id: 2,
         name: "Volume",
         created_at: "2019-10-25 04:44:43",
         updated_at: "2019-10-25 04:44:43",
       },
     },
   }
```

## Example of API page - Ingredients

  * Here is the code for the API page "Ingredients". Going back to how the API operates, each page will return information as dictated by the API controller pages and how the HTTP request was routed by Laravel.
  
```
<?php

namespace App\Http\Controllers\API;
use App\Http\Controllers\Controller;

use App\Ingredient;

class IngredientsController extends Controller
{
    public function index()
    {
        return Ingredient::all();
    }

    public function show(Ingredient $ingredient)
    {
        return $ingredient;
    }

    public function create()
    {
        return view('ingredients.create');
    }

    public function store()
    {
        $attributes = request()->validate([
            'name' => 'required',
            'measurement_id' => 'required',
        ]);

        $ingredient = Ingredient::create($attributes);
        return response()->json([
            'id' => $ingredient->id,
            'message' => 'ingredient was successfully created'
        ]);
    }

    public function update(Ingredient $ingredient)
    {
        $attributes = request()->validate([
            'name' => 'required',
            'measurement_id' => 'sometimes'
        ]);

        $ingredient->update($attributes);

        return response()->json([
            'ingredient' => $ingredient->name,
            'message' => 'ingredient updated'
        ]);
    }

    public function destroy(Ingredient $ingredient)
    {
        $ingredient->delete();

        return response()->json([
            'message' => 'ingredient was successfully deleted'
        ]);
    }
}
```

  * When performing a "GET" HTTP request on this page, Laravel will trigger the function: 
  
```
public function index()
{
    return Ingredient::all();
}
```

  * When performing a "POST" HTTP request on this page, Laravel will trigger the function:
  
```
public function store()
{
    $attributes = request()->validate([
        'name' => 'required',
        'measurement_id' => 'required',
    ]);

    $ingredient = Ingredient::create($attributes);
    return response()->json([
        'id' => $ingredient->id,
        'message' => 'ingredient was successfully created'
    ]);
}
```

  * When performing a "PATCH" HTTP request on this page, Laravel will trigger the function:
  
```
public function update(Ingredient $ingredient)
{
    $attributes = request()->validate([
        'name' => 'required',
        'measurement_id' => 'sometimes'
    ]);

    $ingredient->update($attributes);

    return response()->json([
        'ingredient' => $ingredient->name,
        'message' => 'ingredient updated'
    ]);
}
```
