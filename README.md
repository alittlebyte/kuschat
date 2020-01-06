# kustalk

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Description
Small chat built upon an existing websocket. <br/>
Receives data in {'text':...} objects, sends back {'created':... ,'name':... ,'text':...} ones <br/>
Decided not to use vue-router to separate login system, since it's much easier to pass the props around inside a single component - but it's doable.
