# cinemation
Cinemation is cinema seat reservation website with multiple plugins like seat reservation, live chat, film critique, admin panel, login system and more...

The view of the site is user role dependent, for users is shown users view and for admin is shown view with CRUD capabilities.

Before accessing the home page the user needs to be authenticated, he can do that on the login page and register page beforehand, if the user is not yet registered.

## Login system
### Login page <br/>
The user can login with self-made cinemation account or via google,twitter or facebook made account using auth0.</br>
When clicking the login button all inputs are validated, if some of the inputs validation requirements are neglected then error labels are shown.<br />
The form inputs are: <ul><li>Email</li><li>Password</li><li>reCAPTCHA</li></ul>

### Register page <br/>
The form inputs for registration are : <ul><li>Username</li><li>Email</li><li>Password</li><li>Repeat password</li><li>Date of birth</li></ul>
The user can later add phone number which is verified by sms and used for two-way authentication and notifications.


## Seat reservation page
To access the page the user needs to be authenticated beforehand, then later can reserve a seat for a specific movie in a specific cinema. <br/>
Gets redirected to login page, if the user is not logged-in. <br/>
When a film and cinema is selected the user sees the UI, which contains the seats as components and are disabled if someone has already bought the seat. <br/>
If user has selected some seat it's displayed information about the seats that can be reserved also the price of the seats and the sub-total. <br/>
The user chooses online payment method which includes methods like paypal, google pay, apple pay and more. Before the payment it's checked if the seat has been taken in meanwhile, if not the user is charged the amount and been given the seats. <br/>

## Live chat module
The live chat is component is shown whenever user accesses any page other than register and login page, if logged-in the user can chat with his information (username,profile picture) been shown, otherwise he/she can chat anonymously.<br/>
Clicking the username or profile picture of the user redirects to logged user's profile.

##  User profile page
In this page, all information for the user are shown also the most recents activities like reviews ( rating and/or comments ) and some stats. 

## Cinemas pages
If the user selects cinemas from the navbar, all cinemas are listed. By clicking a cinema you are getting redirected to cinema's info page. 

## Movies pages
If the user selects movies from the navbar, all movies that gonna be premierd soon are listed. By clicking a movie you are getting redirected to movies's info page. 


# Technologies used to make the project
### Next.js for the front-end side of the project ( views,components,routing,api requests, etc ).
### Flask for handling backend REST api requests, used for fetching,storing,modifing data.
### MongoDB NoSQL Database .




