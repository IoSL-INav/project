# Endpoints needed for user management

## Get information of current user
	GET /users/me

## Change user information
	PUT /users/me
	
	{
	"userName":"stringUsername",
	"userAutoPing":true,
	"userAutoGroup":"stringGroupname",
	"userAutoLocate":false,
	}
	

## Delete user
	DELETE /users/me

## Login
	GET /login
	
## Logout
	GET /users/me/logout

## Set location information
	PUT /users/me/location
	(only those objects that are available)
	{
	"beaconMAjor":"123.323"
	"beconMinor"121.000"
	"userLat":50.99999, 
	"userLon":49.99999, 
	"userBuilding":"stringUserBulding",
	"userFloor":"stringUSerFlor"
	}

## Delete location information
	DELETE /users/me/location

## Get all groups of user
	GET /users/me/groups
	
Server Response:

	[{
		"name":"All friends",
		"_id":"569aa3726b01d4f67e7",
		"members":[{
			"_id":"userID-234-2-234-234-",
			"name":"edugain.72dd37f8ase04c21fd21591e184cd37d8b"
		}]
	}]

## Create a group
	POST /users/me/groups
	
	{
	"groupName":"stringGroupname"
	}

## Show groups information
	GET /users/me/groups/id
	

## Change groups information
	PUT /users/me/groups/id
	{
	"newGroupName":"stringGroupname"
	}

## Delete specific group
	DELETE /users/me/groups/id


## Add user to groups
	POST /users/me/groups/id/users
	{
 		"userID":"insert companion id here"
	}

Server Response:
	{
		"status": "success"
		"reason": "user added to group"
	}

## Remove user from list
	DELETE /users/me/groups/id/users/uid

---
# Companion Requests
	/companionrequests

## Show pending requests
	GET /companionrequests

## create a companion requests
	POST /companionrequests

	{
 		"userID":"insert companion id here"
	}

## get a companion requests status / informations
	GET /companionrequests/'companienrequestID'

## change a companion requests
	PUT /companionrequests/'companienrequestID'
{
 "accept":true
}
or
{
 "deny":true
}

## delete a companion requests
	DELETE /companionrequests/'companienrequestID'
---
# Hotspot informations
	/hotspots

## Get a list all hotspots
	GET hotspots/

## Get a hotsport via ID
	GET /hotspots/{id}

## Get a specific hotspot like mensa or library
	GET /hotspots/mensa
	GET /hotspots/library

## Get all beacon information for hotspot
	GET /hotspots/{id|mensa|library}/beacons/

## Get a specific beacon information for a hotspot
	GET /hotspots/{id|mensa|library}/beacons/{id}

## Get all friends in the specific hotspot
	GET /hotspots/{id|mensa|library}/active_friends

### example for friends in the hotspot (update Polling)
	GET /hotspots/_hotspotid_/active_friends
	{
  	friends: [871283,8172837213]
  	friends_locations: [{
    id: 9820189238,
    location : {
      lat: 928931,
      lon: 12989312
    }
	}]
	}



#####Subinformation (Q: Where should it be persisted? User model, Hotspot model?):

-> **AutoPing YES/NO**: If I enter the hotspot please ping my friends automatically

-> **AutoLocation YES/NO**: Locate me via Bluetooth automatically when I have turned it on

**Use cases:**
-> Notify ME if I enter the hotspot

--> Option: Ping my Friends at the hotspot

--> Option: Detail my location: either via Bluetooth or by manual pinnning

-> Notify ME if others are already at the hotspot where I entered


## Links
	https://tub2go.tubit.tu-berlin.de/open/index.php?nav=mse&kto=LBS&pass=s!mey5ao&action=getPosInfo
