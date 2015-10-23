# Team meeting for "IoS Lab - Indoor Navigation"

## Participants
Eridy, Jan, Andreas(10:25), Lennart, Sebastian, Mathias

## Start
23th Oct, 10:10 o'clock

## Subjects

* evaluate bluetooth battery assumption
* Question
  * make decision on battery assumption, 
  * how many userinteraction do we want
  * ask Clemens about the position of the wifi, how exact the coordinates are and if we can get the api-documentation
* IV Plankammer (Team Flächenmanagement) ask them for floor maps, can we have the CAD Files?
  * ask them also if they have coordinates
* Sebastian send Eridy the account information for estimote
* Idea could also be NFC
  * IOS does not have NFC like android
* for documentation (create matrix)
  * technologies to evaluate
     * bluetooth
     * wifi
     * sensors
     * NFC
     * QR-Code
     * manuel position pionting
* userstory: show friends they are already sitting in the mensa
* (Mathias) cyclone have an api for authentication with eduroam members
  * federation provider can log user in
  * get back a JSON-Token (there is a code in the token)
  * afer this use OpenID to connect
* (Sebastian) have a server implementation for user management
* notify user about location/bluetooth stuff, that it is a high power consuming action
* start working on docker 
  * some buzzwords to search for
    * docker img
    * docker compose
    * docker volume
    * docker links (e.x. two container can connect to one DB)
    * docker expose (internal and there is another one for external port forwarding)
  * we only have to implement it for the server part

* create gantt workplan
* devide time to final presentation into 2 weeks 
  * plan sprints into this 2 weeks
  * create issues to sprints which have a fixed date
    * like demo preperation
    * like documentation

* initial presentation
    * show gantt diagram for the time schedule
    * declare the first problems
    * show technologies matrix
    * working plan for the project (approximately)
