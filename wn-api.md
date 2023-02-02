# WidgetApp Developer Guide

## What's new: Streaming

WidgetApp now features _Streaming_, which allows multiple users to work on the same Thing simultaneously. You can programmatically interface with Streaming through its underlying **Streaming API**.

### Streaming Front End (SFE)

Streaming enables multiple users to establish separate and parallel sessions to the same Thing. Most user actions (like searching or scrolling) work through `_ajax` calls to the **Streaming Front End** (SFE). The SFE propagates changes from each user to all other users very quickly, allowing for real-time collaboration.

The existing **Widget Front End** (WFE) handles normal API requests when only one user is working on a Thing. Once another user accesses the same Thing, the SFE takes over all API requests from all users. The SFE will then manage all sessions, but with Streaming API capabilities.

### Communicating with the SFE

Streaming API calls are authenticated through OAuth2.0 access tokens. Ask your admin for one.

To connect an external system to the SFE, use the following URL:

[wss://www.widgetapp.com/_stream](wss://www.widgetapp.com/_stream)

External systems should listen on port 200 for messages from the Streaming API. This will include messages relating to normal WidgetApp user actions (such as `widgetApp_useraction_refresh()` and `widgetApp_useraction_edit()`) conducted over Streaming sessions.