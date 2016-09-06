# Step by step guide

## Account creation
- Create a Stamplay account and leave everything by default https://stamplay.com
- Create a Box account https://box.com
- Create an Auth0 account, disable all connections created by default at https://manage.auth0.com

## Create a Stamplay application
- Go to https://editor.stamplay.com/ and create a new application, save the `application id` for later.

## Create a Box application
- Go to https://app.box.com/developers/services and create a box application, save `client_id` and `client_secret`.

## Configure Box as an OAuth2 provider for Auth0
- Go to https://manage.auth0.com and under the `connections => social` section enable `box`, paste `client_id` and `client_secret` from the previous step
- Then go to the `clients` section and create a new client of type `Single Page Web Application`
  - Go to settings and save `client_id` and `client_secret` for the next step.
  - Set `https://<your-stamplay-application-id>.stamplayapp.com/auth/v1/auth0/callback` as callback URL.
  - Finally go to `connections` and enable `box` (configured in the previous step).

## Configure your Stamplay application
- Open https://editor.stamplay.com/ and edit the application you created previously, go to the `users => authentication` section and select `Auth0`, fill in your account domain and `client_id` and `client_secret` from the previous step.
- Then go to the `objects` section and create an object named `mood`, add two properties named `email` and `mood`.
- Browse the `snippets` section and see how the REST API works.

Now you can go to `https://<your-stamplay-application-id>.stamplayapp.com/auth/v1/auth0/connect` to check that the authentication flow works.

## Configure you web application
- Clone `git@github.com:alejofernandez/boxdevdemo.git`
- Find and replace `<your-stamplay-application-id>` with your stamplay application id in `index.html`, `stats.html`
- Install the `stamplay-cli`
  ```
  npm install -g stamplay-cli
  ```
- Deploy your project
  ```
  stamplay init
  ```
  You'll be prompted to enter your stamplay application id and your API key (located under `dashboard => settings`)
  ```
  stamplay deploy
  ```

## Test your application
open `https://<your-stamplay-application-id>.stamplayapp.com/` and `https://<your-stamplay-application-id>.stamplayapp.com/stats.html`

Or browse the existing live demo at
- https://boxdevdemo.stamplayapp.com
- https://boxdevdemo.stamplayapp.com/stats.html

### Credits
- clmtrackr by Audun Mathias - https://github.com/auduno/clmtrackr - Facial recognition library
- CanvasJS - http://canvasjs.com/ - Charts and graphics
