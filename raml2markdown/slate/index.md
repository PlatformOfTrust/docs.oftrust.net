--- 

title: Platform Of Trust Documentation 

language_tabs: 
   - shell 
   - java
   - python
   - javascript

toc_footers: 
   - <a href='https://developers.oftrust.net'>Developer Portal</a> 

includes: 
   - authentication
   - ontologies
   - errors 
   - feedback
   

search: true 

--- 


# Platform of Trust API Documentation


## What is Platform of Trust?

> Some instructions and tips to make your life easier (and less support requests to us): 

> - Endpoints related code examples are constructed against **SANDBOX environment `https://api-sandbox.oftrust.net/`**. 

> - In **PRODUCTION** use, change domain in api endpoints to `https://api.oftrust.net/`

> If you found a bug or missing information in the documentation, contact us at dev@oftrust.net or create an [issue in Github](https://github.com/PlatformOfTrust/docs/issues/new). 



Communally built Platform of Trust provides a trustworthy and easy-to-use surrounding where you can utilize a vast data pool and develop everyday services for your`
customers with the help from the developer community and without a need for pricey and time-consuming integrations.  
``
Platform of Trust has Finnish origins, but it’s built to expand globally through the network of built environment innovation hubs.

**Developer Portal**

Our [Developer Portal](https://developers.oftrust.net) is your one-stop-shop. From there you'll find getting started guides, use case descriptions and 

**Market place**

Market place is the bazaar to find more data products to use in application development. Visa versa, it is also the service where your data products are added during the integration process. 

# Getting started

## Auth Flow

It's typically a good idea to explain the whole authentication process, because even to this day not everyone is familiar with how they work. In a nutshell [this OAuth single page auth flow is what we use](https://www.oauth.com/oauth2-servers/single-page-apps/#authorization)

The basic flow of how it goes is:

1. user gets redirected from YOUR frontend to YOUR backend's `/login` endpoint or similar

2. the `/login` endpoint generates a `state` parameter for it's own security by e.g. signing the current timestamp with a secret from it's config

3. the `/login` endpoint redirects the user to the login portal with parameters that define the application the user is coming from (client_id, redirect_uri) as well as the state and that we're going to do a code exchange

4. login portal takes care of identifying the user

5. login portal sends user back to YOUR backend's "return url", e.g. `/login/complete` with the new code and the state you provided etc.

6. you validate the state seems valid, isn't too old, etc.

7. you send this code with your client secret to the authorization backend in a server to server -request and get back the actual login token

8. you set the token in a cookie (preferably with `httpOnly; secure; SameSite=strict`)


## Standards used

**Dates**: we use a subset of ISO-8601 - [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt). Example <code>2008-09-15T15:53:00+05:00</code>

**Core Ontology**: The Platform Of Trust core ontology can be found as a JSON-LD ontology file under [ontologies/pot.jsonld](https://github.com/PlatformOfTrust/standards/blob/master/ontologies/pot.jsonld).

Each identity type has their own context which
describes the attributes the identity has. The context file name gives a notion
of whether the context is for an `identity` or a `link`. 

The identity describes the real world identities, such as apartments, 
buildings, rooms etc. The links are the relations between identities. 
As an example, the `Tenant`-link can be applied between
a user identity and an apartment identity, meaning that the user is a tenant
in the apartment.

If only a link between identities is needed, without any kind
of role, the generic `link-link.jsonld` can be used 
[contexts/link-link.jsonld](https://github.com/PlatformOfTrust/standards/tree/master/contexts/link-link.jsonld).

Read more from [Github](https://github.com/PlatformOfTrust/standards/blob/master/README.md)

## Code Examples 

<aside class="warning">
All the documentation code examples use our sandbox environment. When you are done with testing, you should switch to production environment. Easiest way is to store API root url in variable and when needed, change it there. Thus the code examples contain API-root variable as an exmaple. 
</aside>


# OAuth

To make API requests, you need to authenticate to Upwork API. Currently, we support OAuth 2.0 authentication. All API requests MUST be signed following the RFC 5849 specification.


## Client credentials

For each application you develop, you need to obtain new client credentials. 
These include a client identifier and a client shared-secret. 
You can find these credentials at https://developers.oftrust.net/profile 
while logged into your account. 

You will receive a public and a private key for each client identifier and 
client shared-secret you API request.


## OAuth 2.0 workflow

## Get request token

**Endpoint**

POST /api/auth/v1/oauth/token/request

HTTPS is required. All the names of variables follow OAuth specification (see RFC 5849).

```python

import upwork
client = upwork.Client(public_key, secret_key, **credentials)
client.auth.get_request_token()

```
