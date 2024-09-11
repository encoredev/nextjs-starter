# Next.js + Encore TS Web App Starter

This is an [Encore](https://encore.dev/) + [Next.js](https://nextjs.org/) project starter. It's a great way to learn how to combine Encore's backend 
capabilities with a modern web framework — perfect for building a web app.

## Clone this example

Go through the following steps to clone this starter:

1. When you have [installed Encore](https://encore.dev/docs/install), clone this repo:

```bash
git clone --depth=1 https://github.com/encoredev/nextjs-starter.git
```

2. Install backend dependencies and create a new Encore application:

```bash
cd nextjs-starter/backend
npm install      # Install dependencies
encore app init  # Create a new Encore application. Take note of the App ID
```

3. Run your Encore application (keep it running):

```bash
encore run # Inside the backend directory
```

4. In the `frontend/package.json`, replace `{{ENCORE_APP_ID}}` with the ID of your Encore application. You can see the app id in the `encore.app` file.


5. Open a new terminal window and generate a new request client:
    
```bash
npm run gen # Inside the frontend directory
```

### Running locally

Run your Encore backend:
```bash
encore run # Inside the backend directory
```

In a different terminal window, run the Next.js frontend:
```bash
cd frontend
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to see the result.

### Encore's Local Development Dashboard

While `encore run` is running, open <http://localhost:9400/> to view Encore's local developer dashboard.
Here you can see the request you just made and a view a trace of the response.

### Generating a request client

Keep the contract between the backend and frontend in sync by regenerating the request client whenever you make a change
to an Encore endpoint.

In the `gen` npm scripts, replace `next-js-test-ts-9wvi` with the ID of your Encore application.

```bash
npm run gen # Will create a new request client frontend/app/lib/client.ts
```

## Deployment

### Encore

Follow these steps to deploy your backend to a staging environment in Encore's free development cloud.

1. Create a GitHub repo, commit and push the app.
2. Open your app in the Encore [Cloud Dashboard](https://app.encore.dev).
3. Go to your app settings and set the "Root Directory" to `backend`. We need to do this because the `encore.app` file is not in the repo root.
4. In the settings as well, link your app to GitHub and select the repo you just created.
5. Commit and push a change (can be anything) to GitHub to trigger a deploy.

You can follow the deploy in the Cloud Dashboard. When the deploy is complete, your app will be available in the cloud.

### Next.js on Vercel

1. Create a repo and push the project to GitHub.
2. Create a new project on Vercel and point it to your GitHup repo.
3. Select `frontend` as the root directory for the Vercel project.

## CORS configuration

If you are running into CORS issues when calling your Encore API from your frontend then you may need to specify which
origins are allowed to access your API (via browsers). You do this by specifying the `global_cors` key in the `encore.app`
file, which has the following structure:

```js
global_cors: {
  // allow_origins_without_credentials specifies the allowed origins for requests
  // that don't include credentials. If nil it defaults to allowing all domains
  // (equivalent to ["*"]).
  "allow_origins_without_credentials": [
    "<ORIGIN-GOES-HERE>"
  ],
        
  // allow_origins_with_credentials specifies the allowed origins for requests
  // that include credentials. If a request is made from an Origin in this list
  // Encore responds with Access-Control-Allow-Origin: <Origin>.
  //
  // The URLs in this list may include wildcards (e.g. "https://*.example.com"
  // or "https://*-myapp.example.com").
  "allow_origins_with_credentials": [
    "<DOMAIN-GOES-HERE>"
  ]
}
```

More information on CORS configuration can be found here: https://encore.dev/docs/develop/cors

## Learn More

- [Encore Documentation](https://encore.dev/docs)
- [Next.js Documentation](https://nextjs.org/docs)
