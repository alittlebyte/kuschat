### Description
Small chat built upon an existing websocket. <br/>
The socket receives data in {'text':...} objects, sends back {'created':... ,'name':... ,'text':...} ones <br/>
Decided not to use vue-router to separate login system, since it's much easier to pass the props around inside a single component - but it's doable.<br/>
Nothing impressive, just polished. Also, this taught me more about the way Websockets work. </br>
For example, I can't deploy the built version on GitHub pages - I'm forced to use https://, and the websocket doesn't have a wss:// variant, so connection gets refused.

### Download the dependencies with this
```
npm install
```

### Launch with this
```
npm run serve
```
