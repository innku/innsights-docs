##Group

Description
-----------
Return a listing of points representing a group of actions. Each point represent the number of occurrences of a specific action in a time period.

Parameters
-----------
*  `scope` — Fraction of information based on some criteria. You can fraction your information by `event` or by `metric`. Aditional you can delimitate it by `user` or by `resource`.
    - _Possible values_ :
	`scope['event']['name'] = "My event"` \*  
	`scope['metric']['name'] = "My metric"` \*  
	`scope['user']['id'] = "User_id"`  
	`scope['resources']['MyResourceName']['id'] = "MyResource_id"`  
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

*  `of` — Actions to group.
    - _Possible Values_ :
	`of[] = "My Action1"`
	`of[] = "My Action2"`
		.
		.
		.
	`of[] = "My ActionN"`
 

***NOTE*** : `env` doesn't have a default value.

Request
-------
*  `GET /group.json`

```
curl -H "Content-Type:application/json" -H "Accept:application/json"
"http://api.innsights.me/groups.json?authenticity_token=12345&env=production&timeframe=week&ago=5&by=day&of[]=myaction1&of[]=myaction2"
```

Response
---------
``` json  
{  
  {
     name: "March 18 - March 24",
     start: 1363564800,
     finish: 1364169599,
     total: 309,
     average: 44,
     active_users: 79,
     average_per_user: 3,
     points: 
       [
	{
	  name: "myaction1",
	  display: "My Action 1",
	  description: "",
	  points: 57,
	  rank: 1
	},
	{
	  name: "myaction2",
	  display: "My Action 2",
	  description: "",
	  points: 24,
	  rank: 2
	}
      ]
  }
}
```