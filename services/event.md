##Event

Description
-----------
Sets a new action or event. To set a new event you must provide at least the event name parameter.

Parameters
-----------

*  `authenticity_token` — Given token for your app. It can be found in **App Configuration** section.

*  `env` — App environment.
    - _Possible Values_ : development, staging or production.  

*  `event` — Information about the new event. 
    - _Possible Values_ :  
	`event['name'] = "MyNewAction"`  
	`event['user']['id'] = "User_id"`  
	`event['user']['display'] = "Username"`  
	`event['user']['email'] = "User_email"`  
	`event['resources']['resource_name']['id'] = "Resource_id"`  
	`event['resources']['resource_name']['display'] = "Resource_display"`  
	`event['metric']['metric_name'] = "Metric_value"`

***NOTES*** :

*  env doesn't have a default value.

*  In order to set a user to the new event you must provide at least:
     -  User email,
     -  User id and Username, **or**
     -  User id, Username and User email

*  In order to set a resource to the new event you must provide:
     -  Resource id **and** Resource display.
    

Request
-------
*  `POST /event.json`

```
curl -H "Content-Type:application/json" -H "Accept:application/json"
"http://api.innsights.me/event.json?authenticity_token=12345&env=development&event[name]=my_action&event[user][id]=1&event[user][display]=Username&event[user][email]=user@mail.com&event[resources][company][id]=10&event[resources][company][display]=MyCompany"
```

Response
---------
``` json  
{
  "name": "my_action",
  "user": 
   {
     "id": 1,
     "display": "Username",
     "email": "user@mail.com"
   },
  "resources": 
   {
     "company": 
      {
       "id": 10,
       "display": "MyCompany"
      }
   }
}
```
