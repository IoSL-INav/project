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
    * Domain name will change to piazze
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