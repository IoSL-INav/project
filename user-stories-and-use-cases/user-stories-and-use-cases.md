# User stories

Andy and I are proposing following user stories to guide the initial phase of our development.

* As a user, I want to be able to use the app in order to locate my friends
* As a user, I want to share my location so that my friends can find me
* As a user, I want to be able to see my friends already located in my area
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

**Use case: Show location to friends**
* Actors: registered user Alice, mobile application, backend
* Flow
  * Alice taps on the button 'Share location'
  * Mobile application shows current position on a map and asks Alice to confirm the position
    * Unconfirmed: Alice can select her current position
    * Confirmed: proceed
  * Alice chooses between sharing her location with all her friends or just a selected few ones
  * Mobile application sends location and sharing data to backend
  * Backend takes current position of Alice, saves it and notifies either all her friends or just the stated ones
  * Backend returns a success message or an error message
  * Mobile application shows answer from backend

**Use case: Find friends already in my area**
* Actors: registered user Alice, mobile application, backend
* Flow
  * Alice taps on the button 'Show friends in my area'
  * Mobile application performs a request to backend asking for users in Alice' friends list with currently turned on location tracking in Alice area
  * Backend receives the request and queries database for Alice' friends within a defined radius of Alice position
  * Backend builds a response and sends it back to mobile application
    * Empty user list: No friends of Alice currently have location tracking enabled and are in Alice' area
    * User list: These friends of Alice meet the criteria
  * Mobile application takes response and either signals that no trackable friends are currently around or shows a map with drawn locations.

**Use case: Turn off location tracking**
* Actors: registered user Bob, mobile application, backend
* Flow
  * Bob taps on 'Turn off location'
  * Mobile application sends 'quit' signal to backend and disables Bluetooth
  * Backend receives 'quit' signal and tries to delete last saved location from database and to deny all further location requests by Bob's friends
    * Failure: backend signals mobile application that an error occured
    * Success: backend transmit a success message to mobile application
  * Mobile application displays shut down message from backend