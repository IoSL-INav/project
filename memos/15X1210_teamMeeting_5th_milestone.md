# Team meeting for "IoS Lab - Indoor Navigation"

## Participants
Andreas, Lennart, Jan, Mathias, Sebastian (10:30), Eridy (11:00)

## Begin
10th Dec, 10:15 am

## Notes
* Mobile applications
  * Android/iOS
    * Jan presents his status
    * Login and hotspot view working
    * Some minor issues with sending the authentication issue
      * Maybe send both cookies (CSRF and connect.sid)
    * Eridy talks about his iOS part
    * TODO
      * Manual position pinning: maj/min from beacon => pinning on map
      * Automatic positioning
      * Decide the items on this list and in which order we want to implement it
    * TODO: Friends updates at this point via long polling
* Backend
  * TODO: Add some permanent logging mechanisms
  * TODO: Work with mobile applications to get a demo running
  * Current progress on new server setup
    * Domain name will change to piazza
  * API
    * Provide some unit tests for basic functions
      * Login does not need to be covered, but the main API endpoints should be
    * Maybe put location schema back into own file and reference it as 'exported' in using models
      * TODO: Do that
    * TODO: Add switch in updateLocation for either taking the beacon UUID (and map it to the beacon's location) or a specific location (maybe pin-pointed)
    * TODO: Make the location values we receive all optional
    * TODO: "Friends in area" response from server has to include an indicator to signal the levels:
      * building + floor
      * beacon maj + min
      * lon + lat
  * Location
    * accept every location (long & lat, bluetooth region[major&minor], eduroam [floor,building])
    * what is the server send to the client if you want to find a friend?
    * long & lat, bluetooth reagion, floor & building
 * possibility to get locations are:
   * Manuel Pin Pointing
   * Bluetooth
   * Eduroam TUBIT API
   * Android API
   * IOS API
 * Presentation ideas
    * Table/Graphics:
  	  * which usecases (Manuel PinPointing should work at the presentation for the mensa, Bluetooth region should work for the mensa)
  	  * make list of scenario what we can do (define what we want todo [1 is primary and 2 is after 1] and 3 is optional)
             * most of them is in our usecases but we should draw it in a diffrent way
  		    1 manuel pin-pointing (step by step)
  		    2 bluetooth positioning
  		    3 geo-fenzzing with apis (android & ios)
 * TODOs what we want todo on sunday
   	* we publish the docker on the server
   	* give example what you can reach
   	* polling is the first notification (long polling is optional)
   	* clients (android&ios) try to talk to the server
   		* clients have to do manuel pin-pointing and bluetooth region location
