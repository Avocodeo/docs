# Backlogs

## Product Backlog
Product Backlog
https://avocodeo.github.io/docs/backlogs/#product-backlog
In Progress
•	The system will keep track of current inventory of the restaurant/location/household
o	The system will be able to generate notifications on quantity of suppliers
o	The system will be able to generate reports on usage of inventory given a timeframe
•	A user will be able to create a grocery list of items that when filled will be updated in the inventory database table
•	The system will automate the creation of a grocery list from the tolerances set in the inventory.  
•	The system will generate notifications to system admins, and users via notification bubble and emails 
o	Low inventory
o	High inventory
o	Empty inventory
•	The system will let users know what meals can be created depending on the current inventory
•	Management Page Categories
•	Management Page Categories
•	Management Page Ingredients
•	Management Page Measurements
•	Management Page Recipes
•	Management Page Users
•	Graph stats in the application
•	Email a recipe to someone
•	Export recipe in text format 
•	A user may have permissions that are different from other users
•	Route groups for different users
Completed
•	User authentication system
o	A user can login to the system
o	A user can logout of the system
•	
A user will be able to perform CRUD operations on different ingredients in the system
o	Insert an ingredient
o	Update an ingredient
o	Delete an ingredient 
•	A user will be able to perform CRUD operations on different meals/recipes in the system
o	Insert an recipe
o	Update a recipe
o	Delete an recipe
•	A user will be able to perform CRUD operations on different categories of recipes in the system
o	Insert an category
o	Update a category
o	Delete an category
•	A user will be able to perform CRUD operations on different measurements in the system
o	Insert an measurement
o	Update a measurement
o	Delete an measurement


## Sprint Backlog
### Sprint 1 October 2nd - 7th
<p>
Sprint Backlog
https://trello.com/b/Ua0Wx3S2/highrise-enterprise 
James Moore 
-	Setup Travis Continuous integration with #Justin. 4h~
-	Categories Model/View/Controller with #Sahil 4h
-	Measurements Model/view/Controller 2h
-	Users Table seeder #Justin  1h
-	Documentation && Sprint planning && Deployments && answering team questions 8h
Sahil Verma 
-	Categories Model/View/Controller with #James 4h
-	Documentation updates 1h
Tyler Ouellette
-	User Authentication System #Nick 1h
-	Viewing users in the system #Nick 4h
-	Documentation updates 1h
Justin 
-	Setup Travis CI with #James 4h~
-	Users Table Seeder #James 1h
-	Documentation updates 1h
Nick Stanton
-	Create api endpoint for viewing users #Tyler 4h
-	User Auth system #Tyler 1h
Things that got in the way of the effort put forth in this sprint 
 Roadblocks/Showstoppers
•	Development environment setup, incorrect path set up when installing composer halting up some group members
•	Family issues with one group members causing late stand up and documentation site to not be updated with latest standup
•	Module errors when setting up PC local development environment, confusion about whether to use Oracle database or not. 
</p>

### Sprint 2 October 7th - 14th
<p>
James Moore 
-	Sprint Planning 2h
-	Set up VUE component library Vuetify 3h
-	Management Page Ingredients 1.5h
-	Management Page Measurements 1.5h
-	Adding route level permissions to application 1h
-	 Grocery list feature boilerplate 2h
Sahil Verma 
-	Export recipe to text format 3h
-	Management page categories 1h
-	Management page recipes 3h
Tyler Oulette
-	Export recipe to text format 3h
-	Management page categories 1h
-	Management page users 3h
Justin 
-	Email recipe to someone 3h
-	Management Page Recipes 3h
-	Look up graph libraries we can use and create an example 1h
Nick Stanton
-	Email a recipe to someone 3h
-	Management Page users 
</p>


## Database Relationships
- A meal has ingredients. 
- Many meals have many ingredients. 
- many ingredients belong to many meals
- A user has one restaurant 
- A restaurant has many users 
