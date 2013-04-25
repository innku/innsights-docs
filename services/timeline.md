##Timeline

Description
-----------
Returns a timeline for the number of registered events or metrics represented by a listing of points. Each point represents a time interval for a specific event.

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

***NOTE*** : `env` doesn't have a default value.

Request
-------
*  `GET /timeline.json`

```
curl -H "Content-Type:application/json" -H "Accept:application/json"
"http://api.innsights.me/timeline.json?authenticity_token=12345&env=production&timeframe=week&ago=0&by=day&scope%5Bevent%5D%5Bname%5D=MyEvent"
```

Response
---------
``` json  
{  
  "name":"This Week",
  "title":"MyEvent",
  "start":1365984000,
  "finish":1366329599,
  "total":0,
  "average":0,
  "active_users":0,
  "average_per_user":0,
  "points":
  [
    {
      "points":"0.0",
      "start":"2013-04-15T00:00:00Z",
      "finish":"2013-04-15T23:59:59Z",
      "start_uts":1365984000,
      "finish_uts":1365984000
    },
            .
            .
            .
  ],
  "previous":
  {
    "total":0,
    "average":0,
    "active_users":0,
    "average_per_user":0
  },
  "scoreboards":
  {
    "user":
    {
      "points":[]
    },
    "group":
    {
      "points":[]
    }
  }
}
```

***NOTE*** : In this case, timeline service would return a list containing 4 points. Because the finish date is before the week is over, from Monday to Thursday there are 4 days. In other case, if today were friday, timeline service would be returning a list with 5 points, and so on.