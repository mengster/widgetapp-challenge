# Notes

## User guide

I didn't find a lot of information in the notes that I felt were relevant to end users. 
I felt that the only thing that mattered to them was the ability for multiple _end users_
to collaboratively work on the same _Thing_ (and also that they can start using it now).

I did think that the possibility of admins terminating Streaming sessions was relevant to them, though. It would be nice to add more info on how end-users can mitigate this, if possible.

## Admin guide

I found more content relevant to admins in the notes. Most of this info focused on managing access and load on the WidgetApp server. Namely:

- instructions for monitoring and terminating processes, as needed
- details enabling access to devs via access tokens
- info about what port devs will be listening on (ie. `200`)

I added a little bit of info about the SFE here because that helps provide context on the processes admins need to monitor.


## Developer guide

First, I thought it would be better to call this a "Developer guide". This would make it more consistent with the other guides, which focus on their target audience. 

I felt that all the info on this page were relevant to readers interested in building apps or otherwise integrating external services to use the Streaming API.

## Additional notes

* I was curious about the explicit connection URL in the notes (`wss://www.widgetapp.com/_stream`). Normally, a service hosted on-premises would use the customer's domain, and we would prescribe the URL pattern that devs can connect to. 

* The content I've submitted here would normally be an initial draft that would go through numerous rounds of technical review. 

* In general, I would also add links to existing relevant sources. For example:
  * In [Communicating with the SFE](./wn-api.md#communicating-with-the-sfe) I would have linked to any references listing WidgetApp user actions
  * In the [Streaming Front End (SFE)](./wn-api.md#streaming-front-end-sfe) I would also link to any existing information describing how the WFE works.