# Backlogs

## Product Backlog
- Users
- User Login
- Admin Permissions
- Regular User Permissions
- Keeping track of inventory of a given location/household/restaurant
- Having a database table of different ingredients
- Having a database table of different meals
- Categories of meals Breakfast, lunch, dinner, snacks
- Measurements table 
- Grocery list feature
- Notifications when something is running low
- notifications when something is added to the inventory
- Being able to add an ingredient
- Being able to add a meal 
- Emails being sent out to users 
When inventory is updated
When inventory is low
when inventory is empty
When a new user is added to the system (restaurant)

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
