<img src="https://devmounta.in/img/logowhiteblue.png" width="250" align="right">

# Project Summary

This project is designed to give you an opportunity to build something from scratch and to teach you how to connect all the pieces of an application together. All of the instructions give you an idea of what order to do things in, but there won't be any guidance or solutions on how to write the code itself. The styling of the project is not included in the instructions at all and should be completed at your disgression. 

This project is broken into three parts. The setup instructions are more detailed and are designed to get you started. Parts 1-3 get progressively less detailed to give you a chance to practice your skills on your own. Your mentors have also been asked to provide only minimal guidance. They can point you in the right direction, but cannot help you code. This project is a chance for you to combine and showcase the skills you've learned so far.

Good luck and work hard!

# Setup

This section will help you create the files you need and install the packages you need.

## Color Palette & Font

<img src="https://github.com/DevMountain/simulation-1/blob/master/assets/style_guide.png" />

<b>[Google Font - Open Sans](https://fonts.google.com/specimen/Open+Sans?selection.family=Open+Sans)</b>

## React
1) Run `create-react-app shelfie` and cd into the folder to get started.
2) Run `npm i axios --save`. This is the only package you need to add for our front end.
3) Create a component folder inside of src
4) Inside your component folder create a folder for each component you will be using (Dashboard, Product, Form, and Header)
5) Inside each of these folders create a Javascript file named the same thing. Make sure to capitalize the first letter!
6) Create a simple class component in the Dashboard and Form files. For now just return a div containing the component's name from the render method.
7) Create a functional component (created with the function keyword) in the Header and Product files. For now just return a div containing the component's name.
8) Now render the Dashboard, Form, and Header components in App.
9) Render the Product component inside Dashboard.
10) Run `npm start` to make sure everything is working. You should see the names of all the components displayed.

## Server
1) Run `npm i express body-parser --save`
2) Create a folder called server at the root of the project.
3) Create an index.js file and a controller.js file inside of that folder.
4) Open index.js and require your packages and the controller file.
5) Setup a basic Express server (you will add endpoints later, just get the server ready to run).
6) Open your package.json. Add your main property (so nodemon will work) and your proxy (so our axios requests will work).
    * Your main should look like `"main": "server/index.js"`
    * Your proxy should look like `"proxy": "http://localhost:4000"` using whatever port your server is setup to run on (the port should not .
7) Run `nodemon` and make sure your server runs.

## Database
1) Run `npm i massive dotenv --save`
2) Create an .env file at the root of the project.
3) Open your .gitignore and add the .env file to it.
4) Open server/index.js and require masssive and dotenv (make sure to invoke config on dotenv).
5) Go to [Heroku](https://heroku.com) and create a database (you can also use a database you already have created, but just be careful not to name your table for Shelfie the same thing as any of the tables that already exist in your database)
6) Copy the connection URI for your new or existing database and save it in your .env file (make sure you put `?ssl=true` on the end of the string).
7) Create a folder called db at the root of the project.
8) Set up massive in your server using the connection string you saved in your .env file.
9) Make sure to run `nodemon` again and make sure your database is connecting.
10) Copy the connection string from your .env file into SQLTabs and create the products table.
11) It's helpful to insert some dummy data into your database at this point to help you test as you go along. 

## Competencies
Congratulations! If you finished all the setup, you've already completed some demo competencies!

"Student can use git to create, manage, and synchronize commits locally and remotely (Local and remote repository in-sync, .gitignore)" </br>
"Student can use class based components in react and it's features (render, JSX, nested components)" </br>
"Student can apply ES6 constructs in React for better code (import, export, destructuring)" </br>
"Student can create Node servers using the Express package (Server running)" </br>
"Student can create tables in a database" </br>
"Student can connect to their database in their NodeJS servers using Massive" </br>

# Part 1

