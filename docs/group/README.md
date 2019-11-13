# Group

# Design Documentation 

### Who is the audience ?

* Homeowners
* Supply Chain Owners
* Restaurant Owners

### What technologies will be used, at least initially?  (Example: for web, mention which web framework you're using here)

* Git / Github
* Laravel
* Vue JS or React 
* Component Library
* CSS Framework 

### How will the user interact with the project ?

* Web Browser
* Mobile / Desktop

### What problem does this solve?

* keeping track of what users currently have in stock 
* users who aren’t sure what they can make as a meal/dessert given the current inventory. 
* deprecating the use of paper for keeping inventory’s in check. 
* having a shareable and web accessible grocery list.


# Reoccurring Agile Techniques

1. Regression Testing:  We are using a testing framework PHP unit to run our tests. Each time a pull request is made towards the master branch it will have to pass the existing Feature tests we write in order to be merged into the master branch.
2. Test Driven Development: We will be creating controller level tests such as IngredientsControllerTest.php before any code is actually written that will assert how we want the controller to actually work, we will write unit tests for models etc as required, and assert json structures and what appears in our views
3. Continuous Integration: We will be using the tool Travis CI to run our tests each push to a branch / pull request.
4. Code Review practises: Using github every team member is required to assign someone to review the work they've done when they make a pull request
5. Pair Programming: When we plan our sprints our team lead will be pairing our group members with each other to accomplish tasks on trello cards.
6. Code Style Guidelines: Well be following the Cruddy By Design Methodology. The idea is to only use the resourceful methods as much as we can and only break convention when we absolutely must. Video found here https://www.youtube.com/watch?v=MF0jFKvS4SI 
7. Version control system with agile branching: We are using git as our version control system. Each feature must go in its own branch then have a pull request merged to master, 

# Availability 

| Member          |                      Available                      |                 Not Available                  |
| --------------- | :-------------------------------------------------: | :--------------------------------------------: |
| James Moore     |        After 5pm Monday - Friday / Weekends         |            Monday-Friday 8am - 4pm             |
| Tyler Ouellette |    Tuesday, Thursday, Friday / Weekends Any Time    |           Monday & Wednesday 10-7pm            |
| Justin Dearden  | Tuesday + Wednesday + Thursday after 6pm. Weekends~ |                Monday / Friday                 |
| Sahil Verma     |                After 6pm / Weekends                 |                    Mornings                    |
| Nick Stanton    |            Mon \ Wed after 6pm Weekends             | Tuesday / Thursday Before 6pm Monday Wednesday |

# Sprints

## Sprint 1 October 2nd - 7th 

The purpose of this sprint was for every one to get some knowledge of the laravel framework, and set up
their development environments. Which involved setting up the Documentation repository and Whats for dinner api. 

#### Justin Dearden

Hey Everyone, here is my stand up for the week. This week I set up both repos locally on my machine. I installed Laravel with valet and got everything running.  I created the documentation for the Mac installation guide (I do want to tweak it a bit, the headings are off on the Vue page.) Ive been going over the Laracasts and just experimenting and getting familiar with Laravel. 


#### James Moore

1. I created a GitHub organization to house our teams documentation repository and api repository. 
I deployed our documentation site using the static site generator vue press to github pages accessible at https://avocodeo.github.io/docs/ and included some boilerplate for Homepage, guide (development environment set ups) and group related things such as availability.
I created/assigned tasks to my team members to mostly set up there environments and add documentation for the process they followed PC/Mac setups.
I created and pushed a wfd-api repository, this is going to be the backend of our application using the PHP framework Laravel. I modified the welcome page and created a application status end point and accompanying test. To show whether the application is running properly. 
Wrote up our simple design documentation and deployed to documentation website 
2. Today I'm going to create tasks for the following week. We've decided to go with team member Tyler's name suggestion whats-for-dinner for our application 


#### Sahil Verma

