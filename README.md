# kuschat
Small chat built upon an existing Websocket.
Receives data in {'text':...} objects, sends back {'created':.. ,'name':... ,'text':...}. Decided to go without vue-router for the login part - easier to pass props around inside a single component than between two child ones.
