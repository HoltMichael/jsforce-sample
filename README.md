# jsforce-sample

**THIS IS A COPY OF JOSH BIRK'S JSFORCE SAMPLE FOUND AT https://github.com/jsforce/jsforce**
**This quickly hacked together example uses oauth2, rather than the username/password config file in Josh's example.**

To use this sample, first create a Connected App in Salesforce and get the Client ID (Consumer Key) and Client Secret (Consumer Secret). 
Set the oauth scopes to:
Full access (full)
Perform requests at any time (refresh_token, offline_access)

Set the Callback URL to login.salesforce.com
Then go to:
https://login.salesforce.com/services/oauth2/authorize?response_type=code&client_id=<!!Consumer Key!!>&redirect_uri=https://login.salesforce.com

Get the code from the URL and decode, eg. here: https://www.urldecoder.org/

Get an access token and refresh token, using the following in eg. Postman:
POST https://login.salesforce.com/services/oauth2/token?
grant_type: Authorization Code 
client_id: [Connected App Consumer Key]
client_secret: [Connected App Consumer Secret]
code: [decoded code]
redirect_uri: https://login.salesforce.com/

Hit send and the response will return an access_token and refresh_token param. Paste them into index.js, along with the clientId, ClientSecret and instance URL.


# Josh's description below
This is a simple interactive demonstration of how to use Salesforce with Node.js via a library called jsforce.  jsforce can be run via command line or used with server side solutions like express.

Node is required, obviously: https://nodejs.org/en/

You will also want a Developer Edition org (which are free and do not have a fixed expiration): https://developer.salesforce.com/signup

Then to install and run:

1. Clone or download this repository
2. In the repository directory run **npm install -local**
3. Modify config.json with the username and password for your Developer Edition.
4. Run **node index.js displayContactsSOQL** to see a list of contacts from your instance.

index.js will accept:
* displayContactsSOQL
* displayContactsEventMethod
* displayContactsMethodChain
* createContact
* updateContact
* deleteContact

In config.json, you can also set "deployToWeb" to be true to see a sample API call via express at /contacts.

If you are using a scratch org or sandbox, add "production" to config.json and set it to false.

All variables can be handled as environment variables as well, which will override config.json.

Comments within index.js point to specifics about the code.  Full documentation for jsforce can be found on the project site: https://jsforce.github.io/

To learn more about developing on the Salesforce Platform, see the Beginner Developer trail on Trailhead: https://trailhead.salesforce.com/content/learn/trails/force_com_dev_beginner

## Deploying to Heroku via CLI

1. Sign up and install Heroku: [https://signup.heroku.com/](https://signup.heroku.com/)
1. Clone this repo.
1. Login via command line: **heroku login**.
1. In the repo directory (**cd jsforce-sameple**), run **heroku create**.
1. Run **git push heroku master**.
1. Run **herou open**.

## Deploying to Heroku via Deploy Button

1. Make sure you are logged in to the [Heroku Dashboard](https://dashboard.heroku.com/)
1. Click the button below to deploy on Heroku:

    [![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)




