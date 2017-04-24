---
title: appdirect v289.0-SNAPSHOT
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - python: Python
  - ruby: Ruby
  - java: Java
toc_footers: []
includes: []
search: true
highlight_theme: darkula
---

# appdirect v289.0-SNAPSHOT

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

The Product APIs return every developer-configured detail about one or more marketplace products. No authentication is required for any of the Product APIs except Read a product's status, which returns data in the context of the current user's account.<br/><br/>
The List Products API returns all products and their associated details available on your marketplace. Included in those details are the applicationID and the vendorID. One of these IDs is a required parameter to use any of the other product APIs.

Base URL = <a href="http://appdirect.com/api">http://appdirect.com/api</a>


License: <a href="http://www.apache.org/licenses/LICENSE-2.0">Apache License, Version 2.0</a>

# Product

## Read staging catalog

> Code samples

````shell
# You can also use wget
curl -X get http://appdirect.com/api/channel/v1/stagingCatalog \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json'

````

````http
GET http://appdirect.com/api/channel/v1/stagingCatalog HTTP/1.1
Host: appdirect.com
Content-Type: application/json
Accept: application/json

````

````javascript
var headers = {
  'Accept':'application/json',
  'Content-Type':'application/json'

};

$.ajax({
  url: 'http://appdirect.com/api/channel/v1/stagingCatalog',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
````

````javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Content-Type':'application/json'

};

fetch('http://appdirect.com/api/channel/v1/stagingCatalog',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
````

````ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Content-Type' => 'application/json'
}

result = RestClient.get 'http://appdirect.com/api/channel/v1/stagingCatalog', params: {
  }, headers: headers

p JSON.parse(result)
````

````python
import requests
headers = {
  'Accept': 'application/json',
  'Content-Type': 'application/json'
}

r = requests.get('http://appdirect.com/api/channel/v1/stagingCatalog', params={

}, headers = headers)

print r.json()
````

````java
URL obj = new URL("http://appdirect.com/api/channel/v1/stagingCatalog");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
````

`GET /channel/v1/stagingCatalog`

*Read staging catalog*

This call lists all products in the Staging Catalog of your marketplace.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
appStatus|query|string|false|The status of the application, optional.
page|query|integer|false|The page number. Optional, defaults to 0.
productType|query|string|false|The product type, optional.
searchText|query|string|false|The search text, optional.
size|query|integer|false|The number of application returned. Optional, defaults to 20.
sortOrder|query|string|false|The order. Optional, default to ascending.
sortProperty|query|string|false|The sort field. Optional, defaults to the creation date of the application.


#### Enumerated Values

|Parameter|Value|
|---|---|
appStatus|DEVELOPMENT|
appStatus|PENDING|
appStatus|PRODUCTION|
productType|APPDIRECT_SERVICE|
productType|BUNDLE|
productType|CLOUDFOUNDRY_DEPLOYABLE|
productType|CLOUD_SERVICES|
productType|DESIGN_ELEMENT|
productType|DOMAIN_REGISTRATION|
productType|DOMAIN_RESELLER|
productType|DOWNLOAD|
productType|DOWNLOADABLE_BUNDLE|
productType|DOWNLOAD_WITH_FULL_PROFILE|
productType|EMBEDDED_VIDEO|
productType|EXTERNAL|
productType|MODULE|
productType|OPEN_SOURCE|
productType|RACKSPACE_IMAGE|
productType|STANDING_CLOUD|
productType|STATIC|
productType|SUPPORT|
productType|TEMPLATE|
productType|WEB_APP|
productType|WEB_APP_MANUAL_SETUP|
productType|WEB_APP_STACKED|
sortOrder|ASC|
sortOrder|DESC|

### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|a paginated list of Staging products.

> Example responses

````json
[
  {
    "applicationStatus": "...",
    "vendorUUID": "...",
    "href": "...",
    "id": 12345,
    "uuid": "...",
    "publishedApp": {
      "href": "...",
      "id": "..."
    },
    "workingApp": {
      "href": "...",
      "id": "..."
    },
    "name": "...",
    "type": "...",
    "provider": {
      "uuid": "...",
      "name": "...",
      "url": "..."
    },
    "listing": {
      "myAppLogoIconUrl": "...",
      "imageUrl": "...",
      "profileImageUrl": "...",
      "myAppLogoIconSrcset": {
        "property1": "...",
        "property2": "..."
      },
      "imageSrcset": {
        "property1": "...",
        "property2": "..."
      },
      "profileImageSrcset": {
        "property1": "...",
        "property2": "..."
      },
      "blurb": "...",
      "overview": "...",
      "rating": 12345,
      "reviewCount": 12345,
      "mobileBundleId": "...",
      "mobileAppStoreId": "..."
    },
    "overview": {
      "splashTitle": "...",
      "splashDescription": "...",
      "imageUrl": "...",
      "imageSrcset": {
        "property1": "...",
        "property2": "..."
      },
      "demoUrl": "...",
      "documentationUrl": "...",
      "downloadDocumentationUrl": "...",
      "systemRequirements": "...",
      "downloadFileSize": 12345,
      "benefit": [
        {
          "title": "...",
          "description": "..."
        },
        {
          "title": "...",
          "description": "..."
        }
      ],
      "versions": {
        "entry": [
          {},
          {}
        ]
      }
    },
    "support": {
      "email": "...",
      "phone": "...",
      "knowledgebaseUrl": "...",
      "description": "..."
    },
    "privacyUrl": "...",
    "termsUrl": "...",
    "referUrl": "...",
    "hostedLocation": "...",
    "lastModified": 12345,
    "pricing": {
      "edition": [
        {
          "uuid": "...",
          "rank": 12345,
          "name": "...",
          "primary": true,
          "trial": {},
          "expiredTrialGracePeriod": 12345,
          "bundleOnly": true,
          "targetAudience": "...",
          "code": "...",
          "defaultFreeTrial": true,
          "invisible": true,
          "leadGen": true,
          "lastModified": 12345,
          "revenueType": "...",
          "restricted": true,
          "freeTrialDuration": 12345,
          "freeTrialType": "...",
          "customerContractRestricted": true,
          "plan": [
            {},
            {}
          ],
          "bullet": [
            {},
            {}
          ],
          "item": [
            {},
            {}
          ],
          "customization": [
            {},
            {}
          ]
        },
        {
          "uuid": "...",
          "rank": 12345,
          "name": "...",
          "primary": true,
          "trial": {},
          "expiredTrialGracePeriod": 12345,
          "bundleOnly": true,
          "targetAudience": "...",
          "code": "...",
          "defaultFreeTrial": true,
          "invisible": true,
          "leadGen": true,
          "lastModified": 12345,
          "revenueType": "...",
          "restricted": true,
          "freeTrialDuration": 12345,
          "freeTrialType": "...",
          "customerContractRestricted": true,
          "plan": [
            {},
            {}
          ],
          "bullet": [
            {},
            {}
          ],
          "item": [
            {},
            {}
          ],
          "customization": [
            {},
            {}
          ]
        }
      ],
      "pricingSummary": "...",
      "footnote": [
        "...",
        "..."
      ],
      "bullet": [
        {
          "content": "...",
          "tooltip": "..."
        },
        {
          "content": "...",
          "tooltip": "..."
        }
      ]
    },
    "publishedOn": 12345,
    "rating": 12345,
    "numRatings": 12345,
    "buyable": true,
    "free": true,
    "freeTrialOrEditionPresent": true,
    "referable": true,
    "hidePricings": true,
    "collectLeads": true,
    "collectLeadsWithPurchaseEnabled": true,
    "newSubscriptionEnabled": true,
    "changeSubscriptionAllowed": true,
    "displayQuestions": true,
    "displayReviews": true,
    "oneClickPurchasable": true,
    "autoUpgradeToPaid": true,
    "downloadFileSize": 12345,
    "startingPrice": {
      "unit": "...",
      "billingFrequency": "...",
      "amount": {
        "AUD": 12345,
        "CAD": 12345,
        "CHF": 12345,
        "EUR": 12345,
        "GBP": 12345,
        "JPY": 12345,
        "KRW": 12345,
        "MXN": 12345,
        "MYR": 12345,
        "SEK": 12345,
        "SGD": 12345,
        "USD": 12345,
        "INR": 12345,
        "BRL": 12345,
        "DKK": 12345,
        "NZD": 12345,
        "NOK": 12345,
        "ZAR": 12345,
        "PHP": 12345,
        "CNY": 12345,
        "SAR": 12345,
        "GTQ": 12345
      },
      "discount": {
        "description": "...",
        "percentage": 12345,
        "startDate": 12345,
        "expirationDate": 12345,
        "numOfBillingCycles": 12345,
        "availableRedemptions": 12345,
        "amount": {},
        "pricingUnit": "TESTER"
      }
    },
    "highestPercentageDiscount": 12345,
    "highestFixedDiscount": {
      "AUD": 12345,
      "CAD": 12345,
      "CHF": 12345,
      "EUR": 12345,
      "GBP": 12345,
      "JPY": 12345,
      "KRW": 12345,
      "MXN": 12345,
      "MYR": 12345,
      "SEK": 12345,
      "SGD": 12345,
      "USD": 12345,
      "INR": 12345,
      "BRL": 12345,
      "DKK": 12345,
      "NZD": 12345,
      "NOK": 12345,
      "ZAR": 12345,
      "PHP": 12345,
      "CNY": 12345,
      "SAR": 12345,
      "GTQ": 12345
    },
    "bundledPlanIds": [
      12345,
      12345
    ],
    "customIntegration": "...",
    "usageType": "...",
    "linkedImportableApplicationUuid": "...",
    "liveChatEnabled": true,
    "liveChatAvailable": true,
    "showThirdPartyLegalDisclosure": true,
    "showSelfServiceRestriction": true,
    "integrationConfiguration": {
      "productSettings": {
        "validationUrl": "...",
        "preSubmitValidationRequired": true,
        "enabledForSubscriptionChange": true,
        "form": [
          {},
          {}
        ]
      }
    },
    "addon": true,
    "resource": [
      {
        "id": 12345,
        "resourceType": "...",
        "name": "...",
        "link": "...",
        "scribdKey": "...",
        "scribdId": "...",
        "description": "...",
        "resellerAccess": true
      },
      {
        "id": 12345,
        "resourceType": "...",
        "name": "...",
        "link": "...",
        "scribdKey": "...",
        "scribdId": "...",
        "description": "...",
        "resellerAccess": true
      }
    ],
    "screenshot": [
      {
        "name": "...",
        "imageUrl": "...",
        "imageUrlSrcset": {
          "property1": "...",
          "property2": "..."
        }
      },
      {
        "name": "...",
        "imageUrl": "...",
        "imageUrlSrcset": {
          "property1": "...",
          "property2": "..."
        }
      }
    ],
    "addonOffering": [
      {
        "id": 12345,
        "uuid": "...",
        "name": "...",
        "code": "...",
        "description": "...",
        "descriptionHtml": "...",
        "status": "...",
        "stacked": true,
        "exclusive": true,
        "paymentPlan": [
          {
            "href": "...",
            "id": 12345,
            "uuid": "...",
            "frequency": "...",
            "contract": {},
            "allowCustomUsage": true,
            "keepBillDateOnUsageChange": true,
            "separatePrepaid": true,
            "isPrimaryPrice": true,
            "tld": "...",
            "cost": [
              {},
              {}
            ],
            "discount": {}
          },
          {
            "href": "...",
            "id": 12345,
            "uuid": "...",
            "frequency": "...",
            "contract": {},
            "allowCustomUsage": true,
            "keepBillDateOnUsageChange": true,
            "separatePrepaid": true,
            "isPrimaryPrice": true,
            "tld": "...",
            "cost": [
              {},
              {}
            ],
            "discount": {}
          }
        ],
        "bullet": [
          {
            "content": "...",
            "tooltip": "..."
          },
          {
            "content": "...",
            "tooltip": "..."
          }
        ]
      },
      {
        "id": 12345,
        "uuid": "...",
        "name": "...",
        "code": "...",
        "description": "...",
        "descriptionHtml": "...",
        "status": "...",
        "stacked": true,
        "exclusive": true,
        "paymentPlan": [
          {
            "href": "...",
            "id": 12345,
            "uuid": "...",
            "frequency": "...",
            "contract": {},
            "allowCustomUsage": true,
            "keepBillDateOnUsageChange": true,
            "separatePrepaid": true,
            "isPrimaryPrice": true,
            "tld": "...",
            "cost": [
              {},
              {}
            ],
            "discount": {}
          },
          {
            "href": "...",
            "id": 12345,
            "uuid": "...",
            "frequency": "...",
            "contract": {},
            "allowCustomUsage": true,
            "keepBillDateOnUsageChange": true,
            "separatePrepaid": true,
            "isPrimaryPrice": true,
            "tld": "...",
            "cost": [
              {},
              {}
            ],
            "discount": {}
          }
        ],
        "bullet": [
          {
            "content": "...",
            "tooltip": "..."
          },
          {
            "content": "...",
            "tooltip": "..."
          }
        ]
      }
    ],
    "featuredCustomer": [
      {
        "id": 12345,
        "name": "...",
        "logoUrl": "..."
      },
      {
        "id": 12345,
        "name": "...",
        "logoUrl": "..."
      }
    ],
    "featuredMedium": [
      {
        "link": "...",
        "linkDescription": "...",
        "source": {
          "id": 12345,
          "name": "...",
          "logoUrl": "..."
        }
      },
      {
        "link": "...",
        "linkDescription": "...",
        "source": {
          "id": 12345,
          "name": "...",
          "logoUrl": "..."
        }
      }
    ],
    "feature": [
      {
        "id": 12345,
        "header": "...",
        "description": "...",
        "imageUrl": "...",
        "slogan": "...",
        "hideOnOverview": true,
        "position": 12345,
        "bullet": [
          {
            "title": "...",
            "position": 12345,
            "abovePicture": true,
            "highlight": [
              {},
              {}
            ]
          },
          {
            "title": "...",
            "position": 12345,
            "abovePicture": true,
            "highlight": [
              {},
              {}
            ]
          }
        ]
      },
      {
        "id": 12345,
        "header": "...",
        "description": "...",
        "imageUrl": "...",
        "slogan": "...",
        "hideOnOverview": true,
        "position": 12345,
        "bullet": [
          {
            "title": "...",
            "position": 12345,
            "abovePicture": true,
            "highlight": [
              {},
              {}
            ]
          },
          {
            "title": "...",
            "position": 12345,
            "abovePicture": true,
            "highlight": [
              {},
              {}
            ]
          }
        ]
      }
    ],
    "tag": [
      {
        "type": "...",
        "id": 12345,
        "name": "...",
        "badge": "...",
        "showBadge": true,
        "showOnNavigation": true,
        "tag": [
          {},
          {}
        ],
        "description": "..."
      },
      {
        "type": "...",
        "id": 12345,
        "name": "...",
        "badge": "...",
        "showBadge": true,
        "showOnNavigation": true,
        "tag": [
          {},
          {}
        ],
        "description": "..."
      }
    ],
    "language": [
      "...",
      "..."
    ],
    "mosiConnectorType": "MOSI",
    "platform": [
      {
        "uuid": "...",
        "attribute": [
          {
            "platformAttributeDefinitionUuid": "...",
            "uuid": "...",
            "lastModified": 12345,
            "createdOn": 12345,
            "platformAttributeOptionUuid": "...",
            "applicationPlatformUuid": "...",
            "value": "..."
          },
          {
            "platformAttributeDefinitionUuid": "...",
            "uuid": "...",
            "lastModified": 12345,
            "createdOn": 12345,
            "platformAttributeOptionUuid": "...",
            "applicationPlatformUuid": "...",
            "value": "..."
          }
        ],
        "platformDefinition": {
          "lastModified": 12345,
          "numTaggedProducts": 12345,
          "uuid": "...",
          "createdOn": 12345,
          "iconUrl": "...",
          "name": "...",
          "attributeDefinition": [
            {},
            {}
          ],
          "description": "...",
          "isVersionSupported": true
        }
      },
      {
        "uuid": "...",
        "attribute": [
          {
            "platformAttributeDefinitionUuid": "...",
            "uuid": "...",
            "lastModified": 12345,
            "createdOn": 12345,
            "platformAttributeOptionUuid": "...",
            "applicationPlatformUuid": "...",
            "value": "..."
          },
          {
            "platformAttributeDefinitionUuid": "...",
            "uuid": "...",
            "lastModified": 12345,
            "createdOn": 12345,
            "platformAttributeOptionUuid": "...",
            "applicationPlatformUuid": "...",
            "value": "..."
          }
        ],
        "platformDefinition": {
          "lastModified": 12345,
          "numTaggedProducts": 12345,
          "uuid": "...",
          "createdOn": 12345,
          "iconUrl": "...",
          "name": "...",
          "attributeDefinition": [
            {},
            {}
          ],
          "description": "...",
          "isVersionSupported": true
        }
      }
    ],
    "customAttributes": [
      {
        "value": "...",
        "label": "...",
        "attributeKey": "..."
      },
      {
        "value": "...",
        "label": "...",
        "attributeKey": "..."
      }
    ],
    "productRibbon": {},
    "_embedded": {
      "property1": {},
      "property2": {}
    },
    "links": [
      {
        "rel": "...",
        "href": "..."
      },
      {
        "rel": "...",
        "href": "..."
      }
    ]
  }
]
````
<aside class="success">
This operation does not require authentication
</aside>

## List all products

> Code samples

````shell
# You can also use wget
curl -X get http://appdirect.com/api/marketplace/v1/listing \
  -H 'Accept: application/xml' \
  -H 'Content-Type: application/xml'

````

````http
GET http://appdirect.com/api/marketplace/v1/listing HTTP/1.1
Host: appdirect.com
Content-Type: application/xml
Accept: application/xml

````

````javascript
var headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

$.ajax({
  url: 'http://appdirect.com/api/marketplace/v1/listing',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
````

````javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

fetch('http://appdirect.com/api/marketplace/v1/listing',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
````

````ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml',
  'Content-Type' => 'application/xml'
}

result = RestClient.get 'http://appdirect.com/api/marketplace/v1/listing', params: {
  }, headers: headers

p JSON.parse(result)
````

````python
import requests
headers = {
  'Accept': 'application/xml',
  'Content-Type': 'application/xml'
}

r = requests.get('http://appdirect.com/api/marketplace/v1/listing', params={

}, headers = headers)

print r.json()
````

````java
URL obj = new URL("http://appdirect.com/api/marketplace/v1/listing");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
````

`GET /marketplace/v1/listing`

*List all products*

This call lists products based on specific parameters such as attribute, category, date, or type.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
a|query|array[number]|false|Only return products for these attribute ids
approvalAfter|query|number|false|Search products published after this date in milliseconds
approvalBefore|query|number|false|Search products published before this date in milliseconds
c|query|array[number]|false|Only return products for these categories
count|query|integer|false|Limit number of products returned
filter|query|array[string]|false|Only return products for these characteristics
i|query|array[number]|false|Only return products for these sub category ids
order|query|string|false|Ordering type
pl|query|array[number]|false|No description
platform|query|array[string]|false|No description
q|query|string|false|Search term used to search on different fields of an product
s|query|array[number]|false|Only return products for these category ids
start|query|integer|false|Start to return product after this offset
type|query|array[string]|false|Only return product for these product types
vendor|query|array[string]|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
filter|DISCOUNT|
filter|FEATURED|
filter|FREE|
filter|FREE_TRIAL|
filter|PAID|
filter|POPULAR|
filter|STAFFPICK|
order|ALPHABETICAL|
order|NEWEST_FIRST|
order|NEWEST_PUBLISHED|
order|POPULARITY|
type|APPDIRECT_SERVICE|
type|BUNDLE|
type|CLOUDFOUNDRY_DEPLOYABLE|
type|CLOUD_SERVICES|
type|DESIGN_ELEMENT|
type|DOMAIN_REGISTRATION|
type|DOMAIN_RESELLER|
type|DOWNLOAD|
type|DOWNLOADABLE_BUNDLE|
type|DOWNLOAD_WITH_FULL_PROFILE|
type|EMBEDDED_VIDEO|
type|EXTERNAL|
type|MODULE|
type|OPEN_SOURCE|
type|RACKSPACE_IMAGE|
type|STANDING_CLOUD|
type|STATIC|
type|SUPPORT|
type|TEMPLATE|
type|WEB_APP|
type|WEB_APP_MANUAL_SETUP|
type|WEB_APP_STACKED|

### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of products

> Example responses

````json
[
  {
    "href": "...",
    "id": 12345,
    "uuid": "...",
    "url": "...",
    "name": "...",
    "productType": "...",
    "iconUrl": "...",
    "profileLogoUrl": "...",
    "iconSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "profileLogoSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "description": "...",
    "overview": "...",
    "startingPrice": "...",
    "channelStartingPrice": {
      "freeTrial": true,
      "free": true,
      "prices": {
        "property1": {
          "duration": "THREE_YEARS",
          "price": 12345
        },
        "property2": {
          "duration": "MONTHLY",
          "price": 12345
        }
      }
    },
    "billingFrequency": "...",
    "publishedOn": 12345,
    "developerName": "...",
    "vendorName": "...",
    "rating": 12345,
    "numRatings": 12345,
    "showRating": true,
    "overviewImageUrl": "...",
    "overviewImageSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "blurb": "...",
    "buyable": true,
    "free": true,
    "freeTrialOrEditionPresent": true,
    "referable": true,
    "hasLyncToPhone": true,
    "downloadFileSize": 12345,
    "hidePricings": true,
    "collectLeads": true,
    "addon": true,
    "featured": true,
    "featuredSliderPosition": 12345,
    "popular": true,
    "popularity": 12345,
    "staffPick": true,
    "staffPickSliderPosition": 12345,
    "discountDetails": {
      "discountedStartingPrice": "...",
      "startingPricePercentageDiscount": 12345,
      "highestPercentageDiscount": 12345,
      "highestFixedDiscount": {
        "AUD": 12345,
        "CAD": 12345,
        "CHF": 12345,
        "EUR": 12345,
        "GBP": 12345,
        "JPY": 12345,
        "KRW": 12345,
        "MXN": 12345,
        "MYR": 12345,
        "SEK": 12345,
        "SGD": 12345,
        "USD": 12345,
        "INR": 12345,
        "BRL": 12345,
        "DKK": 12345,
        "NZD": 12345,
        "NOK": 12345,
        "ZAR": 12345,
        "PHP": 12345,
        "CNY": 12345,
        "SAR": 12345,
        "GTQ": 12345
      }
    },
    "lastModified": 12345,
    "sortRank": 12345,
    "tag": [
      {
        "type": "...",
        "id": 12345,
        "name": "...",
        "badge": "...",
        "showBadge": true,
        "showOnNavigation": true,
        "tag": [
          {},
          {}
        ],
        "description": "..."
      },
      {
        "type": "...",
        "id": 12345,
        "name": "...",
        "badge": "...",
        "showBadge": true,
        "showOnNavigation": true,
        "tag": [
          {},
          {}
        ],
        "description": "..."
      }
    ],
    "bundleUrl": [
      "...",
      "..."
    ],
    "language": [
      "...",
      "..."
    ],
    "productRibbon": {}
  }
]
````
````xml
<?xml version="1.0" encoding="UTF-8" ?>
<href>...</href>
<id>12345</id>
<uuid>...</uuid>
<url>...</url>
<name>...</name>
<productType>...</productType>
<iconUrl>...</iconUrl>
<profileLogoUrl>...</profileLogoUrl>
<iconSrcset>
  <property1>...</property1>
  <property2>...</property2>
</iconSrcset>
<profileLogoSrcset>
  <property1>...</property1>
  <property2>...</property2>
</profileLogoSrcset>
<description>...</description>
<overview>...</overview>
<startingPrice>...</startingPrice>
<channelStartingPrice>
  <freeTrial>true</freeTrial>
  <free>true</free>
  <prices>
    <property1>
      <duration>THREE_YEARS</duration>
      <price>12345</price>
    </property1>
    <property2>
      <duration>MONTHLY</duration>
      <price>12345</price>
    </property2>
  </prices>
</channelStartingPrice>
<billingFrequency>...</billingFrequency>
<publishedOn>12345</publishedOn>
<developerName>...</developerName>
<vendorName>...</vendorName>
<rating>12345</rating>
<numRatings>12345</numRatings>
<showRating>true</showRating>
<overviewImageUrl>...</overviewImageUrl>
<overviewImageSrcset>
  <property1>...</property1>
  <property2>...</property2>
</overviewImageSrcset>
<blurb>...</blurb>
<buyable>true</buyable>
<free>true</free>
<freeTrialOrEditionPresent>true</freeTrialOrEditionPresent>
<referable>true</referable>
<hasLyncToPhone>true</hasLyncToPhone>
<downloadFileSize>12345</downloadFileSize>
<hidePricings>true</hidePricings>
<collectLeads>true</collectLeads>
<addon>true</addon>
<featured>true</featured>
<featuredSliderPosition>12345</featuredSliderPosition>
<popular>true</popular>
<popularity>12345</popularity>
<staffPick>true</staffPick>
<staffPickSliderPosition>12345</staffPickSliderPosition>
<discountDetails>
  <discountedStartingPrice>...</discountedStartingPrice>
  <startingPricePercentageDiscount>12345</startingPricePercentageDiscount>
  <highestPercentageDiscount>12345</highestPercentageDiscount>
  <highestFixedDiscount>
    <AUD>12345</AUD>
    <CAD>12345</CAD>
    <CHF>12345</CHF>
    <EUR>12345</EUR>
    <GBP>12345</GBP>
    <JPY>12345</JPY>
    <KRW>12345</KRW>
    <MXN>12345</MXN>
    <MYR>12345</MYR>
    <SEK>12345</SEK>
    <SGD>12345</SGD>
    <USD>12345</USD>
    <INR>12345</INR>
    <BRL>12345</BRL>
    <DKK>12345</DKK>
    <NZD>12345</NZD>
    <NOK>12345</NOK>
    <ZAR>12345</ZAR>
    <PHP>12345</PHP>
    <CNY>12345</CNY>
    <SAR>12345</SAR>
    <GTQ>12345</GTQ>
  </highestFixedDiscount>
</discountDetails>
<lastModified>12345</lastModified>
<sortRank>12345</sortRank>
<tag>
  <type>...</type>
  <id>12345</id>
  <name>...</name>
  <badge>...</badge>
  <showBadge>true</showBadge>
  <showOnNavigation>true</showOnNavigation>
  <tag/>
  <tag/>
  <description>...</description>
</tag>
<tag>
  <type>...</type>
  <id>12345</id>
  <name>...</name>
  <badge>...</badge>
  <showBadge>true</showBadge>
  <showOnNavigation>true</showOnNavigation>
  <tag/>
  <tag/>
  <description>...</description>
</tag>
<bundleUrl>...</bundleUrl>
<bundleUrl>...</bundleUrl>
<language>...</language>
<language>...</language>
<productRibbon/>
````
<aside class="success">
This operation does not require authentication
</aside>

## Retrieve a product

> Code samples

````shell
# You can also use wget
curl -X get http://appdirect.com/api/marketplace/v1/products/{applicationId} \
  -H 'Accept: application/xml' \
  -H 'Content-Type: application/xml'

````

````http
GET http://appdirect.com/api/marketplace/v1/products/{applicationId} HTTP/1.1
Host: appdirect.com
Content-Type: application/xml
Accept: application/xml

````

````javascript
var headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

$.ajax({
  url: 'http://appdirect.com/api/marketplace/v1/products/{applicationId}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
````

````javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

fetch('http://appdirect.com/api/marketplace/v1/products/{applicationId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
````

````ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml',
  'Content-Type' => 'application/xml'
}

result = RestClient.get 'http://appdirect.com/api/marketplace/v1/products/{applicationId}', params: {
  }, headers: headers

p JSON.parse(result)
````

````python
import requests
headers = {
  'Accept': 'application/xml',
  'Content-Type': 'application/xml'
}

r = requests.get('http://appdirect.com/api/marketplace/v1/products/{applicationId}', params={

}, headers = headers)

print r.json()
````

````java
URL obj = new URL("http://appdirect.com/api/marketplace/v1/products/{applicationId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
````

`GET /marketplace/v1/products/{applicationId}`

*Retrieve a product*

The product in the response will contains invisible editions in the following cases:
- You are using OAuth to access the endpoint
- The current user is a channel admin or a sales support
This call  returns all details about a specific product on your marketplace.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
applicationId|path|number|true|Application id


### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|product information

> Example responses

````json
{
  "href": "...",
  "id": 12345,
  "uuid": "...",
  "publishedApp": {
    "href": "...",
    "id": "..."
  },
  "workingApp": {
    "href": "...",
    "id": "..."
  },
  "name": "...",
  "type": "...",
  "provider": {
    "uuid": "...",
    "name": "...",
    "url": "..."
  },
  "listing": {
    "myAppLogoIconUrl": "...",
    "imageUrl": "...",
    "profileImageUrl": "...",
    "myAppLogoIconSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "imageSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "profileImageSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "blurb": "...",
    "overview": "...",
    "rating": 12345,
    "reviewCount": 12345,
    "mobileBundleId": "...",
    "mobileAppStoreId": "..."
  },
  "overview": {
    "splashTitle": "...",
    "splashDescription": "...",
    "imageUrl": "...",
    "imageSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "demoUrl": "...",
    "documentationUrl": "...",
    "downloadDocumentationUrl": "...",
    "systemRequirements": "...",
    "downloadFileSize": 12345,
    "benefit": [
      {
        "title": "...",
        "description": "..."
      },
      {
        "title": "...",
        "description": "..."
      }
    ],
    "versions": {
      "entry": [
        {},
        {}
      ]
    }
  },
  "support": {
    "email": "...",
    "phone": "...",
    "knowledgebaseUrl": "...",
    "description": "..."
  },
  "privacyUrl": "...",
  "termsUrl": "...",
  "referUrl": "...",
  "hostedLocation": "...",
  "lastModified": 12345,
  "pricing": {
    "edition": [
      {
        "uuid": "...",
        "rank": 12345,
        "name": "...",
        "primary": true,
        "trial": {},
        "expiredTrialGracePeriod": 12345,
        "bundleOnly": true,
        "targetAudience": "...",
        "code": "...",
        "defaultFreeTrial": true,
        "invisible": true,
        "leadGen": true,
        "lastModified": 12345,
        "revenueType": "...",
        "restricted": true,
        "freeTrialDuration": 12345,
        "freeTrialType": "...",
        "customerContractRestricted": true,
        "plan": [
          {},
          {}
        ],
        "bullet": [
          {},
          {}
        ],
        "item": [
          {},
          {}
        ],
        "customization": [
          {},
          {}
        ]
      },
      {
        "uuid": "...",
        "rank": 12345,
        "name": "...",
        "primary": true,
        "trial": {},
        "expiredTrialGracePeriod": 12345,
        "bundleOnly": true,
        "targetAudience": "...",
        "code": "...",
        "defaultFreeTrial": true,
        "invisible": true,
        "leadGen": true,
        "lastModified": 12345,
        "revenueType": "...",
        "restricted": true,
        "freeTrialDuration": 12345,
        "freeTrialType": "...",
        "customerContractRestricted": true,
        "plan": [
          {},
          {}
        ],
        "bullet": [
          {},
          {}
        ],
        "item": [
          {},
          {}
        ],
        "customization": [
          {},
          {}
        ]
      }
    ],
    "pricingSummary": "...",
    "footnote": [
      "...",
      "..."
    ],
    "bullet": [
      {
        "content": "...",
        "tooltip": "..."
      },
      {
        "content": "...",
        "tooltip": "..."
      }
    ]
  },
  "publishedOn": 12345,
  "rating": 12345,
  "numRatings": 12345,
  "buyable": true,
  "free": true,
  "freeTrialOrEditionPresent": true,
  "referable": true,
  "hidePricings": true,
  "collectLeads": true,
  "collectLeadsWithPurchaseEnabled": true,
  "newSubscriptionEnabled": true,
  "changeSubscriptionAllowed": true,
  "displayQuestions": true,
  "displayReviews": true,
  "oneClickPurchasable": true,
  "autoUpgradeToPaid": true,
  "downloadFileSize": 12345,
  "startingPrice": {
    "unit": "...",
    "billingFrequency": "...",
    "amount": {
      "AUD": 12345,
      "CAD": 12345,
      "CHF": 12345,
      "EUR": 12345,
      "GBP": 12345,
      "JPY": 12345,
      "KRW": 12345,
      "MXN": 12345,
      "MYR": 12345,
      "SEK": 12345,
      "SGD": 12345,
      "USD": 12345,
      "INR": 12345,
      "BRL": 12345,
      "DKK": 12345,
      "NZD": 12345,
      "NOK": 12345,
      "ZAR": 12345,
      "PHP": 12345,
      "CNY": 12345,
      "SAR": 12345,
      "GTQ": 12345
    },
    "discount": {
      "description": "...",
      "percentage": 12345,
      "startDate": 12345,
      "expirationDate": 12345,
      "numOfBillingCycles": 12345,
      "availableRedemptions": 12345,
      "amount": {},
      "pricingUnit": "JBOSS_FUSE"
    }
  },
  "highestPercentageDiscount": 12345,
  "highestFixedDiscount": {
    "AUD": 12345,
    "CAD": 12345,
    "CHF": 12345,
    "EUR": 12345,
    "GBP": 12345,
    "JPY": 12345,
    "KRW": 12345,
    "MXN": 12345,
    "MYR": 12345,
    "SEK": 12345,
    "SGD": 12345,
    "USD": 12345,
    "INR": 12345,
    "BRL": 12345,
    "DKK": 12345,
    "NZD": 12345,
    "NOK": 12345,
    "ZAR": 12345,
    "PHP": 12345,
    "CNY": 12345,
    "SAR": 12345,
    "GTQ": 12345
  },
  "bundledPlanIds": [
    12345,
    12345
  ],
  "customIntegration": "...",
  "usageType": "...",
  "linkedImportableApplicationUuid": "...",
  "liveChatEnabled": true,
  "liveChatAvailable": true,
  "showThirdPartyLegalDisclosure": true,
  "showSelfServiceRestriction": true,
  "integrationConfiguration": {
    "productSettings": {
      "validationUrl": "...",
      "preSubmitValidationRequired": true,
      "enabledForSubscriptionChange": true,
      "form": [
        {},
        {}
      ]
    }
  },
  "addon": true,
  "resource": [
    {
      "id": 12345,
      "resourceType": "...",
      "name": "...",
      "link": "...",
      "scribdKey": "...",
      "scribdId": "...",
      "description": "...",
      "resellerAccess": true
    },
    {
      "id": 12345,
      "resourceType": "...",
      "name": "...",
      "link": "...",
      "scribdKey": "...",
      "scribdId": "...",
      "description": "...",
      "resellerAccess": true
    }
  ],
  "screenshot": [
    {
      "name": "...",
      "imageUrl": "...",
      "imageUrlSrcset": {
        "property1": "...",
        "property2": "..."
      }
    },
    {
      "name": "...",
      "imageUrl": "...",
      "imageUrlSrcset": {
        "property1": "...",
        "property2": "..."
      }
    }
  ],
  "addonOffering": [
    {
      "id": 12345,
      "uuid": "...",
      "name": "...",
      "code": "...",
      "description": "...",
      "descriptionHtml": "...",
      "status": "...",
      "stacked": true,
      "exclusive": true,
      "paymentPlan": [
        {
          "href": "...",
          "id": 12345,
          "uuid": "...",
          "frequency": "...",
          "contract": {},
          "allowCustomUsage": true,
          "keepBillDateOnUsageChange": true,
          "separatePrepaid": true,
          "isPrimaryPrice": true,
          "tld": "...",
          "cost": [
            {},
            {}
          ],
          "discount": {}
        },
        {
          "href": "...",
          "id": 12345,
          "uuid": "...",
          "frequency": "...",
          "contract": {},
          "allowCustomUsage": true,
          "keepBillDateOnUsageChange": true,
          "separatePrepaid": true,
          "isPrimaryPrice": true,
          "tld": "...",
          "cost": [
            {},
            {}
          ],
          "discount": {}
        }
      ],
      "bullet": [
        {
          "content": "...",
          "tooltip": "..."
        },
        {
          "content": "...",
          "tooltip": "..."
        }
      ]
    },
    {
      "id": 12345,
      "uuid": "...",
      "name": "...",
      "code": "...",
      "description": "...",
      "descriptionHtml": "...",
      "status": "...",
      "stacked": true,
      "exclusive": true,
      "paymentPlan": [
        {
          "href": "...",
          "id": 12345,
          "uuid": "...",
          "frequency": "...",
          "contract": {},
          "allowCustomUsage": true,
          "keepBillDateOnUsageChange": true,
          "separatePrepaid": true,
          "isPrimaryPrice": true,
          "tld": "...",
          "cost": [
            {},
            {}
          ],
          "discount": {}
        },
        {
          "href": "...",
          "id": 12345,
          "uuid": "...",
          "frequency": "...",
          "contract": {},
          "allowCustomUsage": true,
          "keepBillDateOnUsageChange": true,
          "separatePrepaid": true,
          "isPrimaryPrice": true,
          "tld": "...",
          "cost": [
            {},
            {}
          ],
          "discount": {}
        }
      ],
      "bullet": [
        {
          "content": "...",
          "tooltip": "..."
        },
        {
          "content": "...",
          "tooltip": "..."
        }
      ]
    }
  ],
  "featuredCustomer": [
    {
      "id": 12345,
      "name": "...",
      "logoUrl": "..."
    },
    {
      "id": 12345,
      "name": "...",
      "logoUrl": "..."
    }
  ],
  "featuredMedium": [
    {
      "link": "...",
      "linkDescription": "...",
      "source": {
        "id": 12345,
        "name": "...",
        "logoUrl": "..."
      }
    },
    {
      "link": "...",
      "linkDescription": "...",
      "source": {
        "id": 12345,
        "name": "...",
        "logoUrl": "..."
      }
    }
  ],
  "feature": [
    {
      "id": 12345,
      "header": "...",
      "description": "...",
      "imageUrl": "...",
      "slogan": "...",
      "hideOnOverview": true,
      "position": 12345,
      "bullet": [
        {
          "title": "...",
          "position": 12345,
          "abovePicture": true,
          "highlight": [
            {},
            {}
          ]
        },
        {
          "title": "...",
          "position": 12345,
          "abovePicture": true,
          "highlight": [
            {},
            {}
          ]
        }
      ]
    },
    {
      "id": 12345,
      "header": "...",
      "description": "...",
      "imageUrl": "...",
      "slogan": "...",
      "hideOnOverview": true,
      "position": 12345,
      "bullet": [
        {
          "title": "...",
          "position": 12345,
          "abovePicture": true,
          "highlight": [
            {},
            {}
          ]
        },
        {
          "title": "...",
          "position": 12345,
          "abovePicture": true,
          "highlight": [
            {},
            {}
          ]
        }
      ]
    }
  ],
  "tag": [
    {
      "type": "...",
      "id": 12345,
      "name": "...",
      "badge": "...",
      "showBadge": true,
      "showOnNavigation": true,
      "tag": [
        {},
        {}
      ],
      "description": "..."
    },
    {
      "type": "...",
      "id": 12345,
      "name": "...",
      "badge": "...",
      "showBadge": true,
      "showOnNavigation": true,
      "tag": [
        {},
        {}
      ],
      "description": "..."
    }
  ],
  "language": [
    "...",
    "..."
  ],
  "mosiConnectorType": "MOSI",
  "platform": [
    {
      "uuid": "...",
      "attribute": [
        {
          "platformAttributeDefinitionUuid": "...",
          "uuid": "...",
          "lastModified": 12345,
          "createdOn": 12345,
          "platformAttributeOptionUuid": "...",
          "applicationPlatformUuid": "...",
          "value": "..."
        },
        {
          "platformAttributeDefinitionUuid": "...",
          "uuid": "...",
          "lastModified": 12345,
          "createdOn": 12345,
          "platformAttributeOptionUuid": "...",
          "applicationPlatformUuid": "...",
          "value": "..."
        }
      ],
      "platformDefinition": {
        "lastModified": 12345,
        "numTaggedProducts": 12345,
        "uuid": "...",
        "createdOn": 12345,
        "iconUrl": "...",
        "name": "...",
        "attributeDefinition": [
          {},
          {}
        ],
        "description": "...",
        "isVersionSupported": true
      }
    },
    {
      "uuid": "...",
      "attribute": [
        {
          "platformAttributeDefinitionUuid": "...",
          "uuid": "...",
          "lastModified": 12345,
          "createdOn": 12345,
          "platformAttributeOptionUuid": "...",
          "applicationPlatformUuid": "...",
          "value": "..."
        },
        {
          "platformAttributeDefinitionUuid": "...",
          "uuid": "...",
          "lastModified": 12345,
          "createdOn": 12345,
          "platformAttributeOptionUuid": "...",
          "applicationPlatformUuid": "...",
          "value": "..."
        }
      ],
      "platformDefinition": {
        "lastModified": 12345,
        "numTaggedProducts": 12345,
        "uuid": "...",
        "createdOn": 12345,
        "iconUrl": "...",
        "name": "...",
        "attributeDefinition": [
          {},
          {}
        ],
        "description": "...",
        "isVersionSupported": true
      }
    }
  ],
  "customAttributes": [
    {
      "value": "...",
      "label": "...",
      "attributeKey": "..."
    },
    {
      "value": "...",
      "label": "...",
      "attributeKey": "..."
    }
  ],
  "productRibbon": {},
  "_embedded": {
    "property1": {},
    "property2": {}
  },
  "links": [
    {
      "rel": "...",
      "href": "..."
    },
    {
      "rel": "...",
      "href": "..."
    }
  ]
}
````
````xml
<?xml version="1.0" encoding="UTF-8" ?>
<href>...</href>
<id>12345</id>
<uuid>...</uuid>
<publishedApp>
  <href>...</href>
  <id>...</id>
</publishedApp>
<workingApp>
  <href>...</href>
  <id>...</id>
</workingApp>
<name>...</name>
<type>...</type>
<provider>
  <uuid>...</uuid>
  <name>...</name>
  <url>...</url>
</provider>
<listing>
  <myAppLogoIconUrl>...</myAppLogoIconUrl>
  <imageUrl>...</imageUrl>
  <profileImageUrl>...</profileImageUrl>
  <myAppLogoIconSrcset>
    <property1>...</property1>
    <property2>...</property2>
  </myAppLogoIconSrcset>
  <imageSrcset>
    <property1>...</property1>
    <property2>...</property2>
  </imageSrcset>
  <profileImageSrcset>
    <property1>...</property1>
    <property2>...</property2>
  </profileImageSrcset>
  <blurb>...</blurb>
  <overview>...</overview>
  <rating>12345</rating>
  <reviewCount>12345</reviewCount>
  <mobileBundleId>...</mobileBundleId>
  <mobileAppStoreId>...</mobileAppStoreId>
</listing>
<overview>
  <splashTitle>...</splashTitle>
  <splashDescription>...</splashDescription>
  <imageUrl>...</imageUrl>
  <imageSrcset>
    <property1>...</property1>
    <property2>...</property2>
  </imageSrcset>
  <demoUrl>...</demoUrl>
  <documentationUrl>...</documentationUrl>
  <downloadDocumentationUrl>...</downloadDocumentationUrl>
  <systemRequirements>...</systemRequirements>
  <downloadFileSize>12345</downloadFileSize>
  <benefit>
    <title>...</title>
    <description>...</description>
  </benefit>
  <benefit>
    <title>...</title>
    <description>...</description>
  </benefit>
  <versions>
    <entry/>
    <entry/>
  </versions>
</overview>
<support>
  <email>...</email>
  <phone>...</phone>
  <knowledgebaseUrl>...</knowledgebaseUrl>
  <description>...</description>
</support>
<privacyUrl>...</privacyUrl>
<termsUrl>...</termsUrl>
<referUrl>...</referUrl>
<hostedLocation>...</hostedLocation>
<lastModified>12345</lastModified>
<pricing>
  <edition>
    <uuid>...</uuid>
    <rank>12345</rank>
    <name>...</name>
    <primary>true</primary>
    <trial/>
    <expiredTrialGracePeriod>12345</expiredTrialGracePeriod>
    <bundleOnly>true</bundleOnly>
    <targetAudience>...</targetAudience>
    <code>...</code>
    <defaultFreeTrial>true</defaultFreeTrial>
    <invisible>true</invisible>
    <leadGen>true</leadGen>
    <lastModified>12345</lastModified>
    <revenueType>...</revenueType>
    <restricted>true</restricted>
    <freeTrialDuration>12345</freeTrialDuration>
    <freeTrialType>...</freeTrialType>
    <customerContractRestricted>true</customerContractRestricted>
    <plan/>
    <plan/>
    <bullet/>
    <bullet/>
    <item/>
    <item/>
    <customization/>
    <customization/>
  </edition>
  <edition>
    <uuid>...</uuid>
    <rank>12345</rank>
    <name>...</name>
    <primary>true</primary>
    <trial/>
    <expiredTrialGracePeriod>12345</expiredTrialGracePeriod>
    <bundleOnly>true</bundleOnly>
    <targetAudience>...</targetAudience>
    <code>...</code>
    <defaultFreeTrial>true</defaultFreeTrial>
    <invisible>true</invisible>
    <leadGen>true</leadGen>
    <lastModified>12345</lastModified>
    <revenueType>...</revenueType>
    <restricted>true</restricted>
    <freeTrialDuration>12345</freeTrialDuration>
    <freeTrialType>...</freeTrialType>
    <customerContractRestricted>true</customerContractRestricted>
    <plan/>
    <plan/>
    <bullet/>
    <bullet/>
    <item/>
    <item/>
    <customization/>
    <customization/>
  </edition>
  <pricingSummary>...</pricingSummary>
  <footnote>...</footnote>
  <footnote>...</footnote>
  <bullet>
    <content>...</content>
    <tooltip>...</tooltip>
  </bullet>
  <bullet>
    <content>...</content>
    <tooltip>...</tooltip>
  </bullet>
</pricing>
<publishedOn>12345</publishedOn>
<rating>12345</rating>
<numRatings>12345</numRatings>
<buyable>true</buyable>
<free>true</free>
<freeTrialOrEditionPresent>true</freeTrialOrEditionPresent>
<referable>true</referable>
<hidePricings>true</hidePricings>
<collectLeads>true</collectLeads>
<collectLeadsWithPurchaseEnabled>true</collectLeadsWithPurchaseEnabled>
<newSubscriptionEnabled>true</newSubscriptionEnabled>
<changeSubscriptionAllowed>true</changeSubscriptionAllowed>
<displayQuestions>true</displayQuestions>
<displayReviews>true</displayReviews>
<oneClickPurchasable>true</oneClickPurchasable>
<autoUpgradeToPaid>true</autoUpgradeToPaid>
<downloadFileSize>12345</downloadFileSize>
<startingPrice>
  <unit>...</unit>
  <billingFrequency>...</billingFrequency>
  <amount>
    <AUD>12345</AUD>
    <CAD>12345</CAD>
    <CHF>12345</CHF>
    <EUR>12345</EUR>
    <GBP>12345</GBP>
    <JPY>12345</JPY>
    <KRW>12345</KRW>
    <MXN>12345</MXN>
    <MYR>12345</MYR>
    <SEK>12345</SEK>
    <SGD>12345</SGD>
    <USD>12345</USD>
    <INR>12345</INR>
    <BRL>12345</BRL>
    <DKK>12345</DKK>
    <NZD>12345</NZD>
    <NOK>12345</NOK>
    <ZAR>12345</ZAR>
    <PHP>12345</PHP>
    <CNY>12345</CNY>
    <SAR>12345</SAR>
    <GTQ>12345</GTQ>
  </amount>
  <discount>
    <description>...</description>
    <percentage>12345</percentage>
    <startDate>12345</startDate>
    <expirationDate>12345</expirationDate>
    <numOfBillingCycles>12345</numOfBillingCycles>
    <availableRedemptions>12345</availableRedemptions>
    <amount/>
    <pricingUnit>JBOSS_FUSE</pricingUnit>
  </discount>
</startingPrice>
<highestPercentageDiscount>12345</highestPercentageDiscount>
<highestFixedDiscount>
  <AUD>12345</AUD>
  <CAD>12345</CAD>
  <CHF>12345</CHF>
  <EUR>12345</EUR>
  <GBP>12345</GBP>
  <JPY>12345</JPY>
  <KRW>12345</KRW>
  <MXN>12345</MXN>
  <MYR>12345</MYR>
  <SEK>12345</SEK>
  <SGD>12345</SGD>
  <USD>12345</USD>
  <INR>12345</INR>
  <BRL>12345</BRL>
  <DKK>12345</DKK>
  <NZD>12345</NZD>
  <NOK>12345</NOK>
  <ZAR>12345</ZAR>
  <PHP>12345</PHP>
  <CNY>12345</CNY>
  <SAR>12345</SAR>
  <GTQ>12345</GTQ>
</highestFixedDiscount>
<bundledPlanIds>12345</bundledPlanIds>
<bundledPlanIds>12345</bundledPlanIds>
<customIntegration>...</customIntegration>
<usageType>...</usageType>
<linkedImportableApplicationUuid>...</linkedImportableApplicationUuid>
<liveChatEnabled>true</liveChatEnabled>
<liveChatAvailable>true</liveChatAvailable>
<showThirdPartyLegalDisclosure>true</showThirdPartyLegalDisclosure>
<showSelfServiceRestriction>true</showSelfServiceRestriction>
<integrationConfiguration>
  <productSettings>
    <validationUrl>...</validationUrl>
    <preSubmitValidationRequired>true</preSubmitValidationRequired>
    <enabledForSubscriptionChange>true</enabledForSubscriptionChange>
    <form/>
    <form/>
  </productSettings>
</integrationConfiguration>
<addon>true</addon>
<resource>
  <id>12345</id>
  <resourceType>...</resourceType>
  <name>...</name>
  <link>...</link>
  <scribdKey>...</scribdKey>
  <scribdId>...</scribdId>
  <description>...</description>
  <resellerAccess>true</resellerAccess>
</resource>
<resource>
  <id>12345</id>
  <resourceType>...</resourceType>
  <name>...</name>
  <link>...</link>
  <scribdKey>...</scribdKey>
  <scribdId>...</scribdId>
  <description>...</description>
  <resellerAccess>true</resellerAccess>
</resource>
<screenshot>
  <name>...</name>
  <imageUrl>...</imageUrl>
  <imageUrlSrcset>
    <property1>...</property1>
    <property2>...</property2>
  </imageUrlSrcset>
</screenshot>
<screenshot>
  <name>...</name>
  <imageUrl>...</imageUrl>
  <imageUrlSrcset>
    <property1>...</property1>
    <property2>...</property2>
  </imageUrlSrcset>
</screenshot>
<addonOffering>
  <id>12345</id>
  <uuid>...</uuid>
  <name>...</name>
  <code>...</code>
  <description>...</description>
  <descriptionHtml>...</descriptionHtml>
  <status>...</status>
  <stacked>true</stacked>
  <exclusive>true</exclusive>
  <paymentPlan>
    <href>...</href>
    <id>12345</id>
    <uuid>...</uuid>
    <frequency>...</frequency>
    <contract/>
    <allowCustomUsage>true</allowCustomUsage>
    <keepBillDateOnUsageChange>true</keepBillDateOnUsageChange>
    <separatePrepaid>true</separatePrepaid>
    <isPrimaryPrice>true</isPrimaryPrice>
    <tld>...</tld>
    <cost/>
    <cost/>
    <discount/>
  </paymentPlan>
  <paymentPlan>
    <href>...</href>
    <id>12345</id>
    <uuid>...</uuid>
    <frequency>...</frequency>
    <contract/>
    <allowCustomUsage>true</allowCustomUsage>
    <keepBillDateOnUsageChange>true</keepBillDateOnUsageChange>
    <separatePrepaid>true</separatePrepaid>
    <isPrimaryPrice>true</isPrimaryPrice>
    <tld>...</tld>
    <cost/>
    <cost/>
    <discount/>
  </paymentPlan>
  <bullet>
    <content>...</content>
    <tooltip>...</tooltip>
  </bullet>
  <bullet>
    <content>...</content>
    <tooltip>...</tooltip>
  </bullet>
</addonOffering>
<addonOffering>
  <id>12345</id>
  <uuid>...</uuid>
  <name>...</name>
  <code>...</code>
  <description>...</description>
  <descriptionHtml>...</descriptionHtml>
  <status>...</status>
  <stacked>true</stacked>
  <exclusive>true</exclusive>
  <paymentPlan>
    <href>...</href>
    <id>12345</id>
    <uuid>...</uuid>
    <frequency>...</frequency>
    <contract/>
    <allowCustomUsage>true</allowCustomUsage>
    <keepBillDateOnUsageChange>true</keepBillDateOnUsageChange>
    <separatePrepaid>true</separatePrepaid>
    <isPrimaryPrice>true</isPrimaryPrice>
    <tld>...</tld>
    <cost/>
    <cost/>
    <discount/>
  </paymentPlan>
  <paymentPlan>
    <href>...</href>
    <id>12345</id>
    <uuid>...</uuid>
    <frequency>...</frequency>
    <contract/>
    <allowCustomUsage>true</allowCustomUsage>
    <keepBillDateOnUsageChange>true</keepBillDateOnUsageChange>
    <separatePrepaid>true</separatePrepaid>
    <isPrimaryPrice>true</isPrimaryPrice>
    <tld>...</tld>
    <cost/>
    <cost/>
    <discount/>
  </paymentPlan>
  <bullet>
    <content>...</content>
    <tooltip>...</tooltip>
  </bullet>
  <bullet>
    <content>...</content>
    <tooltip>...</tooltip>
  </bullet>
</addonOffering>
<featuredCustomer>
  <id>12345</id>
  <name>...</name>
  <logoUrl>...</logoUrl>
</featuredCustomer>
<featuredCustomer>
  <id>12345</id>
  <name>...</name>
  <logoUrl>...</logoUrl>
</featuredCustomer>
<featuredMedium>
  <link>...</link>
  <linkDescription>...</linkDescription>
  <source>
    <id>12345</id>
    <name>...</name>
    <logoUrl>...</logoUrl>
  </source>
</featuredMedium>
<featuredMedium>
  <link>...</link>
  <linkDescription>...</linkDescription>
  <source>
    <id>12345</id>
    <name>...</name>
    <logoUrl>...</logoUrl>
  </source>
</featuredMedium>
<feature>
  <id>12345</id>
  <header>...</header>
  <description>...</description>
  <imageUrl>...</imageUrl>
  <slogan>...</slogan>
  <hideOnOverview>true</hideOnOverview>
  <position>12345</position>
  <bullet>
    <title>...</title>
    <position>12345</position>
    <abovePicture>true</abovePicture>
    <highlight/>
    <highlight/>
  </bullet>
  <bullet>
    <title>...</title>
    <position>12345</position>
    <abovePicture>true</abovePicture>
    <highlight/>
    <highlight/>
  </bullet>
</feature>
<feature>
  <id>12345</id>
  <header>...</header>
  <description>...</description>
  <imageUrl>...</imageUrl>
  <slogan>...</slogan>
  <hideOnOverview>true</hideOnOverview>
  <position>12345</position>
  <bullet>
    <title>...</title>
    <position>12345</position>
    <abovePicture>true</abovePicture>
    <highlight/>
    <highlight/>
  </bullet>
  <bullet>
    <title>...</title>
    <position>12345</position>
    <abovePicture>true</abovePicture>
    <highlight/>
    <highlight/>
  </bullet>
</feature>
<tag>
  <type>...</type>
  <id>12345</id>
  <name>...</name>
  <badge>...</badge>
  <showBadge>true</showBadge>
  <showOnNavigation>true</showOnNavigation>
  <tag/>
  <tag/>
  <description>...</description>
</tag>
<tag>
  <type>...</type>
  <id>12345</id>
  <name>...</name>
  <badge>...</badge>
  <showBadge>true</showBadge>
  <showOnNavigation>true</showOnNavigation>
  <tag/>
  <tag/>
  <description>...</description>
</tag>
<language>...</language>
<language>...</language>
<mosiConnectorType>MOSI</mosiConnectorType>
<platform>
  <uuid>...</uuid>
  <attribute>
    <platformAttributeDefinitionUuid>...</platformAttributeDefinitionUuid>
    <uuid>...</uuid>
    <lastModified>12345</lastModified>
    <createdOn>12345</createdOn>
    <platformAttributeOptionUuid>...</platformAttributeOptionUuid>
    <applicationPlatformUuid>...</applicationPlatformUuid>
    <value>...</value>
  </attribute>
  <attribute>
    <platformAttributeDefinitionUuid>...</platformAttributeDefinitionUuid>
    <uuid>...</uuid>
    <lastModified>12345</lastModified>
    <createdOn>12345</createdOn>
    <platformAttributeOptionUuid>...</platformAttributeOptionUuid>
    <applicationPlatformUuid>...</applicationPlatformUuid>
    <value>...</value>
  </attribute>
  <platformDefinition>
    <lastModified>12345</lastModified>
    <numTaggedProducts>12345</numTaggedProducts>
    <uuid>...</uuid>
    <createdOn>12345</createdOn>
    <iconUrl>...</iconUrl>
    <name>...</name>
    <attributeDefinition/>
    <attributeDefinition/>
    <description>...</description>
    <isVersionSupported>true</isVersionSupported>
  </platformDefinition>
</platform>
<platform>
  <uuid>...</uuid>
  <attribute>
    <platformAttributeDefinitionUuid>...</platformAttributeDefinitionUuid>
    <uuid>...</uuid>
    <lastModified>12345</lastModified>
    <createdOn>12345</createdOn>
    <platformAttributeOptionUuid>...</platformAttributeOptionUuid>
    <applicationPlatformUuid>...</applicationPlatformUuid>
    <value>...</value>
  </attribute>
  <attribute>
    <platformAttributeDefinitionUuid>...</platformAttributeDefinitionUuid>
    <uuid>...</uuid>
    <lastModified>12345</lastModified>
    <createdOn>12345</createdOn>
    <platformAttributeOptionUuid>...</platformAttributeOptionUuid>
    <applicationPlatformUuid>...</applicationPlatformUuid>
    <value>...</value>
  </attribute>
  <platformDefinition>
    <lastModified>12345</lastModified>
    <numTaggedProducts>12345</numTaggedProducts>
    <uuid>...</uuid>
    <createdOn>12345</createdOn>
    <iconUrl>...</iconUrl>
    <name>...</name>
    <attributeDefinition/>
    <attributeDefinition/>
    <description>...</description>
    <isVersionSupported>true</isVersionSupported>
  </platformDefinition>
</platform>
<customAttributes>
  <value>...</value>
  <label>...</label>
  <attributeKey>...</attributeKey>
</customAttributes>
<customAttributes>
  <value>...</value>
  <label>...</label>
  <attributeKey>...</attributeKey>
</customAttributes>
<productRibbon/>
<_embedded>
  <property1/>
  <property2/>
</_embedded>
<links>
  <rel>...</rel>
  <href>...</href>
</links>
<links>
  <rel>...</rel>
  <href>...</href>
</links>
````
<aside class="success">
This operation does not require authentication
</aside>

## List all product recommendations

> Code samples

````shell
# You can also use wget
curl -X get http://appdirect.com/api/marketplace/v1/products/{applicationId}/recommendations \
  -H 'Accept: application/xml' \
  -H 'Content-Type: application/xml'

````

````http
GET http://appdirect.com/api/marketplace/v1/products/{applicationId}/recommendations HTTP/1.1
Host: appdirect.com
Content-Type: application/xml
Accept: application/xml

````

````javascript
var headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

$.ajax({
  url: 'http://appdirect.com/api/marketplace/v1/products/{applicationId}/recommendations',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
````

````javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

fetch('http://appdirect.com/api/marketplace/v1/products/{applicationId}/recommendations',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
````

````ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml',
  'Content-Type' => 'application/xml'
}

result = RestClient.get 'http://appdirect.com/api/marketplace/v1/products/{applicationId}/recommendations', params: {
  }, headers: headers

p JSON.parse(result)
````

````python
import requests
headers = {
  'Accept': 'application/xml',
  'Content-Type': 'application/xml'
}

r = requests.get('http://appdirect.com/api/marketplace/v1/products/{applicationId}/recommendations', params={

}, headers = headers)

print r.json()
````

````java
URL obj = new URL("http://appdirect.com/api/marketplace/v1/products/{applicationId}/recommendations");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
````

`GET /marketplace/v1/products/{applicationId}/recommendations`

*List all product recommendations*

This call lists all  products that other customers have bought in addition to the one specified.
Returns recommendations for additional purchases (currently simply returning what others who have bought the product have also bought).
This may be augmented later to include additional recommendation strategies but always in the context of a single product.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
applicationId|path|number|true|Application id


### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of recommended applications

> Example responses

````json
[
  {
    "href": "...",
    "id": 12345,
    "uuid": "...",
    "url": "...",
    "name": "...",
    "productType": "...",
    "iconUrl": "...",
    "profileLogoUrl": "...",
    "iconSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "profileLogoSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "description": "...",
    "overview": "...",
    "startingPrice": "...",
    "channelStartingPrice": {
      "freeTrial": true,
      "free": true,
      "prices": {
        "property1": {
          "duration": "THREE_YEARS",
          "price": 12345
        },
        "property2": {
          "duration": "MONTHLY",
          "price": 12345
        }
      }
    },
    "billingFrequency": "...",
    "publishedOn": 12345,
    "developerName": "...",
    "vendorName": "...",
    "rating": 12345,
    "numRatings": 12345,
    "showRating": true,
    "overviewImageUrl": "...",
    "overviewImageSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "blurb": "...",
    "buyable": true,
    "free": true,
    "freeTrialOrEditionPresent": true,
    "referable": true,
    "hasLyncToPhone": true,
    "downloadFileSize": 12345,
    "hidePricings": true,
    "collectLeads": true,
    "addon": true,
    "featured": true,
    "featuredSliderPosition": 12345,
    "popular": true,
    "popularity": 12345,
    "staffPick": true,
    "staffPickSliderPosition": 12345,
    "discountDetails": {
      "discountedStartingPrice": "...",
      "startingPricePercentageDiscount": 12345,
      "highestPercentageDiscount": 12345,
      "highestFixedDiscount": {
        "AUD": 12345,
        "CAD": 12345,
        "CHF": 12345,
        "EUR": 12345,
        "GBP": 12345,
        "JPY": 12345,
        "KRW": 12345,
        "MXN": 12345,
        "MYR": 12345,
        "SEK": 12345,
        "SGD": 12345,
        "USD": 12345,
        "INR": 12345,
        "BRL": 12345,
        "DKK": 12345,
        "NZD": 12345,
        "NOK": 12345,
        "ZAR": 12345,
        "PHP": 12345,
        "CNY": 12345,
        "SAR": 12345,
        "GTQ": 12345
      }
    },
    "lastModified": 12345,
    "sortRank": 12345,
    "tag": [
      {
        "type": "...",
        "id": 12345,
        "name": "...",
        "badge": "...",
        "showBadge": true,
        "showOnNavigation": true,
        "tag": [
          {},
          {}
        ],
        "description": "..."
      },
      {
        "type": "...",
        "id": 12345,
        "name": "...",
        "badge": "...",
        "showBadge": true,
        "showOnNavigation": true,
        "tag": [
          {},
          {}
        ],
        "description": "..."
      }
    ],
    "bundleUrl": [
      "...",
      "..."
    ],
    "language": [
      "...",
      "..."
    ],
    "productRibbon": {}
  }
]
````
````xml
<?xml version="1.0" encoding="UTF-8" ?>
<href>...</href>
<id>12345</id>
<uuid>...</uuid>
<url>...</url>
<name>...</name>
<productType>...</productType>
<iconUrl>...</iconUrl>
<profileLogoUrl>...</profileLogoUrl>
<iconSrcset>
  <property1>...</property1>
  <property2>...</property2>
</iconSrcset>
<profileLogoSrcset>
  <property1>...</property1>
  <property2>...</property2>
</profileLogoSrcset>
<description>...</description>
<overview>...</overview>
<startingPrice>...</startingPrice>
<channelStartingPrice>
  <freeTrial>true</freeTrial>
  <free>true</free>
  <prices>
    <property1>
      <duration>THREE_YEARS</duration>
      <price>12345</price>
    </property1>
    <property2>
      <duration>MONTHLY</duration>
      <price>12345</price>
    </property2>
  </prices>
</channelStartingPrice>
<billingFrequency>...</billingFrequency>
<publishedOn>12345</publishedOn>
<developerName>...</developerName>
<vendorName>...</vendorName>
<rating>12345</rating>
<numRatings>12345</numRatings>
<showRating>true</showRating>
<overviewImageUrl>...</overviewImageUrl>
<overviewImageSrcset>
  <property1>...</property1>
  <property2>...</property2>
</overviewImageSrcset>
<blurb>...</blurb>
<buyable>true</buyable>
<free>true</free>
<freeTrialOrEditionPresent>true</freeTrialOrEditionPresent>
<referable>true</referable>
<hasLyncToPhone>true</hasLyncToPhone>
<downloadFileSize>12345</downloadFileSize>
<hidePricings>true</hidePricings>
<collectLeads>true</collectLeads>
<addon>true</addon>
<featured>true</featured>
<featuredSliderPosition>12345</featuredSliderPosition>
<popular>true</popular>
<popularity>12345</popularity>
<staffPick>true</staffPick>
<staffPickSliderPosition>12345</staffPickSliderPosition>
<discountDetails>
  <discountedStartingPrice>...</discountedStartingPrice>
  <startingPricePercentageDiscount>12345</startingPricePercentageDiscount>
  <highestPercentageDiscount>12345</highestPercentageDiscount>
  <highestFixedDiscount>
    <AUD>12345</AUD>
    <CAD>12345</CAD>
    <CHF>12345</CHF>
    <EUR>12345</EUR>
    <GBP>12345</GBP>
    <JPY>12345</JPY>
    <KRW>12345</KRW>
    <MXN>12345</MXN>
    <MYR>12345</MYR>
    <SEK>12345</SEK>
    <SGD>12345</SGD>
    <USD>12345</USD>
    <INR>12345</INR>
    <BRL>12345</BRL>
    <DKK>12345</DKK>
    <NZD>12345</NZD>
    <NOK>12345</NOK>
    <ZAR>12345</ZAR>
    <PHP>12345</PHP>
    <CNY>12345</CNY>
    <SAR>12345</SAR>
    <GTQ>12345</GTQ>
  </highestFixedDiscount>
</discountDetails>
<lastModified>12345</lastModified>
<sortRank>12345</sortRank>
<tag>
  <type>...</type>
  <id>12345</id>
  <name>...</name>
  <badge>...</badge>
  <showBadge>true</showBadge>
  <showOnNavigation>true</showOnNavigation>
  <tag/>
  <tag/>
  <description>...</description>
</tag>
<tag>
  <type>...</type>
  <id>12345</id>
  <name>...</name>
  <badge>...</badge>
  <showBadge>true</showBadge>
  <showOnNavigation>true</showOnNavigation>
  <tag/>
  <tag/>
  <description>...</description>
</tag>
<bundleUrl>...</bundleUrl>
<bundleUrl>...</bundleUrl>
<language>...</language>
<language>...</language>
<productRibbon/>
````
<aside class="success">
This operation does not require authentication
</aside>

## Retrieve a product status

> Code samples

````shell
# You can also use wget
curl -X get http://appdirect.com/api/marketplace/v1/products/{applicationId}/status \
  -H 'Accept: application/xml' \
  -H 'Content-Type: application/xml'

````

````http
GET http://appdirect.com/api/marketplace/v1/products/{applicationId}/status HTTP/1.1
Host: appdirect.com
Content-Type: application/xml
Accept: application/xml

````

````javascript
var headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

$.ajax({
  url: 'http://appdirect.com/api/marketplace/v1/products/{applicationId}/status',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
````

````javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

fetch('http://appdirect.com/api/marketplace/v1/products/{applicationId}/status',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
````

````ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml',
  'Content-Type' => 'application/xml'
}

result = RestClient.get 'http://appdirect.com/api/marketplace/v1/products/{applicationId}/status', params: {
  }, headers: headers

p JSON.parse(result)
````

````python
import requests
headers = {
  'Accept': 'application/xml',
  'Content-Type': 'application/xml'
}

r = requests.get('http://appdirect.com/api/marketplace/v1/products/{applicationId}/status', params={

}, headers = headers)

print r.json()
````

````java
URL obj = new URL("http://appdirect.com/api/marketplace/v1/products/{applicationId}/status");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
````

`GET /marketplace/v1/products/{applicationId}/status`

*Retrieve a product status*

This call returns the status of a product on your marketplace.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
applicationId|path|number|true|Application id


### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|products status

> Example responses

````json
{
  "assigned": true,
  "pending": true,
  "requested": true,
  "pendingAppType": "REQUESTED",
  "companyEntitlementId": 12345,
  "editionId": 12345,
  "editionName": "...",
  "ownerUuid": "...",
  "ownerFullName": "...",
  "ownerAdmin": true,
  "partOfExistingBundle": true,
  "companyEntitlementPending": true,
  "freeTrialAllowed": true,
  "companyWide": true,
  "purchaseRestriction": [
    {
      "appId": 12345,
      "appName": "...",
      "ownedEditionId": 12345,
      "ownedEditionName": "...",
      "browsedEditionId": 12345,
      "requiredAppEdition": [
        {
          "appId": 12345,
          "appName": "...",
          "editionId": 12345,
          "editionName": "..."
        },
        {
          "appId": 12345,
          "appName": "...",
          "editionId": 12345,
          "editionName": "..."
        }
      ],
      "upcomingSubscription": true,
      "restrictionType": "..."
    },
    {
      "appId": 12345,
      "appName": "...",
      "ownedEditionId": 12345,
      "ownedEditionName": "...",
      "browsedEditionId": 12345,
      "requiredAppEdition": [
        {
          "appId": 12345,
          "appName": "...",
          "editionId": 12345,
          "editionName": "..."
        },
        {
          "appId": 12345,
          "appName": "...",
          "editionId": 12345,
          "editionName": "..."
        }
      ],
      "upcomingSubscription": true,
      "restrictionType": "..."
    }
  ]
}
````
````xml
<?xml version="1.0" encoding="UTF-8" ?>
<assigned>true</assigned>
<pending>true</pending>
<requested>true</requested>
<pendingAppType>REQUESTED</pendingAppType>
<companyEntitlementId>12345</companyEntitlementId>
<editionId>12345</editionId>
<editionName>...</editionName>
<ownerUuid>...</ownerUuid>
<ownerFullName>...</ownerFullName>
<ownerAdmin>true</ownerAdmin>
<partOfExistingBundle>true</partOfExistingBundle>
<companyEntitlementPending>true</companyEntitlementPending>
<freeTrialAllowed>true</freeTrialAllowed>
<companyWide>true</companyWide>
<purchaseRestriction>
  <appId>12345</appId>
  <appName>...</appName>
  <ownedEditionId>12345</ownedEditionId>
  <ownedEditionName>...</ownedEditionName>
  <browsedEditionId>12345</browsedEditionId>
  <requiredAppEdition>
    <appId>12345</appId>
    <appName>...</appName>
    <editionId>12345</editionId>
    <editionName>...</editionName>
  </requiredAppEdition>
  <requiredAppEdition>
    <appId>12345</appId>
    <appName>...</appName>
    <editionId>12345</editionId>
    <editionName>...</editionName>
  </requiredAppEdition>
  <upcomingSubscription>true</upcomingSubscription>
  <restrictionType>...</restrictionType>
</purchaseRestriction>
<purchaseRestriction>
  <appId>12345</appId>
  <appName>...</appName>
  <ownedEditionId>12345</ownedEditionId>
  <ownedEditionName>...</ownedEditionName>
  <browsedEditionId>12345</browsedEditionId>
  <requiredAppEdition>
    <appId>12345</appId>
    <appName>...</appName>
    <editionId>12345</editionId>
    <editionName>...</editionName>
  </requiredAppEdition>
  <requiredAppEdition>
    <appId>12345</appId>
    <appName>...</appName>
    <editionId>12345</editionId>
    <editionName>...</editionName>
  </requiredAppEdition>
  <upcomingSubscription>true</upcomingSubscription>
  <restrictionType>...</restrictionType>
</purchaseRestriction>
````
<aside class="success">
This operation does not require authentication
</aside>

## List all products by developer

> Code samples

````shell
# You can also use wget
curl -X get http://appdirect.com/api/marketplace/v1/vendors/{vendorUuid}/products \
  -H 'Accept: application/xml' \
  -H 'Content-Type: application/xml'

````

````http
GET http://appdirect.com/api/marketplace/v1/vendors/{vendorUuid}/products HTTP/1.1
Host: appdirect.com
Content-Type: application/xml
Accept: application/xml

````

````javascript
var headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

$.ajax({
  url: 'http://appdirect.com/api/marketplace/v1/vendors/{vendorUuid}/products',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
````

````javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/xml',
  'Content-Type':'application/xml'

};

fetch('http://appdirect.com/api/marketplace/v1/vendors/{vendorUuid}/products',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
````

````ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/xml',
  'Content-Type' => 'application/xml'
}

result = RestClient.get 'http://appdirect.com/api/marketplace/v1/vendors/{vendorUuid}/products', params: {
  }, headers: headers

p JSON.parse(result)
````

````python
import requests
headers = {
  'Accept': 'application/xml',
  'Content-Type': 'application/xml'
}

r = requests.get('http://appdirect.com/api/marketplace/v1/vendors/{vendorUuid}/products', params={

}, headers = headers)

print r.json()
````

````java
URL obj = new URL("http://appdirect.com/api/marketplace/v1/vendors/{vendorUuid}/products");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
````

`GET /marketplace/v1/vendors/{vendorUuid}/products`

*List all products by developer*

This call lists all products offered by a specific developer.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
vendorUuid|path|string|true|Vendor UUID


### Responses

Status|Meaning|Description
---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Products read.
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Vendor not found.

> Example responses

````json
[
  {
    "href": "...",
    "id": 12345,
    "uuid": "...",
    "url": "...",
    "name": "...",
    "productType": "...",
    "iconUrl": "...",
    "profileLogoUrl": "...",
    "iconSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "profileLogoSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "description": "...",
    "overview": "...",
    "startingPrice": "...",
    "channelStartingPrice": {
      "freeTrial": true,
      "free": true,
      "prices": {
        "property1": {
          "duration": "THREE_YEARS",
          "price": 12345
        },
        "property2": {
          "duration": "MONTHLY",
          "price": 12345
        }
      }
    },
    "billingFrequency": "...",
    "publishedOn": 12345,
    "developerName": "...",
    "vendorName": "...",
    "rating": 12345,
    "numRatings": 12345,
    "showRating": true,
    "overviewImageUrl": "...",
    "overviewImageSrcset": {
      "property1": "...",
      "property2": "..."
    },
    "blurb": "...",
    "buyable": true,
    "free": true,
    "freeTrialOrEditionPresent": true,
    "referable": true,
    "hasLyncToPhone": true,
    "downloadFileSize": 12345,
    "hidePricings": true,
    "collectLeads": true,
    "addon": true,
    "featured": true,
    "featuredSliderPosition": 12345,
    "popular": true,
    "popularity": 12345,
    "staffPick": true,
    "staffPickSliderPosition": 12345,
    "discountDetails": {
      "discountedStartingPrice": "...",
      "startingPricePercentageDiscount": 12345,
      "highestPercentageDiscount": 12345,
      "highestFixedDiscount": {
        "AUD": 12345,
        "CAD": 12345,
        "CHF": 12345,
        "EUR": 12345,
        "GBP": 12345,
        "JPY": 12345,
        "KRW": 12345,
        "MXN": 12345,
        "MYR": 12345,
        "SEK": 12345,
        "SGD": 12345,
        "USD": 12345,
        "INR": 12345,
        "BRL": 12345,
        "DKK": 12345,
        "NZD": 12345,
        "NOK": 12345,
        "ZAR": 12345,
        "PHP": 12345,
        "CNY": 12345,
        "SAR": 12345,
        "GTQ": 12345
      }
    },
    "lastModified": 12345,
    "sortRank": 12345,
    "tag": [
      {
        "type": "...",
        "id": 12345,
        "name": "...",
        "badge": "...",
        "showBadge": true,
        "showOnNavigation": true,
        "tag": [
          {},
          {}
        ],
        "description": "..."
      },
      {
        "type": "...",
        "id": 12345,
        "name": "...",
        "badge": "...",
        "showBadge": true,
        "showOnNavigation": true,
        "tag": [
          {},
          {}
        ],
        "description": "..."
      }
    ],
    "bundleUrl": [
      "...",
      "..."
    ],
    "language": [
      "...",
      "..."
    ],
    "productRibbon": {}
  }
]
````
````xml
<?xml version="1.0" encoding="UTF-8" ?>
<href>...</href>
<id>12345</id>
<uuid>...</uuid>
<url>...</url>
<name>...</name>
<productType>...</productType>
<iconUrl>...</iconUrl>
<profileLogoUrl>...</profileLogoUrl>
<iconSrcset>
  <property1>...</property1>
  <property2>...</property2>
</iconSrcset>
<profileLogoSrcset>
  <property1>...</property1>
  <property2>...</property2>
</profileLogoSrcset>
<description>...</description>
<overview>...</overview>
<startingPrice>...</startingPrice>
<channelStartingPrice>
  <freeTrial>true</freeTrial>
  <free>true</free>
  <prices>
    <property1>
      <duration>THREE_YEARS</duration>
      <price>12345</price>
    </property1>
    <property2>
      <duration>MONTHLY</duration>
      <price>12345</price>
    </property2>
  </prices>
</channelStartingPrice>
<billingFrequency>...</billingFrequency>
<publishedOn>12345</publishedOn>
<developerName>...</developerName>
<vendorName>...</vendorName>
<rating>12345</rating>
<numRatings>12345</numRatings>
<showRating>true</showRating>
<overviewImageUrl>...</overviewImageUrl>
<overviewImageSrcset>
  <property1>...</property1>
  <property2>...</property2>
</overviewImageSrcset>
<blurb>...</blurb>
<buyable>true</buyable>
<free>true</free>
<freeTrialOrEditionPresent>true</freeTrialOrEditionPresent>
<referable>true</referable>
<hasLyncToPhone>true</hasLyncToPhone>
<downloadFileSize>12345</downloadFileSize>
<hidePricings>true</hidePricings>
<collectLeads>true</collectLeads>
<addon>true</addon>
<featured>true</featured>
<featuredSliderPosition>12345</featuredSliderPosition>
<popular>true</popular>
<popularity>12345</popularity>
<staffPick>true</staffPick>
<staffPickSliderPosition>12345</staffPickSliderPosition>
<discountDetails>
  <discountedStartingPrice>...</discountedStartingPrice>
  <startingPricePercentageDiscount>12345</startingPricePercentageDiscount>
  <highestPercentageDiscount>12345</highestPercentageDiscount>
  <highestFixedDiscount>
    <AUD>12345</AUD>
    <CAD>12345</CAD>
    <CHF>12345</CHF>
    <EUR>12345</EUR>
    <GBP>12345</GBP>
    <JPY>12345</JPY>
    <KRW>12345</KRW>
    <MXN>12345</MXN>
    <MYR>12345</MYR>
    <SEK>12345</SEK>
    <SGD>12345</SGD>
    <USD>12345</USD>
    <INR>12345</INR>
    <BRL>12345</BRL>
    <DKK>12345</DKK>
    <NZD>12345</NZD>
    <NOK>12345</NOK>
    <ZAR>12345</ZAR>
    <PHP>12345</PHP>
    <CNY>12345</CNY>
    <SAR>12345</SAR>
    <GTQ>12345</GTQ>
  </highestFixedDiscount>
</discountDetails>
<lastModified>12345</lastModified>
<sortRank>12345</sortRank>
<tag>
  <type>...</type>
  <id>12345</id>
  <name>...</name>
  <badge>...</badge>
  <showBadge>true</showBadge>
  <showOnNavigation>true</showOnNavigation>
  <tag/>
  <tag/>
  <description>...</description>
</tag>
<tag>
  <type>...</type>
  <id>12345</id>
  <name>...</name>
  <badge>...</badge>
  <showBadge>true</showBadge>
  <showOnNavigation>true</showOnNavigation>
  <tag/>
  <tag/>
  <description>...</description>
</tag>
<bundleUrl>...</bundleUrl>
<bundleUrl>...</bundleUrl>
<language>...</language>
<language>...</language>
<productRibbon/>
````
<aside class="success">
This operation does not require authentication
</aside>



