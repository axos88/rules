---
gallery: true
short_description: In a SAML application customize the mapping between the Auth0 user and the SAML attributes
categories:
- enrich profile
---
## SAML Attributes mapping

If the application the user is logging in to is SAML (like Salesforce for instance), you can customize the mapping between the Auth0 user and the SAML attributes.
Below you can see that we are mapping `user_id` to the NameID, `email` to `http://schemas.../emailaddress`, etc.

For more information about SAML options, look at <https://docs.auth0.com/saml-configuration>.

```js
function (user, context, callback) {
  context.samlConfiguration.mappings = {
     "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier": "user_id",
     "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress":   "email",
     "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name":           "name",
     "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/food":           "user_metadata.favorite_food",
     "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/address":        "app_metadata.shipping_address"
  };

  callback(null, user, context);
}
```
