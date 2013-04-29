##Scoreboard

Description
-----------
Returns a listing of ranked scores accomplished by a group of users or resources for a given event.

Parameters
-----------
*  `scope` — Fraction of information based on some criteria. You can fraction your information by `event` or by `metric`. Aditional you can delimitate it by `user` or by `resource`.
    - _Possible values_ :
	`scope['event']['name'] = "My event"` \*  
	`scope['metric']['name'] = "My metric"` \*  
	\* ***Note*** : You must specify at least one of these scopes (either by event or by metric).

*  `timeframe` — Period of time.
    - _Possible Values_ : week, month, year or history.
    - _Default_ : week.  

*  `ago` — Timeframe offset to be represented. 
    - _Possible Values_ : 0, 1, 2 ... n
    - _Default_ : 0  

*  `by` — Time interval for each point.
    - _Possible Values_ : day, week, month or year
    - _Default_ : day.  

*  `env` — App environment.
    - _Possible Values_ : development, staging or production.  

*  `authenticity_token` — Given token for your app. It can be found in **App Configuration** section.

***NOTE*** : `env` doesn't have a default value.

##USERS

Scoreboard by users.

Request
-------
*  `GET /users/scoreboard.json`

```
curl -H "Content-Type:application/json" -H "Accept:application/json"
"http://api.innsights.me/users/scoreboard.json?authenticity_token=12345&env=production&timeframe=week&ago=5&by=day&scope[event][name]=myevent"
```

Response
---------
``` json  
{
  "start": 1360540800,
  "finish": 1361145599,
  "points": 
    [
      {
	"id": 7,
	"display": "Username",
	"email": "mail@user.com",
	"points": 79,
	"rank": 1
      },
      {
	"id": 12,
	"display": "Username",
	"email": "mail@user.com",
	"points": 48,
	"rank": 2
      },
	.
	.
	.
      {
	"id": User_id,
	"display": "Username",
	"email": "mail@user.com",
	"points": 48,
	"rank": n
      }
    ]
}
```

##RESOURCES

Scoreboard by resources.

Request
-------

*  `GET /resources/resource_name/scoreboard.json`

```
curl -H "Content-Type:application/json" -H "Accept:application/json"
"http://api.innsights.me/resources/resource_name/scoreboard.json?authenticity_token=12345&env=production&timeframe=week&ago=5&by=day&scope[event][name]=myevent"
```

Response
--------
``` json  
{
  "start": 1360540800,
  "finish": 1361145599,
  "points": [
    {
      "id": 3,
      "display": "Resource_name",
      "points": 133,
      "rank": 1
    },
    {
      "id": 4,
      "display": "Resource_name",
      "points": 67,
      "rank": 2
    },
    {
      "id": 2,
      "display": "Resource_name",
      "points": 8,
      "rank": 3
    }
     .
     .
     .
  ]
}
```