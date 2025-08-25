# wearedev-obfuscator-api-proxy

A simple Vercel proxy to bypass CORS restrictions when using the [WeAreDevs Obfuscator API](https://wearedevs.net/api/obfuscate).

## Why?
The WeAreDevs API does not send CORS headers, so you cannot call it directly from the browser.  
This proxy allows your frontend (React, Next.js, etc.) to communicate with it safely.

### Note
- you guys can freely use my deployed vercel, but you can deploy your own vercel if you want too.

## Deploy on Vercel
1. Clone this repo or copy the `/api/obfuscate.js`, `vercel.json`, and `package.json` files.
2. Push to your GitHub/GitLab/Bitbucket.
3. Import the project into [Vercel](https://vercel.com/).
4. And deploy

## Usage
Send a POST request to your deployed Vercel URL:

```http
POST https://<your-vercel-app>.vercel.app/api/obfuscate
Content-Type: application/json

{
  "script": "print('hello world')"
}
````

### Example in JavaScript

```js
const response = await fetch('https://<your-vercel-app>.vercel.app/api/obfuscate', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ script: "print('Hello world!')" })
});

const data = await response.json();
console.log(data);
```

## CORS

* By default, this proxy allows all origins (`Access-Control-Allow-Origin: *`).
* You can lock it down by editing `api/obfuscate.js` and replacing `*` with your frontend domain.

```js
res.setHeader('Access-Control-Allow-Origin', 'https://yourdomain.com');
```

## License

MIT
