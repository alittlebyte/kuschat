# kuschat
Small chat built upon an existing Websocket. <br/>
Receives data in {'text':...} objects, sends back {'created':.. ,'name':... ,'text':...}. <br/>
Decided to go without vue-router for the login part - easier to pass props around inside a single component, than between two child ones.
