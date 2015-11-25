## Indoor-Region Based Navigation

* We could use region based navigation in order to route a User to his friends

Setup:

* **Beacon nodes:** The Beacon nodes would be positioned in certain areas of the mensa to create a different regions based on the beacons radio range
* **Devices:** Android/iOS
* **Protocol**: 
* **iBeacon/Bluetooth** will be used for Device/Beacon intercommunication. The Device will retrieve Region-Information via Bluetooth.

* **HTTP** Will be used for Device/Server interaction. The Device will send check-In information via JSON to the server.
 The Device will retriefe check-In information via JSON from the server.
 (Bluetooth, HTTP)
* **Architecture**: Master/Client architecture. (Central Server handling JSON requests as Master, Smartphone devices as clients)

* **Scenario:** As soon as a person enters a region, the Device registers it self and makes a check-in to the location (**check-in** = register the user on the server to this location)

* **Scenario** As soon as a person enters a region he interacts with the application to do a check-in (not automatic)

* **Scenario** A person looking for friends will see the positon (check-ins) on the device (Map). He will be directed to the to the correct region.

* **Pro/Con:** Works possibly without direct access to Device own Location Coordinates (Defined by Beacons)
* Beacon Metadata are stored to the Server (Location,Region)

* Devices does not need to show the whole map but the most certain region.
* Automatic Check-In makes constant Bluetooth tracking mandatory and could result in huge battery dranage.


## Live Indoor-Location Feedback Navigation

* A Person will see how friends are moving to a specific area in Realtime on his device. In order to improve indoor-localization of the devices, we use iBeacons that constantly send LBS in bluetooth information. This enables Devices to capture their indoor-location more precisely.


**Setup:**

* **Beacon nodes:** The Beacon nodes would be positioned in certain areas of the mensa. It should be at least four at each wall.
* **Devices:** Android/iOS
* **Protocol**: 
* **iBeacon/Bluetooth** will be used for Device/Beacon intercommunication. Bluetooth connection between Device/Beacon makes the indoor localization more precisely
* **UDP/WebSockets:** In order to make fast location updates synchronized in all different devices and servers, WebSocket communication is more prefarable then document exchange via HTTP/JSON. (WebSockets enable realtime communication)
* **Scenario:**
* A Person just follows his friends which movements are shown live in the app on a map. (marked as dots or similar other annotations on the map)

**Pro/Cons**

* Application needs pre-calibration Data. In order to enable indoor-localization with help of beacons. The application needs to check each Beacon and register at least once with the Beacons´signal in order to calibrate it´s own location-service. This is mandatory but might also be done previously. The calibration data might be selected and stored in to the application it self as Database. This will help to not force users to calibrate their app themselves.
* Users will need to have bluetooth activated as soon as he wants to use the app (might be forgotten)


## D2D Indoor-Navigation via Virtual Beacons

The Application will implement the iBeacon Protocol and behave itself as Virtual-beacon, constantly broadcasting Bluetooth information, that might be taken up from other Devices nearly. This might be used from Device-to-Device in order to inform about the location of a person in Realtime.

**Setup:**

* **Beacon nodes** Same as in other approaches real Beacons will still be needed in order to enable precise indoor navigation (positioned at wals)

* **Devices** iOS (Estimote virtual Beacons are currently only supported for iOS)

* **Protocol:** iBeacon/Bluetooth only

* **Scenario:**
* A person will see live-update of other friends moving and surrounding him on his device. The device itself uses indoor-coordinates and constantly sends them via iBeacon to surrounding targets. This will give all participants the posibility to find there place to sit.

**Pro/Cons**

* No Server Architecture needed (Device to Device communication)
* The moving persons with their devices might constantly be out of range while moving for a steady exchange of location information
* is only supported on iOS devices


