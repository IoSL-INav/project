# Team meeting for "IoS Lab - Indoor Navigation"

## Participants
Andreas, Lennart, Eridy, Sebastian, Mathias

## Begin
10th Dec, 10:30 am

## Notes
* Backend
  * We discuss the current status
  * Should we store the user ID in cookie or provide it via middleware in request?
  * Groups
    * TODO: Return created groupID on group adding
  * Database
    * Reduce collection amount to lower number
    * TODO: Switch from reference to subdocument (e.g. for location)
    * TODO: Put chapter about 'Database design' into documentation
    * TODO: Watch mongoose (mocking?) logging during queries
  * Mobile applications
    * Eridy presents his current status on iOS
    * Localisation differs in two ways
      * Pinned: lat and long are set
      * Region-based: located via beacons, lat and long for person empty