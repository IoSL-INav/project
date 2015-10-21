# User stories

Andy and I are proposing following user stories to guide the initial phase of our development.

* As a user, I want to be able to use the app in order to locate my friends
* As a user, I want to share my location so that my friends can find me
* As a user, I want to be able to add friends in order to share locations
* As a user, I want to restrict the location access to only my selected friends
* As a user, I want to be able to completely turn off the location tracking

# Use cases

Based on the user stories mentioned above this would be our initial use cases.

**Use case: Register as user**
* Actors: unregistered user, mobile application, backend
* Flow
  * Unregistered user downloads the app from any kind of App Store
  * Unregistered user taps on "Sign up"
  * Mobile application shows a short sign up formular
  * Unregistered user supplies an user name (unique), a valid mail address and a password
  * Mobile application sends given input to backend
  * Backend validates received input
    * On error: Sends back an error
    * On success: Creates new user based on given input and returns a success message
  * Mobile application shows return message from backend and eventually forwards to main part of application

**Use case: Add a friend**
* Actors: registered user Alice, registered user Bob, mobile application, backend
* Flow
  * Alice taps on the button 'Add a friend' and puts in 'Bob' as the user name
  * Mobile application takes input and sends it to backend
  * Backend validates input and looks up supplied user name ('Bob')
    * Not found: backend returns an error message
    * Found: backend adds 'Bob' to Alice's friend list and returns success message
  * Mobile applications shows answer from backend

**Use case: Show location to friend**
* Actors: registered user Alice, registered user Bob, mobile application, backend