##Innsights API

***

Overview
---------

Innsights is the service that gives you the power to answer:  

* What are your users doing?  
* Which ones are behaving the way you want?  
* How can you replicate this behavior?  

Innsights answers these questions by giving you an easy way to track the features in your application, the users getting involved with those features and the characteristics of those users.

Authentication
--------------

You authenticate to the Innsights API by providing a given authenticity token. Each app will be given a different token but each token will remain the same among the distinct app environments.

The authenticity token can be found in the **App Configuration** section.

![Authenticity Token](screenshots/auth_innsights.png)  

API Services
--------------

* [<code>GET</code> *Timeline*](https://github.com/innku/innsights-docs/blob/master/services/timeline.md)

*  [<code>GET</code> *Group*](https://github.com/innku/innsights-docs/blob/master/services/group.md)

*  [<code>POST</code> *Event*](https://github.com/innku/innsights-docs/blob/master/services/event.md)

*  [<code>GET</code> *Scoreboard*](https://github.com/innku/innsights-docs/blob/master/services/scoreboard.md)
    -  [*Users*](https://github.com/innku/innsights-docs/blob/master/services/scoreboard.md)

    -  [*Resources*](https://github.com/innku/innsights-docs/blob/master/services/scoreboard.md)

Get involved
------------

Please feel free to tell us how we can improve our API. If you have any specific feature request or if you've found a bug, please use **GitHub issues**. Fork these docs and send a pull request with improvements.
