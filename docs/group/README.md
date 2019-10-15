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

## Sprint 1 October 2nd - 8th 

The purpose of this sprint was for every one to get some knowledge of the laravel framework, and set up
their development environments. Which involved setting up the Documentation repository and Whats for dinner api. 

#### Justin Dearden
<p>
Hey Everyone, here is my stand up for the week. This week I set up both repos locally on my machine. I installed Laravel with valet and got everything running.  I created the documentation for the Mac installation guide (I do want to tweak it a bit, the headings are off on the Vue page.) Ive been going over the Laracasts and just experimenting and getting familiar with Laravel. 
</p>

#### James Moore
<p>
1. I created a GitHub organization to house our teams documentation repository and api repository. 
I deployed our documentation site using the static site generator vue press to github pages accessible at https://avocodeo.github.io/docs/ and included some boilerplate for Homepage, guide (development environment set ups) and group related things such as availability.
I created/assigned tasks to my team members to mostly set up there environments and add documentation for the process they followed PC/Mac setups.
I created and pushed a wfd-api repository, this is going to be the backend of our application using the PHP framework Laravel. I modified the welcome page and created a application status end point and accompanying test. To show whether the application is running properly. 
Wrote up our simple design documentation and deployed to documentation website 
2. Today I'm going to create tasks for the following week. We've decided to go with team member Tyler's name suggestion whats-for-dinner for our application 
</p>

#### Sahil Verma
<p>
1.    Installation of Laravel on local machine complete - the installation process involved downloading a composer, PHP and Laravel. The process wasn’t a smooth and simple installation as some steps needed proper attention. In the PC documentation guide I created, I listed all the steps that need to be completed in-order for a smooth installation. Example, making sure the latest version of PHP was installed so the composer could work, disabling certain extensions in the php.ini file so Laravel could install properly etc. If followed properly, Laravel will install and you will be able to work with the file in an editor of your choice. 
2.    Documentation Guide posted on GitHub (formatting will be adjusted for easier reading)
3.    Downloaded local repository that James has posted in GitHub to keep in-line with group for our web application What’s For Dinner
4.    Watching Laracast videos/YouTube tutorials to familiarize myself with the environment and extra practice for when we start coding!
</p>

#### Tyler Ouellette

<p>

1. I created a Trello board for the group that is being used for our weekly sprints. 
   
2. I installed composer for mac and laravel. I had some issues initially with the set up process. After looking over the process and re-doing it, I got it working properly.  The issue was within my zshrc file Path.
   
3. Created a review of the laracasts videos with basic examples and documentation for quick reference. Will be uploading the documentation once formatting is complete.
   
4. Watched the Laracast Videos up to video 10.

</p>

#### Nick Stanton
<p>
1. I followed the documentation provided by group members and installed Git, PHP, Composer, and Laravel in that order. Encountered some dependency isues, fixed and made sure all further dependencies were correct, all plugins were loaded. PHP Launches, and is able to run laravel framework.
2. Git cloned the project files and ensured that compatibility was working between my system and the rest of the group
3. Participated in card edits on trello, providing input where necessary
4. Edited setup documentation for installation stand-alone systems
</p>

## Sprint 2 October 9th - 14th 

#### Tyler Ouellette
<p>

1. Attended sprint meeting with the customer. 30min
2. Helped design database Schema with Justin/Sahil for table layout and entity relationship  1hr
3. Created Users endpoint for API which included created the controller, table seeder, Factory, migrations and Test cases with the help of James 3 hours. This did entail issues as test cases for create user and update user failing (ongoing issue, 2 additional hours of trouble shooting)
4. Basic Trello housekeeping, brainstorm ideas for project. 30 min
5. Added members to review section of pull requests.
6. Create Sprint Report, update Docs repo of sprint details.
</p>

#### James Moore
<p>
1. Brain stormed features 30m
2. Helped out some team mates with development environment issues /questions 2.5h. 3. Prepared the sprint for this week 2h
4. Added reoccurring agile techniques and use to our group documentation page
5.  Created Controller, model, migrations, endpoints and tests for Categories, Measurements, Ingredients as well as setting up a relationship and foreign key with ingredient to measurement 6h. 
6.  Added members to review section of pull requests.
</p>

#### Justin Dearden
<p>
1. Implemented continuous integration software (Travis) to the repo. Set up its test environment, DB settings, commands and linked it to the project. Configured it after for better optimization. (https://travis-ci.com/Avocodeo/wfd-api) Time spent: 2.5H.
2. Created ‘Recipes’ endpoint for the API. Involved building the controller, model, view, DB factory, DB seeder, migrations and test cases. Time spent: 3H.
3. Attended sprint meeting with our customer/Tyler. Time spent: 30M.
4. Helped design database schema with Tyler/Sahil. Time spent: 1H.
5. Housekeeping items, such as updating Trello and reviewing pull requests on GitHub. Time spend: 30M.
</p>

#### Sahil Verma
<p>
1. Worked with Tyler and Justin to create our unofficial database schema
2.Created an updated/official database schema using dbdiagram.io to get a better visual representation with relationships 
2a.Using Microsoft Access, created all database tables, populated 100 ingredients with RNG numbers for cost, expiry date and quantity so we can start coding some of our features since data is in. Created the same relationships using Microsoft Access which now allows us to do advance SQL queries in Access which we can convert to MySQL commands. Access also allows us to easily export our table to numerous file types making it easy to add to any database language/framework.
3. Brainstormed a couple ideas for what our application can do and added to our Trello card
</p>

#### Nick Stanton