# Backlogs

## Product Backlog

https://avocodeo.github.io/docs/backlogs/#product-backlog
#### In Progress
<!-- - Create Measurements Types management page -->
- Admin Permissions


#### Completed
- Email a recipe to someone
- Route groups for different users access levels
- Notification System
  - The system will generate notifications to system admins, and users via notification bubble and emails 
  - Low inventory
  - Empty inventory
  - Inventory Item Added
  - New User Added


- Grocery List
  - A user will be able to create a grocery list of items that when filled will be updated in the inventory database table    
  - The system will automate the creation of a grocery list from the tolerances set in the inventory.  
  - The system will let users know what meals can be created depending on the current inventory


- Add documentation for api endpoints (ie. GET request to api/ingredients)
- More documentation for creating a management page
- Adding admin permissions (gate level permissions to application)
- Create VUE router and turn it into a SPA
- Setup Database foreign keys to ensure all tables are correct and referenced.
- Features that are not fully functional yet but are partially implemented
- A user will be able to perform CRUD operations on different ingredients in the front end
- Insert an ingredient
- Update an ingredient
- Delete an ingredient 
- A user will be able to perform CRUD operations on different meals/recipes in the front end
- Insert an recipe
- Update a recipe
- Delete an recipe
- A user will be able to perform CRUD operations on different categories of recipes in the front end
- Insert an category
- Update a category
- Delete an category
- A user will be able to perform CRUD operations on different measurements in the system
- Insert an measurement
- Update a measurement
- Delete an measurement
- Brainstorm grocery list features and use cases
- Add sprint evaluation doc to documentation site for download
- Export recipe in text format 
- Management Page Categories
- Management Page Categories
- Management Page Ingredients
- Management Page Measurements
- Management Page Recipes
- Management Page Users

- Added a favicon for our application
- Created an admin login to seeder
- Discussed how much team each person can actually dedicate to the project for better sprint  estimations
- Created the following management pages
- Users page  can create, update or delete
- Categories page
- Measurements page
- Ingredients page
- Recipes page
- Added Vuetify component library to application

- User authentication system
- A user can login to the system
- A user can logout of the system
A user will be able to perform CRUD operations on different ingredients in the system
- Insert an ingredient
- Update an ingredient
- Delete an ingredient 
A user will be able to perform CRUD operations on different meals/recipes in the system
- Insert an recipe
- Update a recipe
- Delete an recipe
A user will be able to perform CRUD operations on different categories of recipes in the system
- Insert an category
- Update a category
- Delete an category
A user will be able to perform CRUD operations on different measurements in the system
- Insert an measurement
- Update a measurement
- Delete an measurement


## Sprint Backlog
### Sprint 1 October 2nd - 7th

Sprint Backlog

https://trello.com/b/Ua0Wx3S2/highrise-enterprise 

#### James Moore 
-	Setup Travis Continuous integration with Justin. 4h~
-	Categories Model/View/Controller with #Sahil 4h
-	Measurements Model/view/Controller 2h
-	Users Table seeder #Justin  1h
-	Documentation && Sprint planning && Deployments && answering team questions 8h

#### Sahil Verma 
-	Categories Model/View/Controller with #James 4h
-	Documentation updates 1h

#### Tyler Ouellette
-	User Authentication System #Nick 1h
-	Viewing users in the system #Nick 4h
-	Documentation updates 1h
#### Justin 
-	Setup Travis CI with #James 4h~
-	Users Table Seeder #James 1h
-	Documentation updates 1h
#### Nick Stanton
-	Create api endpoint for viewing users #Tyler 4h
-	User Auth system #Tyler 1h
Things that got in the way of the effort put forth in this sprint 



### Sprint 2 October 7th - 14th

