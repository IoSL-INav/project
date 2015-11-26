# "IoS Lab - Indoor Navigation" - 3rd milestone meeting

## Participants
Jan, Andreas, Lennart, Sebastian, Mathias

## Start
26th Nov, 10:30 o'clock

## Subjects

* Possible merge of PIazza and IoSL-INav
** PIazza is reimplementation of backend parts of previous projects
** We would have to talk

* Backend work
** Add tests for our API parts
*** At least one test per Controller function
*** Provide a 'mock' setup so that we can perform tests with that added user
*** There are plenty of Node.JS test suites
** Friends lists
*** Initial list will be the 'All friends' list
*** Move /lists (/groups) endpoint to /users
** Restructure the API
*** Make it location dependent to always share my location to defined user group when I'm entering a so called 'hotspot' (mensa, library, etc.)
*** Pin point user's location as a fallback or even privacy default
** Authorization can use the node keycloak package
** TODO: Restructure API
** TODO: Completely update use cases based on restructured API
** TODO: Come up with a solution for removing users from a location
** TODO: Add a docker compose file
** TODO: Have a look at the keycloak package
** TODO: Implement tests for backend controllers

* Mobile applications
** Use long-lasting background connections to devices (Android should work)
** Jan presents current status
*** Implemented web view for later authorization
*** Able to position and view mensa plan
** There is the possibility to get more beacons if we would need more
** TODO: Exchange gained information about web view and beacon stuff
** TODO: Get long-lasting connections working (websockets?)