# Team meeting for "IoS Lab - Indoor Navigation"

## Participants
Eridy, Jan, Andreas (10:25), Lennart, Sebastian, Mathias

## Start
23th Oct, 10:10 o'clock

## Subjects

* Evaluate Bluetooth battery consumption
* Questions
  * How should be Bluetooth tracking be done?
    * Constantly turned on Bluetooth and automatic tracking inside Mensa? => Privacy issues, battery consumption
    * Time-dependant turn on of Bluetooth e.g. only between 12 - 14 o'clock?
    * Criterias: battery consumption, user interaction, accuracy
  * How important is battery consumption?
  * How much user interaction do we want?
  * Ask tubIT contact person about the position of the WiFi coordinates, how exact the coordinates are and if we can get the API documentation
* Ask IV Plankammer (Team Flächenmanagement) for floor maps, can we have the CAD Files?
  * Ask them also if they have coordinates
* Sebastian send Eridy the account information for estimote
* Idea could also be NFC
  * iOS does not have NFC like Android
* For documentation (create matrix)
  * Technologies to evaluate
     * Bluetooth
     * WiFi
     * Sensors
     * NFC
     * QR-Code
     * manuel position pinning
* Add the user story: Show friends around me (already sitting in Mensa)
* (Mathias) Cyclone has an API for authentication for TUB members
  * Federation provider can log user in
  * We get back a JSON-Token (or: there is a code in the token)
  * After this use OpenID to connect
* Sebastian has a server implementation for this user management (other SNET project)
* Notify user about location/Bluetooth stuff, that it is a highly power consuming action
* Start working with Docker 
  * Some buzzwords to search for could be
    * Docker image
    * Docker compose (orchestration tool)
    * Docker volume
    * Docker links (e.g. two containers can connect to one database)
    * Docker expose (internal and there is another one for external port forwarding)
  * We only have to implement it for the server part
* Create a gantt workplan
* Divide time to final presentation into about 2 week sprints
  * Create issues for sprints which have a fixed date
    * Like finalizing the demo preparation or the documentation
  * Feature implementation should be sorted by importance of user stories
* Initial presentation
    * Show gantt diagram for time schedule
    * List first encountered problems
    * Show technologies matrix
    * Work plan for project (approximately)
