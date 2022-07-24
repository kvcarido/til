# Adding Headers to a Fetch Request

Some APIs require some form of authentication in order to receive data. When learning how to use the [Nookipedia API](https://api.nookipedia.com), I had to request an API key and navigate through their documentation on how to authenticate through an HTTP request.

Their documentation states under **Header Parameters** that `X-API-KEY` is a required header and accepts a `string <uuid>`, which is the generated API key assigned to you. While testing the request using Postman, the tool's UI makes it pretty easy to figure out how to pass this required `key-value` header data.

As I'm building an Animal Crossing-related side project, I wanted to learn how to pass header parameters when using a `fetch` request in my JavaScript. After a few quick YouTube tutorial video scans, I gave this a try:

```javascript
const url = 'https://api.nookipedia.com/villagers'
const key = 'dont-expose-your-api-keys'

fetch (url, {
    headers: {
        'X-API-KEY': key
    }
})
.then(res => res.json()) // parse response from string to json
.then(data => console.log(data))
.catch(err => console.log(`error: ${err}`))
```

The `fetch` method accepts [two parameters](https://developer.mozilla.org/en-US/docs/Web/API/fetch#parameters), a `resource` (typically the API url) and a few `options`.

The `options` parameter is an object containing any custom settings that you want to apply to the request. In the example above, I'm including the header object containing `X-API-KEY` with the value of `key`, a string variable containing my API key.