<b>Live example [here](https://shelfie.devmountain.com/v2/part1/). Filled out planning sheet [here](https://github.com/DevMountain/simulation-1/blob/master/PLANNING_SHEET.md)</b>

For the first part of the project you will be adding two main features: viewing the inventory and adding additional products.

Functionality of the form:
* A user should be able to add a name and a price for the product.
* A user should be able to add an image URL for the product.
* There should be an image preview that displays the image added by the user.
    * If there is no image URL, a default image should appear in the preview.
    * The image container should remain the same size.
* A user should be able to click the 'Cancel' button to clear all three input boxes.
* A user should be able to click the 'Add to Inventory' button.
    * This should save the product in the database.
    * This should clear the input boxes

Functionality of the dashboard:
* A user should be able to see all of the products that have been added to the inventory.
* Each individual product should display its name, price and image.
    * If there is no image URL, a default image should appear for the product.

## Design
<img src="https://github.com/DevMountain/simulation-1/blob/master/assets/part1_view.png" />

## Step 1
You are going to start with the basic layout of the form and setting up the input boxes. You need to store the value of all three inputs in state.

* Start by creating three input elements in the JSX.
* Then create the 'Cancel' and 'Add to Inventory' buttons.
* Set up state with initial values for the inputs.
* Now you need to update state whenever those inputs change. Write a method for each input and and hook them up to the corresponding input box using an event handler.
* Next you need to reset the input values when the user clicks 'Cancel'. Write a method to reset state and hook it up to the cancel button using an event handler.

## Step 2
In this step you will set up the dashboard to display the inventory. 

* Store the inventory list in the App state. This will make it easier to update with new products later. 
    * Fill the list with some dummy products so you have something to display. 
    * Each one should have a name, price, and image.
    * You can get rid of your dummy data once you are pulling the data from the backend.
* Pass the inventory list down to the Dashboard component through props.
* Inside Dashboard you should map over the inventory list and render the Product component for each product. At this point you should see the word 'Product' repeated the same number of times as you have products in your dummy data.
* Now you should update the Product component to display a name, price, and image based on props.
* Go back to Dashboard and update where you're mapping over the inventory to pass the current product information to the Product component through props.

## Step 3
It's time to write your GET endpoint so you get the inventory list from the database. 

* Open server/index.js and create the entry point for the endpoint. The url should be '/api/inventory'.
* Create the function for this endpoint in controller.js. Set up your endpoint to just send a string (I recommend 'It worked!!! Woohoo!!!') so you can make sure the endpoint works before worrying about the database. Remember to set a status code as well.
* Make sure `nodemon` is running and open up Postman to test your endpoint. Once you get your test string back you're ready to move on.
* Open SQLTabs and write a query to get all the products from the table. Make sure to test it.
* Create a sql file in your db folder named 'get_inventory'. Copy the query you wrote in SQLTabs into the file and save it. 
* Go back to the function you wrote in your controller and remove the test response. Replace it with the database function get_inventory. Now set up the resonse to send the products that come out of the database (with a status code of course).
* Go back to Postman and test your endpoint again. This time you should get the inventory list.

## Step 4 
Now that your endpoint is working, you'll hit it with axios from your front-end.

* Remove the dummy products you created in the App state; we don't need them anymore. (Note: we still need to keep the list on state, we are just removing the fake products from the list)
* Write a method in App that makes a GET request to the endpoint you just wrote. 
    * Once the response comes back from the server, update state with the inventory list you got from the database.
* You want this method to fire as soon as the user opens your page, so invoke it in the lifecycle method that fires as soon as the component loads.

## Step 5
Next you need to write your POST endpoint so you can add new products to your database.

* Open server/index.js and create the entry point for the endpoint. The url should be '/api/product'.
* Create the function for this endpoint in controller.js. This endpoint should pull the name, price, and image URL off of the body. For now all you should do is console.log these values to make sure they're getting to the endpoint correctly.
* Just like before, we should send a test string in the response so we can test our endpoint.
* Make sure `nodemon` is running and open Postman again. When testing your endpoint, make sure to send a fake name, price, and image URL on the body. Once you get the test string back, and you can see the console.log in your endpoint showing the same fake values you sent in Postman, you're ready to move on.
* Open SQLTabs and write a query to add a new product in the table. Make sure to test it.
    * Remember that parameters ($1, $2, etc) only work in your project files and not in SQLTabs. Test your sql query with actual data here.
* Create a sql file in your db folder named 'create_product'. Copy the query you wrote in SQLTabs into the file, change the dummy data to parameters, and save it. 
* Go back to the function you wrote in your controller and remove the test response. Replace it with the database function create_product. Now set up the response to send the 'all good' status code. 
* Go back to Postman and test your endpoint again. This time you shouldn't get any data in the response, but the status code should be green and say 'OK'. Query your database and you should see the new product in your products table.

## Step 6
Lastly, you are going hit the POST endpoint with an axios request

* Before you write your POST request, open App and pass the method that makes the GET request down to Form through props. We need to call this method after we create a new product to get the updated inventory list. 
    * Remember to set the value of 'this' for the method in App.
* Write a method in Form that makes a POST request to the endpoint you just wrote. 
    * You should take the name, price, and image URL from state and send them on the body of the request.
    * Once the response comes back from the server, invoke the method you passed from App to Form through props.
    * Also invoke the method that clears the inputs.
* The method should fire when a user clicks the 'Add to Inventory' button.

## Competencies
You just covered a lot of competencies! Here is the breakdown:

<strong>Step 1</strong> </br>
"Student can use class based components in react and it's features (state, setState, constructors)" </br>
"Student can use class based components in react and it's features (events)" </br>
"Student can apply ES6 constructs in React for better code (arrow functions)" </br>
<strong>Step 2</strong> </br>
"Student can use class based components in react and it's features (props)" </br>
"Student can create functional components that receive and render props" </br>
<strong>Step 3</strong> </br>
"Student can create a RESTful API (GET endpoint)" </br>
"Student can create a RESTful API (Status codes)" </br>
"Student can create SQL statements to manipulate data in their databases (Select)" </br>
"Student can run SQL commands in their NodeJS servers using Massive" </br>
<strong>Step 4</strong> </br>
"Student can interact with the web via axios and REST" </br>
"Student can use componentDidMount in their code" </br>
<strong>Step 5</strong> </br>
"Student can create a RESTful API (POST endpoint)" </br>
"Student can create a RESTful API (body parser)" </br>
"Student can create SQL statements to manipulate data in their databases (Insert)" </br>
<strong>Step 6</strong> </br>
"Student can use class based components in react and it's features (.bind)" </br>

# Part 2

<b>Live example [here](https://shelfie.devmountain.com/v2/part2/)</b>

For the second part of the project you will be adding two additional features: deleting products and editing existing products.

Functionality of the form:
* The form should still perform all of the functionality previously added.
* The 'Add to Inventory' and 'Save Changes' buttons should be conditionally rendered.
    * A user should be able to click the 'Add to Inventory' button only when adding a new product.
    * A user should be able to click the 'Save Changes' button only when editing an existing product.
* A user should be able to click the 'Save Changes' button.
    * This should update the product in the database.
    * This should clear the input boxes and display the 'Add to Inventory' button once complete.
* A user should be able to click the 'Cancel' button while editing.
    * This should cancel any changes made to the product.
    * This should clear the input boxes and display the 'Add to Inventory' button.

Functionality of the dashboard:
* The dashboard should still perform all of the functionality previously added.
* A 'Edit' and a 'Delete' button should display for every product.
* A user should be able to click any 'Delete' button to remove the corresponding product from the database.
* A user should be able to click and 'Edit' button to edit the corresponding product.
    * This should populate the form input boxes with the existing values for the product.
    * This should display the 'Save Changes' button in the form.

## Design
### View 
<img src="https://github.com/DevMountain/simulation-1/blob/master/assets/part2_view.png" />

### Edit Functionality
<img src="https://github.com/DevMountain/simulation-1/blob/master/assets/part2_edit.png" />

## Step 1
In this step you will add the delete functionality.

* Write a DELETE endpoint in your server. 
    * The endpoint should use a parameter to determine which product to remove from the database. 
    * The endpoint should respond with the 'all good' status code if the product is successfully removed.
* Before you write your axios request, open App and pass the method that makes the GET request down to Dashboard through props. We need to call this method after we delete a product to get the updated list.   
* Write a method in Dashboard that sends an axios request to the endpoint you just wrote.
    * The method should accept a parameter to determine which product to remove from the database.
    * Once the response comes back from the server, invoke the method you passed from App to Dashboard through props.
* Pass the method from Dashboard to each Product component through props. 
    * The method should fire when a user clicks any of the 'Delete' buttons.
    * Remember to pass an argument into the method to identify which product should be deleted.

## Step 2
Next you will add the abiltiy to select a product to edit.

* Add an additional property to the App state to store the currently selected product and pass this data to Form through props.
* The Form state should store the id of the currently selected product when editing.
    * This value should be null if the user is adding a new product.
* Use the componentDidUpdate lifecycle hook in Form.
    * This life cycle hook takes in a parameter that represents the old props object before the component updated. In this lifecycle hook we can compare our old props (using the parameter) and our new props (using this.props).
    * Check to see if the selected product being passed from App on the new props object is different from the product on the old props object.
    * If they are different it means that a new product has been selected, and so you should update the Form state with the product information from the new props object.
    * If there is a new product, the 'Add to Inventory' button should switch to the 'Save Changes' button.
* Write a method in App to set the selected product on state.
    * The method should accept a parameter that is the product to be edited. 
    * Remember to set the value of 'this' for the method in App. 
* Pass the method down through props from App to Dashboard, then again from Dashboard to each Product component.
    * The method should fire when a user clicks any of the 'Edit' buttons.
    * Remember to pass an argument into the method to identify which product was selected.

## Step 3
Now you will complete the edit functionality by saving the changes in the database.

* Write a PUT endpoint in your server.
    * The endpoint should use a parameter to determine which product to update in the database.
    * The endpoint should use the body to transfer the updated values for the product.
    * The endpoint should respond with the 'all good' status code if the product is successfully updated.
* Write a method in Form that sends an axios request to the endpoint you just wrote.
    * The method should send the values stored in state in the request. 
    * Once the response comes back from the server, invoke the method that gets the inventory list that was passed from App to Form in Part 1.
* The updating method should fire when a user clicks the 'Save Changes' button.

## Competencies
You added more competencies! Here is the breakdown:

<strong>Step 1</strong> </br>
"Student can create a RESTful API (DELETE endpoint)" </br>
"Student can create a RESTful API (params)" </br>
<strong>Step 2</strong> </br>
"Student can use componentDidUpdate in their code" (This is a bonus competency!)</br>
<strong>Step 3</strong> </br>
"Student can create a RESTful API (PUT endpoint)" </br>

# Part 3

<b>Live example [here](https://shelfie.devmountain.com/v2/#/)</b>

For the final part of the project you will be adding one additional feature: the routing. This part of the project will not have steps for you to follow, but there will be a list of changes that you need to make in each component to your previous functionality.

The functionality:
* Your application should still perform all of the functionality previously added.
* The Dashboard should have its own route.
* The Form should be used in two routes. 
    * There should be a route for adding a product.
    * There should be a route for editing an existing product.
* A user should be able to navigate between the Dashboard and the Add Form using navigation links in the Header.
* A user should be able to navigate to the Edit Form using the 'Edit' buttons. 
* A user should be navigated to the Dashboard upon successfully adding a new product.
* A user should be navigated to the Dashboard upon successfully saving changes to an existing product.
* A user should be navigated to the Dashboard upon canceling changes to an existing product.

## Design
### Dashboard
<img src="https://github.com/DevMountain/simulation-1/blob/master/assets/part3_dashboard.png" />

### Add
<img src="https://github.com/DevMountain/simulation-1/blob/master/assets/part3_add.png" />

### Edit
<img src="https://github.com/DevMountain/simulation-1/blob/master/assets/part3_edit.png" />

## Additional Setup
Run `npm i react-router-dom --save`

## Routing
You should have three routes total.
* '/' should render the Dashboard component.
* '/add' should render the Form component.
* '/edit/:id' should render the Form component.

## Changes

App
* You should no longer store the inventory list in App state (should move to Dashboard state)
* You should no longer store the currently selected product in App state (this will not need to be stored in state)
* The method to get the inventory list should no longer be defined in App (should move to Dashboard)
* The method to select a product to be edited should not exist.
    * This functionality should instead be built using parameters in your routing.
* You should use App to set up your routes.

Dashboard
* You should now store the inventory list in Dashboard state (moved from App)
* The method to get the inventory list should be defined here (moved from App)

Product
* The edit button should now route to the edit view, instead of invoking a method to select the product. Your edit route should use a parameter to determine which product is currently being edited.

Form
* You should write a new GET endpoint that returns a single product.
* You should write a method to hit this endpoint and set the product information on state.
* This method should fire in componentDidMount if the user has selected a product to edit. If the user is adding a new product the method should not fire.
* The user should be redirected to the Dashboard view after adding a new product or saving changes to an existing product instead of calling the method to get the inventory. 
* The componentDidUpdate lifecycle hook should no longer be used to check for a selected product.
* The componentDidUpdate lifecycle hook should now be used to clear the inputs if the user navigates from the Edit view to the Add view.
 
## Final Step
Once you have completed all the functionality of your application you are ready to set up your server to server the front end files
* Run `npm run build`
* Use express.static to serve the build from your server.

## Competencies
You added four more big competencies!

"Student can add ReactRouter to their code base (HashRouter)" </br>
"Student can add ReactRouter to their code base (Route, Switch, component)" </br>
"Student can add ReactRouter to their code base (Link)" </br>
"Student can add ReactRouter to their code base (match object)" </br>
"Student can create Node servers using the Express package (Serving static files)" </br>

<b>Congratulations! You've completed 30 competencies and built your first full-stack application!</b>
