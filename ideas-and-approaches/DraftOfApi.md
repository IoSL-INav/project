# Endpoints needed for user management


## Get information of current user
	GET /users/me


## Change user information

```
    PUT /users/me

    {
        "userName": "stringUserName",
        "userAutoPing": true,
        "userAutoGroup": "stringGroupName",
        "userAutoLocate": false
    }
```

```
    Server response:
    {
          userID: 'ee000000-1234-abcd-def71-83a736f72941',
          userName: 'marksUsername',
          userEmail: 'mark.smith@web.org',
          userAutoPing: true,
          userAutoLocate: false
    }
```



## Delete user
	DELETE /users/me


## Login
	GET /login


## Logout
	GET /users/me/logout


## Set location information

```
PUT /users/me/location

{
    "userBuilding": "stringUserBuilding",
    "userFloor": "stringUserFloor",
    "userMajor": 1234,
    "userMinor": 5679,
    "userLat": 50.99999,
    "userLon": 49.99999
}
```



## Delete location information

```
DELETE /users/me/location
```


## Get all groups of user

```
GET /users/me/groups
```


```
Server response:

[{
    "name": "All friends",
    "_id": "569aa...d4f67e7",
    "members":[{
        "_id": "userID-...-234-",
        "name": "edugain.72dd37f8ase...1e184cd37d8b"
    }]
}]
```


## Create a group

```
POST /users/me/groups

{
    "groupName": "stringGroupName"
}
```



## Show groups information
	GET /users/me/groups/groupID


## Change groups information

```
PUT /users/me/groups/groupID
{
    "newGroupName": "stringGroupName"
}
```



```
Server Response:

{
		status: 'success',
		reason: 'group updated',
		group: {
			name: 'updateGroupName',
			_id: '56acaf64a980090d254dbfc8',
			members: []
		}
}
```


## Delete specific group
	DELETE /users/me/groups/groupID


## Add user to groups

```
POST /users/me/groups/groupID/users

{
    "userID": "insert companionID here"
}
```



```
Server response:

{
    "status": "success"
    "reason": "user added to group"
}
```



## Remove user from list
	DELETE /users/me/groups/groupID/users/userID


# Companion Requests
	/companionrequests


## Show pending requests
	GET /companionrequests

```
Server response:

[{
		"_id": "56accf6e4a94cae610c223c9"
		"from": "b9b0d35c-...-cd06d7b46d70"
		"to": "b9b0d35c-...-cd06d7b23634f2"
		"status": "pending"
		"__v": 0
}]
```


## Create a companion request

```
POST /companionrequests

{
    "userEmail": "insert companion mail address here"
}
```


```
Server response:

{
		"status": "success"
		"reason": "companion request sent"
		"companionRequestID": "56accf6e4a94cae610c223c9"
}
```


## Get a companion request status
	GET /companionrequests/companienrequestID

```
Server response:

    {
			"_id": "56accf6e4a94cae610c223c9"
			"from": "b9b0d35c-...-cd06d7b46d70"
			"to": "b9b0d35c-...-cd06d7b23634f2"
			"status": "pending"
			"__v": 0
		}
```


## Change a companion request

```
PUT /companionrequests/companienrequestID

{
    "accept": true
}

or

{
    "deny": true
}
```
```
Server response:

{
    "status": "success"
    "reason": "companion request accepted"
}
```


## Delete a companion requests

```
DELETE /companionrequests/companienrequestID
```
```
Server response:

{
    "status": "success"
    "reason": "companion request deleted"
}
```


# Hotspot information
	/hotspots


## Get a list of all hotspots

```
GET hotspots/
```


```
Server response:

[
  {
    "_id": "56acd...1f6f81162c",
    "name": "Mensa",
    "beacons": [
      {
        "name": "shoe",
        "companyUUID": "D0D3FA86-....-6AF44C51822F",
        "major": 9386,
        "minor": 56215,
        "location": {
          "coordinates": [
            13.326402,
            52.509646
          ],
          "building": "Mensa",
          "floor": "Mensa 2.OG"
        }
      },
      {
        "name": "car",
        "companyUUID": "D0D3FA86-....-6AF41DFC866B",
        "major": 62242,
        "minor": 28193,
        "location": {
          "coordinates": [
            13.326402,
            52.509646
          ],
          "building": "Mensa",
          "floor": "Mensa 2. OG"
        }
      },
      {
        "name": "fridge",
        "companyUUID": "D0D3FA86-....-6AF4BC5AD3C5",
        "major": 62245,
        "minor": 37267,
        "location": {
          "coordinates": [
            13.32576,
            52.509851
          ],
          "building": "Mensa",
          "floor": "Mensa 1. OG"
        }
      },
      {
        "name": "door",
        "companyUUID": "D0D3FA86-....-6AF4BB14CA82",
        "major": 42882,
        "minor": 54653,
        "location": {
          "coordinates": [
            13.32576,
            52.509851
          ],
          "building": "Mensa",
          "floor": "Mensa 1. OG"
        }
      },
      {
        "name": "purpleDoor",
        "companyUUID": "D0D3FA86-....-6af401c6e22d",
        "major": 49816,
        "minor": 55395,
        "location": {
          "coordinates": [
            13.326402,
            52.509646
          ],
          "building": "Mensa",
          "floor": "Mensa 2. OG"
        }
      },
      {
        "name": "blueBeacon",
        "companyUUID": "b9407f30-....-25556b57fe6d",
        "major": 1000,
        "minor": 20010,
        "location": {
          "coordinates": [
            13.326261,
            52.509489
          ],
          "building": "Mensa",
          "floor": "Mensa 1. OG"
        }
      },
      {
        "name": "greenBeacon",
        "companyUUID": "b9407f30-....-25556b57fe6d",
        "major": 1002,
        "minor": 3090,
        "location": {
          "coordinates": [
            13.325618,
            52.509693
          ],
          "building": "Mensa",
          "floor": "Mensa 1. OG"
        }
      }
    ]
  }
]
```


## Get a hotsport via ID
	GET /hotspots/hotspotID


## Get all friends in specific hotspot

```
GET /hotspots/active_friends
```


```
Server response:
{
      "friends": [{
          "id": "userID01",
          "name": "userName01",
          "location": {
              "coordinates": [ 13.3, 45.5 ],
              "building": "BA",
              "floor": "12th",
              "accuracy": 2
          }
      }, {
        "id": "userID02",
          "name": "userName02",
          "location": {
              "coordinates": [ 14.3, 42.5 ],
              "building": "AB",
              "floor": "19th",
              "accuracy": 1
          }
      }]
}
```


## Get all beacon information for hotspot
	GET /hotspots/hotspotID/beacons/


## Get a specific beacon information for a hotspot
	GET /hotspots/hotspotID/beacons/beaconID
