### Description
Small chat built upon an existing websocket. <br/>
The socket receives data in {'text':...} objects, sends back {'created':... ,'name':... ,'text':...} ones <br/>
Decided not to use vue-router to make Login a separate component, since it would only hinder the ability to pass props around - but it's doable.<br/>
Nothing impressive, just polished. Also, this taught me more about the way Websockets work. </br>
For example, I can't deploy the built version on GitHub pages - I'm being forced to use https://, and the websocket doesn't have a wss:// variant, so connection gets refused. </br>
If the websocket was changed to another one that is secure, there are two tweaks to be made, so this becomes deployable: </br>
- switch the webpack-npm build output location from /dist to /docs, obviously; </br>
- go into the created index.html and delete all the first slashes in every script and src. Courtesy of https://medium.com/@mwolfhoffman/deploying-to-github-pages-with-vue-webpack-cli-5b2ba17f14a0

### Download the dependencies with this
```
npm install
```

### Launch with this
```
npm run serve
```