#### James Moore 
-	Sprint Planning 2h
-	Set up VUE component library Vuetify 3h
-	Management Page Ingredients 1.5h
-	Management Page Measurements 1.5h
-	Adding route level permissions to application 1h
-	Grocery list feature boilerplate 2h
#### Sahil Verma 
-	Export recipe to text format 3h
-	Management page categories 1h
-	Management page recipes 3h
#### Tyler Oulette
-	Export recipe to text format 3h
-	Management page categories 1h
-	Management page users 3h
#### Justin Dearden
-	Email recipe to someone 3h
-	Management Page Recipes 3h
-	Look up graph libraries we can use and create an example 1h
#### Nick Stanton
-	Email a recipe to someone 3h
-	Management Page users 

### Sprint 3 October 15th- 21st

#### Tyler Ouellette
- Did Users Management Page with controllers and updated migrations 5h
- Did Categories Management Page 1hr
-  Created Inventory Model/View/Controller/Routes/Management Page/Test 4hr
- Created Default Admin account to seeder 1hr


#### James Moore
- Added vuetify component library and set up application menu and side bar menu 4h. 
- Created the first management page ingredients with crud capabilities vue component, created measurements management page vue component and created measurement type model, controller, tests and relationships 10h. 
- Added bacon strip favicon :bacon: 30m. 

#### Justin Dearden

- Created the recipe management page with crud capabilities, vue components and controller 3hr

#### Sahil Verma
- Worked on exporting recipe to text format 2h

#### Nick Stanton
- Added 'isAdmin' entry to users table in database for additional administrative permissions, and changed users table migration file. 1h
- Created AdminController and associated blade pages and setup routes for new user administration page. 1h

### Sprint 4 October 21st - 28th

#### James Moore 
-	Refactor Management Pages, cleaned up code that broke tests 4h
-	Turned application into SPA 30min
-	Highlight where we are at in the application with the group 30min
-	Added category_id and pair programmed with Tyler 1hr
-	Logout route redirects back to proper page 30min

#### Sahil Verma 
-	Researched BLOB files, VUE, Laravel to understand downloaded and exporting to text file. 5h
-	Created download recipe button within the Recipes.Vue page 4h
-	Confirmation when file is downloaded 1h

#### Tyler Ouellette
-	Updated Docs Repo with sprint Log, backup log and finish sprint report document 2hr 
-	Attended Customer meeting 1hr 
-	Categories Foreign key and relationship pair programming with James 1hr
-	Created Model, View, Controller, Seeder, Tests for suppliers 3h
-	Added sprint evaluation document to docs website for download 30min
-	Finished Inventory View, Model Seeder etc. 1hr
-	Fixed delete Item function in all management  pages 1hr
-	Trello Planning and maintenance 30min
-	Database Refactor started and almost finished 3hr

#### Nick Stanton
-	Researched and added email system to project 5h
-	Configured the product to run with SMTP driver using Mailtrap.io for email testing 1hr
-	Created markdown pages  for  various  emails  to  be sent 1h
-	Documented various API pages within the app 2hr

#### Justin Dearden
-	Created documentation for the management page creation 3h
-	Cleaned up the documentation website, refactoring and added content 2h
-	Helped with environment issues 1hr

### Sprint 5 October 29th - Nov 3rd

#### James Moore 
-	Created Grocery List feature  3h
-	Adjusted Home page to have a nice display of options on where to start
-	Created Notifications Tab 


#### Sahil Verma 
-	Adjusted download button to directly download file instead of using modal 2h

#### Tyler Ouellette
-	Updated Docs Repo with sprint Log, backup log and finish sprint report document 2hr 
-	Attended Customer meeting 1hr 
-	Help group member understand and use command line Git properly 30min
-	Helped Nick with Notifications, created in sidebar 30min
-	Trello Housekeeping 30min

#### Nick Stanton
-	Added notification table, factory, seeder, notification pages 3h
-	Installed Laravel telescope for debugging 1h
-	Setup notification API 1h

#### Justin Dearden


## Database Relationships
- A meal has ingredients. 
- Many meals have many ingredients. 
- many ingredients belong to many meals
- A user has one restaurant 
- A restaurant has many users 
