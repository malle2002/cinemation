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

## Forum
Forum is used between users to have more detailed review about movie, discussisions or anything related or non-related to filmography. Anybody can reply to forum post. Posts are categorised.

## Cinemas pages
If the user selects cinemas from the navbar, all cinemas are listed. By clicking a cinema you are getting redirected to cinema's info page. <br/>
Filters are involved to have better searching.

## Movies pages
If the user selects movies from the navbar, all movies that gonna be premierd soon are listed. By clicking a movie you are getting redirected to movies's info page. 
Filters are involved to have better searching.

## Admin Dashboard
If logged-in as administrator you have different view that has CRUD capabilities like:<br/>
<ul><li>Adding cinema or movie</li><li>Removing cinema, movie or user activity</li><li>Updating cinema or movie</li></ul><br/>
Also administrator can give gifts to the users and view logs of the reservations ( can refund only if it's requested 1 day before premiering ).

# Data Model
### User
<ul><li>userId</li><li>username</li><li>email</li><li>phone</li><li>password</li><li>dateOfBirth</li><li>role</li><li>movieReviews</li><li>numberOfReservations</li><li>totalCostOfReservations</li><li>Rank</li></ul>

### Cinema
<ul><li>cinemaId</li><li>name</li><li>location</li><li>capacity</li><li>workingDays</li></ul>

### Movie
<ul><li>movieId</li><li>name</li><li>description</li><li>genres</li><li>rating</li><li>likes</li><li>duration</li><li>director</li><li>actors</li></ul>

### LiveChatComment
<ul><li>userId</li><li>text</li><li>dateCreated</li><li>isEdited</li></ul>

### Reservation
<ul><li>reservationId</li><li>userId</li><li>cinemaId</li><li>movieId</li><li>seats</li></ul>

### Transaction
<ul><li>transactionId</li><li>userId</li><li>reservationId</li><li>paymentCost</li><li>dateCreated</li><li>status</li><li>method</li></ul>

### ForumPost
<ul><li>postId<li>creatorId</li><li>postBody</li><li>likes</li><li>dateCreated</li><li>category</li></ul>


# Technologies used to make the project
### Next.js for the front-end side of the project ( views,components,routing,api requests, etc ).
### Flask for handling backend REST api requests, used for fetching,storing,modifing data.<br/>
  GET {<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinemas',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinema?cId=*',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinema/premier',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinema/premier/{movieId}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinema/premier/{movieId}/reservation',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/movies',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/movies?catId=*&genres=*&duration=*&rating=*',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/movie?mId=*'<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/forum?category=*',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/forum/{category}/post?postId=*',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/forum/c?postId=*',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/profile?pId=*'<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/profile?pId=*&edit=true'<br/>
  }<br/>
  POST {<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinemas/add/{cinemaid}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinemas/edit/{cinemaid}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinemas/delete/{cinemaid}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/movies/add/{movieId}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/movies/edit/{movieId}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/movies/delete/{movieId}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/forum/delete/{postId}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinema?cId=*',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/cinema/premier/{movieId}',<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;'/profile/save/{userId}'<br/>
  }<br/>
### MongoDB NoSQL Database to store the data. 


