# Endpoints needed for user management

## Get information of current user
	GET /users/me

## Change user information
	PUT /users/me

## Delete user
	DELETE /users/me

## Login
	GET /login
	
## Logout
	GET /users/me/logout

## Set location information
	PUT /users/me/location

## Delete location information
	DELETE /users/me/location

## Get all groups of user
	GET /users/me/groups

## Create a group
	POST /users/me/groups

## Show groups information
	GET /users/me/groups/id

## Change groups information
	PUT /users/me/groups/id

## Delete specific group
	DELETE /users/me/groups/id

## Add user to groups
	POST /users/me/groups/id/users

## Remove user from list
	DELETE /users/me/groups/id/users/uid

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

### example for friends in the hotspot
	/hotspots/mensa/active_friends
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
