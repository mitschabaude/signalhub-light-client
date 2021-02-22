# signalhub-light-client

This is intended for users of [mafintosh/signalhub](https://github.com/mafintosh/signalhub). It only contains the client part, cleaned from external dependencies to be smaller and easier to bundle with modern ESM bundlers like [Snowpack](https://www.snowpack.dev/).


```sh
yarn add signalhub-light-client
```

## Usage

``` js
import signalhub from 'signalhub-light-client'
const hub = signalhub('my-app-name', 'http://yourhub.com')

hub.subscribe('my-channel', message => {
  console.log('new message received', message);
});

hub.broadcast('my-channel', {hello: 'world'})
```

## API

#### `hub = signalhub(appName, url)`

Create a new hub client. If you have more than one hub running specify them in an array

``` js
// more than one server currently not supported
let hub = signalhub('my-app-name', 'https://signalhub1.example.com')
```

The `appName` is used to namespace the subscriptions/broadcast so you can reuse the
signalhub for more than one app.

#### `hub.subscribe(channel, message => { /* do something */ })`

Subscribe to a channel on the hub. `message` can be any output of `JSON.parse`.

#### `hub.broadcast(channel, message)`

Broadcast a new message to a channel on the hub. Messages have to be JSON-serializable.

#### `hub.close()`

Close all subscriptions

## License

MIT
