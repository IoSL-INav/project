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
* Actors: unregistered user, mobile application, federation provider, backend
* Flow
  * Unregistered user downloads the app from any kind of App Store
  * Unregistered user taps on "Sign up"
  * Mobile application sends log in request to keycloak federation provider in order to log user in
  * Mobile application shows return message from backend/federation provider and eventually forwards to main part of application

**Use case: Add a friend**
* Actors: registered user Alice, registered user Bob, mobile application, backend
* Flow
  * Alice taps on the button 'Manage friends' and then presses the '+' button. She puts in Bob's tubIT mail address
  * Mobile application takes input and sends it to backend
  * Backend validates input and looks up supplied user mail
    * Not found: backend returns an error message
    * Found: backend adds 'Bob' to Alice's default friends group and returns success message
  * Mobile applications shows answer from backend


Location sharing is now done via a mixture of geo-fencing so called hotspots and detecting those as well as the user's settings with whom to share the entering/leaving of such a hotspot. Therefore the process of sharing a user's location involves editing the user's settings.

**Use case: Show location to friends (most privacy, most interaction)**
* Actors: registered user Alice, mobile application, backend
* Flow
  * Alice taps on the settings menu button
  * She chooses to disable auto-ping and auto-locating
  * Alice turns WLAN on
  * Alice enters a so called hotspot
  * The application notifies her via push notification that she entered a hotspot and asks if she wants to inform a group about her presence in the area
    * Alice unlocks app and chooses 'no' or which specific group to inform (e.g. all her friends)
  * The application now tries to locate her precisely and therefore asks Alice if she wants to be located that way
    * Alice chooses either 'yes' or 'no'
      * If 'yes': The application asks whether to locate via Bluetooth or manual position pinning
      * If 'no': continue
  * Mobile application syncs gathered context information with Alice's backend information and eventually pings specified friend groups

**Use case: Show location to friends (medium privacy, medium interaction)**
* Actors: registered user Alice, mobile application, backend
* Flow
  * Alice taps on the settings menu button
  * She chooses to enable auto-ping and disable auto-locating
    * She specifies which group to share with if she is found to be inside a hotspot
  * Alice turns WLAN on
  * Alice enters a so called hotspot
  * The application pings everyone in the specified group that Alice entered the area
  * The application tries to locate Alice precisely and therefore asks Alice via push notification if she wants to located be that way
    * Alice unlocks her phone and chooses either 'yes' or 'no'
      * If 'yes': The application asks whether to locate via Bluetooth or manual position pinning
      * If 'no': continue
  * Mobile application syncs gathered context information with Alice's backend information and eventually pings specified friend groups

**Use case: Show location to friends (least privacy, least interaction)**
* Actors: registered user Alice, mobile application, backend
* Flow
  * Alice taps on the settings menu button
  * She chooses to enable auto-ping and auto-locating
    * She specifies which group to share with if she is found to be inside a hotspot
    * She turns Bluetooth on so that the app is able to automatically locate her in beacon fence
  * Alice turns WLAN on
  * She enters a so called hotspot
  * The application pings everyone in the specified group that Alice entered the area
  * The application tries to locate Alice precisely via Bluetooth
    * As always: if that fails, use manual position pinning if wanted
  * Mobile application syncs gathered context information with Alice's backend information and eventually pings specified friend groups

**Use case: Find friends already in my area**
* Actors: registered user Alice, mobile application, backend
* Flow
  * Alice taps on the button 'Show friends in my area'
  * Mobile application performs a request to backend asking for users in Alice' friends list who are currently in a hotspot and have turned on to share their location
  * Backend receives the request and queries database for those friends
  * Backend builds a response and sends it back to mobile application
    * Empty user list: No friends of Alice currently have location tracking enabled and are in the hotspot
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