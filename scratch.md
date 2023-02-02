# USER
non-technical domain experts in THINGS on how to use the app

- Multiple users can now work on the same Thing at the same time - the **Streaming Front End** (SFE) propagates changes as quickly as possible so all clients can see them. 

- Streaming API is authorized only for approved user groups - managed through OAuth2.0 access tokens

# ADMIN
technical support staff on how to install, configure, and maintain the web server

- Streaming API runs over websockets - different services can use the same websocket connection

- Streaming API is authorized only for approved user groups - managed through OAuth2.0 access tokens

- SFE and Streaming API processes add to server load
    - monitor `_sfe` and `_stream` processes for CPU, memory, etc. Restart any that go rogue (>~50% load)
    - Default is one SFE on startup, with another started in parallel for every 10 Streaming API clients
    - To restart `sfe` instances: `widgetapp_admin -process _sfe -n <num_instances> -start`
    - SFE restarts killed `_stream` processes automatically for existing connections

# API/DEV
for third-party developers on how to interface with WidgetApp programmatically

- Most user actions, like search or scrolling, work by calling `_ajax` endpoints

- Streaming API is authorized only for approved user groups - managed through OAuth2.0 access tokens

- Authentication is unchanged from previous versions - managed through the existing WidgetApp frontend (WFE)

- WFE handles existing API requests as per previous versions, but hands over to the new **Streaming Front End** (SFE).
  SFE then manages the session as per WFE, but with Streaming API capabilities.

- External systems connect using: [wss://www.widgetapp.com/_stream](wss://www.widgetapp.com/_stream)

- External systems that use SFE must listen on port 200 for stream messages from any `widgetaApp_useraction_xxx` APIs (`widgetApp_useraction_refresh()`, `widgetApp_useraction_edit()`, etc)