1.    Installation of Laravel on local machine complete - the installation process involved downloading a composer, PHP and Laravel. The process wasn’t a smooth and simple installation as some steps needed proper attention. In the PC documentation guide I created, I listed all the steps that need to be completed in-order for a smooth installation. Example, making sure the latest version of PHP was installed so the composer could work, disabling certain extensions in the php.ini file so Laravel could install properly etc. If followed properly, Laravel will install and you will be able to work with the file in an editor of your choice. 
2.    Documentation Guide posted on GitHub (formatting will be adjusted for easier reading)
3.    Downloaded local repository that James has posted in GitHub to keep in-line with group for our web application What’s For Dinner
4.    Watching Laracast videos/YouTube tutorials to familiarize myself with the environment and extra practice for when we start coding!


#### Tyler Ouellette


1. I created a Trello board for the group that is being used for our weekly sprints. 
2. I installed composer for mac and laravel. I had some issues with the set up process. I created a document with all the instructions of what I did and followed of the laracast videos and included screen shots of the errors that I had. 
3. Uploaded my documentation guide to the github.
4. Created a review of the laracasts videos with basic examples and documentation for quick reference. Will be uploading the documentation once formatting is complete.
5. Watched the Laracast Videos up to video 10.


#### Nick Stanton

1. I followed the documentation provided by group members and installed Git, PHP, Composer, and Laravel in that order. Encountered some dependency isues, fixed and made sure all further dependencies were correct, all plugins were loaded. PHP Launches, and is able to run laravel framework.
2. Git cloned the project files and ensured that compatibility was working between my system and the rest of the group
3. Participated in card edits on trello, providing input where necessary
4. Edited setup documentation for installation stand-alone systems


## Sprint 2 October 9th - 13th 

#### Tyler Ouellette

1. Attended sprint meeting with the customer. 30min
2. Helped design database Schema with Justin/Sahil for table layout and entity relationship  1hr
3. Created Users endpoint for API which included created the controller, table seeder, Factory, migrations and Test cases with the help of James 3 hours. This did entail issues as test cases for create user and update user failing (ongoing issue, 2 additional hours of trouble shooting)
4. Basic Trello housekeeping, brainstorm ideas for project. 30 min
5. Added members to review section of pull requests.
6. Create Sprint Report, update Docs repo of sprint details.


#### James Moore

1. Brain stormed features 30m
2. Helped out some team mates with development environment issues /questions 2.5h. 3. Prepared the sprint for this week 2h
3. Added reoccurring agile techniques and use to our group documentation page
4.  Created Controller, model, migrations, endpoints and tests for Categories, Measurements, Ingredients as well as setting up a relationship and foreign key with ingredient to measurement 6h. 
5.  Added members to review section of pull requests.


#### Justin Dearden

