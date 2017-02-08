# Ajax

> Ajax module in Vanilla JS

<p align="center">
  <img src="ajax-logo.png" alt="Ajax" />
</p>

## Installation

Use it as [jqSlim](https://github.com/pwFoo/jqSlim) plugin. It's included to the [plugin directory](https://github.com/pwFoo/jqSlim/tree/master/plugins)

## Usage

As jqSlim plugin.

```js
$.ajax([options])
```

## Options

Optional object with request options. See all accepted options below.

**HTTP Methods**

You may pass any HTTP method as you want, using `method` property:

```js
var request = ajax({
  method: 'options',
  url: '/api/users',
  data: {
    user: 'john'
  }
})

request.then(function (response) {...})
```

For using this kind of request, you must pass `url` property.

The property `data` is optional, but may used to pass any data via `body` on request.

**headers**

An object when `key` is a header name, and `value` is a header value.

```js
ajax({
  headers: {
    'content-type': 'application/json',
    'x-access-token': '123@abc'
  }
})
```

If `content-type` is not passed, `application/x-www-form-urlencoded` will be used.

**Note about uploads:**

If you need to upload some file, with `FormData`, use `content-type: null`.

## Return methods

### `then(response, xhrObject)`

> Promise that returns if the request was successful.

```js
ajax({...}).then(function (response, xhr) {
  // Do something
})
```

### `catch(responseError, xhrObject)`

> Promise that returns if the request has an error.

```js
ajax({...}).catch(function (response, xhr) {
  // Do something
})
```

### `always(response, xhrObject)`

> That promise always returns, independent if the status is `done` or `error`.

```js
ajax({...}}).always(function (response, xhr) {
  // Do something
})
```

## Abort request

If a request is very slow, you can abort it using `abort()` method:

```js
const getLazyUser = ajax({...})

const timer = setTimeout(function () {
  getLazyUser.abort()
}, 3000)

getLazyUser.then(function (response) {
  clearTimeout(timer)
  console.log(response)
})
```

In the above example, if request is slowest than 3 seconds, it will be aborted.

## Browser compatibility

![Chrome][chrome-logo] | ![Firefox][firefox-logo] | ![IE][ie-logo] | ![Edge][edge-logo] | ![Opera][opera-logo] | ![Safari][safari-ios-logo]
---                    | ---                      | ---            | ---                | ---                  | ---
Latest ✔               | Latest ✔                 | 9+ ✔           | Latest ✔           | Latest ✔             | 3.2+ ✔
