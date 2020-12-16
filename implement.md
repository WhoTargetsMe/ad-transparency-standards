# An ad transparency schema

By implementing a schema, or standard, for how ad transparency data is presented, ad platforms can increase comprehension, trust, interoperability, quality of analysis and more. 

## Caveat

There is likely other work going on in this area that we don't know about. If you're working on it, or know of another relevant initiative, please get in touch.

## Ways to use the schema

- In ad libraries, to create a standard format for access to ad data
- On web pages, so people can use a variety of new, context-adding tools that read and interpret this data.

## The schema

## Fields

### `entity/details`

- `ENTITY_ID`: An internal ID for the advertiser (e.g. a pageID)
- `ENTITY_REAL_NAME`: The name of the entity running the ad (e.g. "The Democratic Party")
- `ENTITY_INTERNAL_NAME`: An internal name of the entity (e.g. a short url "democrats")
- `ENTITY_WEBSITE`: The website of the entity (e.g. "https://democrats.org" - useful to de-duplicate 
- `ENTITY_ELECTORAL_ID`: An (external) ID held by an electoral regulator (e.g. FEC ID)
- `ENTITY_LEGAL_STATUS`: The legal status of the entity (e.g. individual, company, charity, political party)
- `ENTITY_VERIFICATION_DATE`: The date the entity was verified (blank if not, or no verification programme)

### `atps/id_type and advertising_platform/id_type`

- `GOOGLE_ATP_ID`: Google internal ID for ad technology providers.
- `IAB_GVL_ID`:  IAB ID for ad technology providers. For more details read the [IAB's website "TCF – Transparency & Consent Framework"](https://iabeurope.eu/transparency-consent-framework/).

### `targeting_category/geo_location`

- `GEO_LOCATION_NOT_DISCLOSED`: Default value. Unclear whether geolocation data was used.
- `GEO_LOCATION_NOT_USED`: Geolocation data wasn’t used.
- `GEO_LOCATION_APPROXIMATE`: Geolocation data is based on either fuzzified lat-long or IP-derived location.
- `GEO_LOCATION_PRECISE`: Precise geolocation data, as defined by the IAB TCF v2.0.
- `GEO_LOCATION_UNKNOWN_TYPE`: Other geolocation types, including cases where both APPROXIMATE and PRECISE are used or where APPROXIMATE or PRECISE cannot be determined.

### `targeting_category/remarketing`

- `REMARKETING_NOT_DISCLOSED`: Default value. Unclear whether remarketing is used.
- `REMARKETING_NOT_USED`: Remarketing not used.
- `REMARKETING_THIRD PARTY`: The ad targeting is based on online or offline data about you from someone who may not be the advertiser.
- `REMARKETING_WEBSITE_VISIT`: The ad targeting is based on a previous visit to an advertiser’s website.
- `REMARKETING_UNKNOWN_TYPE- `: Other remarketing types not listed or undetermined. For example, `UPLOADED` or `WEBSITE_VISIT` cannot be determined.

### `targeting_category/user_characteristics`

- `<empty repeated field = NOT_DISCLOSED>`
- `USER_CHARACTERISTICS_NOT_USED`: User characteristics weren’t used.
- `USER_CHARACTERISTICS_GENDER`: The ad targeting criteria is (partially) based on either declared or inferred gender.
- `USER_CHARACTERISTICS_AGE_GROUP`: The ad targeting criteria is (partially) based on either declared or inferred age group.
- `USER_CHARACTERISTICS_UNKNOWN_TYPE`: Other user characteristics not listed.

### `targeting_category/user_interests`

- `USER_INTERESTS_NOT_DISCLOSED`: Default value. Unclear whether user interests are used.
- `USER_INTERESTS_NOT_USED`: User interests weren’t used.
- `USER_INTERESTS_USED`: The ad targeting criteria is (partially) based on either declared or inferred user interests.

### `targeting_category/context`

- `CONTEXT_NOT_DISCLOSED`: Default value. Unclear whether context is used.
- `CONTEXT_NOT_USED`: Context wasn’t used.
- `CONTEXT_USED`: The ad targeting criteria is (partially) based on either declared or inferred context.

### `targeting_category/other`

- `OTHER_NOT_DISCLOSED`: Default value. Unclear whether other information is used.
- `OTHER_NOT_USED`: Other information wasn’t used.
- `OTHER_USED`: The ad targeting criteria is (partially) based on other information, either declared or inferred.

## Formatting the JSON messages and metadata tag

JSON messages should be minified and escaped. The following example applies to AdsMetadata JSON:

```json
{
  "atps": [ {
    "id_type": "GOOGLE_ATP_ID",
    "id": 2,
    "name": "ATP with Google ID"
  }, {
    "id_type": "IAB_GVL_ID",
    "id": 3,
    "name": "ATP with IAB Global Vendor ID"
  } ],
  "advertising_platform": {
    "id_type": "GOOGLE_ATP_ID",
    "id": 4,
    "name": "Some Advertising Platform"
  },
  "targeting_category": {
    "geo_location_type": "APPROXIMATE",
    "remarketing_type": "WEBSITE_VISIT",
    "user_interests": true,
    "user_characteristic_types": [ "GENDER", "AGE_GROUP" ],
    "contextual": true,
    "other": true
  }
}
```


