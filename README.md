# Module 4, Week 3, Day 2: Express and Helmet

This exercise demonstrates adding security response headers to an Express app with Helmet. It follows the lesson's route, JSON response, port 3000, and app.use(helmet()) middleware.

## Run

```sh
cd express-helmet-app
npm install
npm start
```

Open http://localhost:3000. The response is:

```json
{"res":"Sending 200 as response"}
```

## Check the headers

1. Open Developer Tools and select Network.
2. Refresh localhost:3000 and select the document request.
3. Check the 200 status and inspect Response Headers.
4. Helmet adds Content-Security-Policy, X-Content-Type-Options, X-Frame-Options, and Referrer-Policy. X-Powered-By is absent.

For the before-and-after demonstration, temporarily comment out app.use(helmet());, restart the app, and inspect the headers. Restore the line and restart for the final version.

## Verified results

Both versions returned HTTP 200 with the same JSON body. Baseline Express advertised X-Powered-By: Express. Helmet removed that header and added X-Content-Type-Options: nosniff, X-Frame-Options: SAMEORIGIN, and Content-Security-Policy. Captured responses are in verification.json.

## Why secure HTTP headers?

Response headers influence browser security behavior. They can restrict resource loading, reduce framing and content-type confusion risks, and limit referrer information. Removing X-Powered-By reduces unnecessary disclosure of the framework. Helmet is one layer of protection; it does not replace input validation, safe output handling, authentication, or HTTPS.

## Version note

The lesson includes older Helmet features. Current Helmet does not implement every item on that slide: Public-Key-Pins and Expect-CT are obsolete, and Helmet sets X-XSS-Protection to 0 to disable legacy browser filters. Compare the actual headers rather than expecting an exact match to the slide.

Official reference: https://helmet.js.org/

## Submission

Post https://github.com/Declan-101/m4-w3-d2-exercise to the GAP Week 7 Day 2 Exercise assignment. GAP submission is a separate step.
