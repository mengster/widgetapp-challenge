# WidgetApp Admin Guide

## What's new: Streaming

WidgetApp now features _Streaming_, which allows multiple users to work on the same Thing simultaneously. 

### Streaming Front End (SFE)

Streaming is powered by a **Streaming Front End** (SFE) that:
 
- enables multiple sessions from multiple users to the same Thing
- propagates changes from each user to all sessions, as quickly as possible

Each user session is authenticated using the same methods supported by WidgetApp. 

### Developer access to the Streaming

The underlying **Streaming API** also allows third-party WidgetApp developers to programmatically interface with the feature's functions. You can grant developers access to this API through OAuth2.0 access tokens.

The Streaming API also uses port 200 to transmit API messages. Ensure that external systems using the Streaming API can listen in on this port.

### Managing Streaming load

Streaming launches two separate processes on your WidgetApp server, namely `_sfe` and `_stream`. Both processes add server load on top of other WidgetApp processes.

On startup, WidgetApp launches one `_sfe`; it launches another SFE to run in parallel for every 10 Streaming API clients. We strongly recommend that you monitor `_sfe` and `_stream` processes for resource usage; if any start consuming over 50% load, restart them.

To restart an `_sfe` process, run:

`widgetapp_admin -process _sfe -n <num_instances> -start`

Note: Restarting an `_sfe` process automatically kills `_stream` processes for existing connections.


