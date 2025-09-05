This library defines a set of resources that are commonly used in API specifications. This helps to standardize API definitions as well as to avoid writing a lot of boilerplate definitions.

## Security Schemes
This library defines two different security schema type:

### Token
This security scheme called Token, The Client ID Enforcement policy restricts access to a protected resource by allowing requests only from registered client applications. The policy ensures that the client credentials sent on each request have been approved to consume the API.

When a client application is registered in Anypoint Platform, a pair of credentials consisting of a client ID and client secret is generated. When the client application requests access to an API, a contract is created between the application and that API. An API that is protected with a Client ID Enforcement policy is accessible only to applications that have an approved contract.

When you apply a Client ID Enforcement policy, access to your API is tracked by reporting the client ID along with the analytics events. You can configure Mule runtime engine (Mule) to encrypt all sensitive information that pertains to policies, contracts, and initialization data.

## Traits
Trait Name  | Description	  | Typical Usage
---|---|---
ErrorResponses  | Defines a comprehensive set of error response codes | Add to any endpoint definition
Pageable  | Defines attributes used for result set paging | Apply to a GET method that supports pagination
Trackable | Defines a header for supplying tracking information | Apply to any endpoint for end-to-end traceability

## Data types
Type Name | Description | Typical Usage
---|---|---
ErrorResponse | Defines a comprehensive set of error response codes | Add to any endpoint definition

## Usage
To use one or more of these resources in your API definition, first add this library as an Exchange dependency to your Design Center project so that you can import it into your main RAML file. For example:

```
uses: 
  CommonResources: exchange_modules/<groupid>/core-library/1.0.0/core-library.raml
```  
You can then add the appropriate trait(s) to your endpoints as follows:

```
/accounts:
  description: Find one or more accounts matching a given set of criteria
  is: [ CommonResources.ErrorResponses ]
  securedBy: [ CommonResources.Token ]
```