1. Implemented continuous integration software (Travis) to the repo. Set up its test environment, DB settings, commands and linked it to the project. Configured it after for better optimization. (https://travis-ci.com/Avocodeo/wfd-api) Time spent: 2.5H.
2. Created ‘Recipes’ endpoint for the API. Involved building the controller, model, view, DB factory, DB seeder, migrations and test cases. Time spent: 3H.
3. Attended sprint meeting with our customer/Tyler. Time spent: 30M.
4. Helped design database schema with Tyler/Sahil. Time spent: 1H.
5. Housekeeping items, such as updating Trello and reviewing pull requests on GitHub. Time spend: 30M.


#### Sahil Verma

1. Worked with Tyler and Justin to create our unofficial database schema
2.Created an updated/official database schema using dbdiagram.io to get a better visual representation with relationships 
3.Using Microsoft Access, created all database tables, populated 100 ingredients with RNG numbers for cost, expiry date and quantity so we can start coding some of our features since data is in. Created the same relationships using Microsoft Access which now allows us to do advance SQL queries in Access which we can convert to MySQL commands. Access also allows us to easily export our table to numerous file types making it easy to add to any database language/framework.
4. Brainstormed a couple ideas for what our application can do and added to our Trello card

#### Nick Stanton

## Sprint 3 October 14th - 20th 

#### Tyler Ouellette
1.  Updated Docs Repo with sprint Log, backuplog, and finish sprint report document 2hr
2. Attended Customer meeting  1hr
3. Did Users Management Page with controllers and updated migrations 5h
4. Did Categories Management Page 1hr
5. Created Inventory Model/View/Controller/Routes/Management Page/Test 2hr
6. Helped Group understand functionality of project and database 30min
7. Created Default Admin account to seeder 1hr
8. Minor Trello House Keeping 30min

#### James Moore

1. Added vuetify component library and set up application menu and side bar menu 4h. 
2. Created the first management page ingredients with crud capabilities vue component, created measurements management page vue component and created measurement type model, controller, tests and relationships 10h. 
3. Added bacon strip favicon :bacon: 30m. 
4. Met with group members to solve development environment issues 3H.
5. Sprint planning 2h.


#### Justin Dearden

1. Sat with James to troubleshoot local environment / DB 1hr
2. Research Vuetify and the component library 1hr
3. Created the recipe management page with crud capabilities, vue components and controller 3hr
4. Reviewed main index.vue file to learn structure and understand how to effectively make changes 1hr
5. Sprint review 30min


  #### Sahil Verma

1. Continued working on exporting recipe to text format 2h
2. Researched laracasts videos to get familiar with database concepts 1h


#### Nick Stanton

1. Added 'isAdmin' entry to users table in database for additional administrative permissions, and changed users table migration file. 1h
2. Created AdminController and associated blade pages and setup routes for new user administration page. 1h
3. Extensively researched laravel authentication features for use between Admins and Users. 8h
4. Researched SMTP and laravel's built in email features. 1h

## Sprint 4 October 21st - 27th 

#### Tyler Ouellette
1. Updated Documentation Repo With latest updates 1hr
2. Attended Sprint meeting with our customer 1hr.
3. Worked with James to get categories foreign key setup over discord. 1hr
4. Created Model, View, Controller, Seeder and Tests for Suppliers. 3hr
5. Adding sprint evaluation document to site for download. 30min
6. Finished Inventory, Model, Controller, Seeder, Routes, Tests etc 1hr more.
7. Fixed delete item function in all management pages 1hr
8. Trello Planning and Maintenance 30min
  
#### Sahil Verma
1.    Spent 10 hours watching, learning and implementing the following:
2.    Laracasts videos on routes, controllers, migrations, yield/section tips, database access
3.    Understanding the routes/controllers implemented in our directory structure
4.    Reviewed the management pages to understand how everything is laid out/linked
5.    Attempted to create my own export page with a new route but ended up scratching it since my changes could be implemented in our existing Recipes.vue page
6.    Watched Vue tutorials to understand how the script portion works (methods), templates, click events etc. 
7.    Researched how BLOB works to download a file based off user input
8.    Implemented a download button using BLOB that downloads a .txt file with the name of the recipe the user is downloading with the recipe name and category (lunch, dinner, snack etc) in the file. Confirmation on screen appears when file is downloaded.

#### Nick Stanton
1. Researched and added email system to project. 5h
2. Configured to run with SMTP driver using service called 'Mailtrap.io' for email testing. 1h
3. Created markdown pages for various emails to be sent. 1h
4. Fixed various bugs between email systems and laravel. 2h
5. Documented various API pages within the app. 2h
   
#### Justin Deaden
1. Wrote out documentation for the management page API creation - 3H
2. Worked on the docs site, cleaned up items and added content - 2H
3. Troubleshot environment setups - 1H
4. Researched Laravel issues - Categories not displaying on recipes page - 1H
5. Looked more into Vue and layouts for the management pages - 1H

#### James Moore
1. Went through each management page and did some clean up and fixed code that was causing tests to break. 4h
2. Turned the application into a SPA 0h
3. Highlight where were at in the application 30min
4) Add category_id foreign key on recipes 1h
5) Logout route redirects back to proper page 30min

## Sprint 5 October 28th - Nov 3rd

#### Tyler Ouellette

1.	Updated Docs Repo with sprint Log, backup log and finish sprint report document 2hr 
2.	Attended Customer meeting 1hr 
3.	Help group member understand and use command line Git properly 30min
4.	Helped Nick with Notifications, created in sidebar 30min
5.	Trello Housekeeping 30min

#### Sahil Verma

1. Adjusted download button to directly download file instead of using modal 2h

#### James Moore

1. Created Grocery List feature  3h
2. Adjusted Home page to have a nice display of options on where to start 2h
3. Created Notifications Tab 2h

#### Nick Stanton

1. Added notification table, factory, seeder, notification pages 3h
2. Installed Laravel telescope for debugging 1h
3.	Setup notification API 1h
