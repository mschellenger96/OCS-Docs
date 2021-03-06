---
uid: omfIngressSubsctriptions
---

Subscriptions 
=============


A Subscription is used to consume data from a topic. Multiple subscriptions can retrieve data from a single topic.

There are two types of Subscriptions with different behaviors. 

The API calls in this section are used to create and manipulate subscriptions.  

Standard Subscription 
---------------------

A Standard Subscription provides an endpoint for an external application to query. It maintains a bookmark into the topic queue and serves up data in sequence. 
Standard Subscriptions are not yet supported.


OCS Data Store Subscription 
---------------

An OCS Data Store Subscription retrieves data from a topic and writes it directly to a namespace in the OCS Data Store. 

Data Models 
-----------

Subscription information is contained in an object called Subscription which has the following format: 

| Property             | Type                    | Details                                |
|----------------------|-------------------------|----------------------------------------|
| Id                   | string                  | Unique Id generated by the API during  |
|                      |                         | creation.                              |
| Name                 | string                  | A friendly name for the Subscription.  |
| TopicId              | string                  | Unique Id for the Topic we are subscribing to. |
| TopicTenantId        | string                  | Identifies the owner of the Topic.     |
| TopicNamespaceId     | string                  | Identifies the namespace for the Topic |
| TenantId             | string                  | Identifies the owner of the Subscription. |
| NamespaceId          | string                  | Identifies the namespace for the Subscription |
| IsRevoked            | boolean                 | Revocation status of the Subscription. |
| Description          | string                  | Description of the Subscription.       |
| Type                 | integer                 | An enumeration where OCSDataStore=1, Standard=2  |
| CreatedDate          | string                  | The time that the Subscription was created. The string is formatted using ISO 8601 format. |
| Enabled              | boolean                 | Whether the topic exists or not        |

***************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions/count``
-------------------------------------------------

Get the number of subscriptions for a tenant.  

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace.   

**Returns**

An integer count of subscriptions. 

*****************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions?skip={skip}&count={count}``
---------------------------------------------

Get all subscriptions for a tenant. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``int skip``
  An optional parameter representing the zero-based offset of the first subscription to retrieve. If not specified, a default value of 0 is used. 
``int count``
  An optional parameter representing the maximum number of subscriptions to retrieve. If not specified, a default value of 100 is used.

**Returns**

An array of Subscription objects. 

*********************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions/{subscriptionId}``
---------------------------------------------------------------

Get a specific subscription. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``subscriptionId``
  Unique Id for the subscription. 

**Returns**

A Subscription object that was found. 

*************************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions/{subscriptionId}/{secondsUntilExpiration}``
---------------------------------------------------------------------------------------

Get a security token for a subscription. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``subscriptionId``
  Unique Id for the subscription. 
``secondsUntilExpiration``
  Integer number of seconds until the token expires. 

**Returns**

A token string for the subscription.

*****************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/subscriptions``
--------------------------------------------

Gets the default Access Control List for new subscriptions

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 

**Returns**

An AccessControlList object.

*******************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions/{subscriptionId}/accesscontrol``
--------------------------------------------

Gets the Access Control List for a particular subscriptions

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``subscriptionId``
  Unique Id for the subscription. 

**Returns**

An AccessControlList object.

*******************

``GET api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions/{subscriptionId}/owner``
--------------------------------------------

Gets the Owner Trustee for a particular subscriptions

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``subscriptionId``
  Unique Id for the subscription. 

**Returns**

A Trustee object.

*******************

``PUT api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions``
--------------------------------------------

Create or update a subscription. Only the name and description may be updated. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 

**Body**

A Subscription object. 

**Returns**

A Subscription object that was created or updated. 

*******************

``PUT api/tenants/{tenantId}/namespaces/{namespaceId}/accesscontrol/subscriptions``
--------------------------------------------
Updates the default Access Control List for new subscriptions

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 

**Body**

An AccessControlList object.

*******************

``PUT api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions/{subscriptionId}/accesscontrol``
--------------------------------------------

Updates the Access Control List for a particular subscriptions

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``subscriptionId``
  Unique Id for the subscription. 

**Body**

An AccessControlList object.

*******************

``PUT api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions/{subscriptionId}/owner``
--------------------------------------------

Updates the Owner Trustee for a particular subscriptions

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``namespaceId``
  Unique Id for the namespace. 
``subscriptionId``
  Unique Id for the subscription. 

**Body**

A Trustee object.

*******************

``DELETE api/tenants/{tenantId}/namespaces/{namespaceId}/subscriptions/{subscriptionId}``
-----------------------------------------------------------------

Delete a Subscription. 

**Parameters**

``tenantId``
  Unique Id for the tenant. 
``subscriptionId``
  Unique Id for the subscription. 
