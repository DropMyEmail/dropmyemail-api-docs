---
layout: default
title: "Dropmyemail API"
---

## Dropmyemail API Version 1

Welcome to Dropmyemail API! This site describes __version 1__ of Dropmyemail API. You will be shown how to create an app using Dropmyemail API. If you should have any problems, please contact [support](mailto:support@dropmyemail.com).

### Current Version: 1.3.1

### What the API can do

You will be able to do the following:

- Add email accounts for backup
- Remove email accounts from backup
- Migrate email accounts
- Restore email accounts
- Retrieve the email messages

And much more. Do visit the detailed documentation for a better picture on what the API can do.

### Things to Note

Currently the API is partial complete. We also do not support backup and migrate for Gmail/Google apps email accounts at the moment. We will definitely add support for Gmail/Google email accounts very soon. Do check back often for updates.

#### JSON endpoints

We only offer our endpoints in [JSON](http://en.wikipedia.org/wiki/JSON). Please make your requests in JSON. Our responses will also be in JSON. We don't foresee adding more formats in future.

#### Security

All responses are encrypted in SSL via __https__

#### Rate limiting

There is a rate limit of 20 requests per second. Please contact us at [support@dropmyemail.com](mailto:support@dropmyemail.com) if you need to raise your limit.

#### OAuth 2 authentication

Our authentication is done via [OAuth 2](http://oauth.net/2). Read the __Getting Started__ section below on how to authenticate your application.

Currently our access tokens do not expire.

### Getting Started

To get started you will need a Dropmyemail account. Then you need to create a Developer application from Dropmyemail.

#### Creating a Developer application

First, register an account at [Dropmyemail](www.dropmyemail.com). After getting a Dropmyemail account, log in. Go to __Account Settings > Applications__. You should see the __Applications__ page.

From the __Applications__ page, create a developer application by filling up the form and clicking __Register__. If successful, you will have an app with an __uid__ and a __secret__. Those credentials will be used in the authentication process.

### Authentication

In order to make API calls, your app has to get the permission to access the user's account. Your app has to direct the user to an authorization page, where the user will grant your app the permission. If permission is granted, your app has to retrieve the access token. After which you may make API calls using this access token. The sections below will step you through the whole authentication process to obtain an access token from the user.

#### Requesting authorization

We provide a web page for your user to authorize your application. Direct your user to the a URL of the format below.

```
http://www.dropmyemail.com/oauth/authorize?client_id=YOUR_APP_UID&redirect_uri=http://example.com/callback&response_type=code&scope=read+write
```

The URL contains a few parameters as explained below.

##### Client ID

This identifies your app. Replace the __client_id__ with your own developer application's __uid__.

##### Scopes

Currently, we offer the following scopes:

- read
- write

Scopes determine which API call your app can make. Replace __scopes__ with the scopes your app needs. Multiple scopes can be added together by using __+__ as a separator.

##### Redirect URI

This is the URL that your user will be redirected to after the authorization process. It also has to match the URL you used when registering the application.

After the user has authorized your app, you will be given an authorization token in the request parameter like the url below. You can make use of this token to request for the access token.

```
http://example.com/callback?code=abcdefg
```

#### Requesting the access token

The authorization token expires in 5 minutes. Within the 5 minutes, your app has to make a request for the access token. You can make a __POST__ request in the format below.

```
https://www.dropmyemail.com/oauth/token
```

##### Parameters

- client_id: Your app's uid
- client_secret: Your app's secret
- code: The authorization code
- grant\_type: authorization_code
- redirect_uri: http://example.com/callback

The redirect uri has to match the URL registered in your app. The response will be similar to below.

``` javascript
{
 "access_token": "de6780bc506a0446309bd9362820ba8aed28aa506c71eedbe1c5c4f9dd350e54",
 "token_type": "bearer",
 "expires_in": 7200,
 "refresh_token": "8257e65c97202ed1726cf9571600918f3bffb2544b26e00a61df9897668c33a1"
}
```

Your access token is now created. Save the access token so that you will be able to make API calls.

### Making API calls

When making calls, include the parameter __access_token__ in order to authenticate. An example of a __GET__ request looks like this

```
https://api.dropmyemail.com/v1/accounts?access_token=abcdefg
```

All requests should be directed to __https://api.dropmyemail.com__.

Visit the documentation to find out how to make API calls.
