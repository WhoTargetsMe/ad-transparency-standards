# An ad transparency schema

By implementing a schema, or standard, for how ad transparency data is presented, ad platforms can increase comprehension, trust, interoperability, quality of analysis and more. 

## Caveat

There is likely other work going on in this area that we don't know about. If you're working on it, or know of another relevant initiative, please get in touch.

## Ways to use the schema

- In ad libraries, to create a standard format for access to ad data
- On web pages, so people can use a variety of new, context-adding tools that read and interpret this data.

## The schema and fields

### `entity/details`

- `ENTITY_ID`: An internal ID for the advertiser (e.g. a pageID)
- `ENTITY_REAL_NAME`: The name of the entity running the ad (e.g. "The Democratic Party")
- `ENTITY_INTERNAL_NAME`: An internal name of the entity (e.g. a short url "democrats")
- `ENTITY_WEBSITE`: The website of the entity (e.g. "https://democrats.org" - useful to de-duplicate 
- `ENTITY_ELECTORAL_ID`: An (external) ID held by an electoral regulator (e.g. FEC ID)
- `ENTITY_LEGAL_STATUS`: The legal status of the entity (e.g. individual, company, charity, political party)
- `ENTITY_TYPE`: The type of entity (e.g. candidate, elected official, political party, non-profit, public figure etc).
- `ENTITY_VERIFICATION_DATE`: The date the entity was verified (blank if not, or no verification programme)

### `ad/details`

- `AD_ID`: An internal ID for the ad.
- `AD_LIBRARY_URL`: A deeplink to the ad in the platform ad library.
- `AD_COPY`: All text used in the ad.
- `AD_IMAGE_URLS`: Link(s) to the image(s) used in the ad.
- `AD_MEDIA_URLS`: Link(s) to the media files used in the ad.
- `AD_URLS`: The URLs used in the ad.

### `ad/group`

- `GROUP_NOT_DISCLOSED`: Default value. Unclear if part of a group of ads.
- `GROUP_ID`: An internal ID for all ads in the same ad group.

### `ad/testing`

- `TESTING_NOT_DISCLOSED`: Default value. 
- `TESTING_NOT_USED`: The ad doesn't make use of the platform's testing capabilities.
- `TESTING_TYPE`: Values - 'AB' or 'Multivariate'

### `ad/dates`

- `DATETIME_LIVE`: When the ad started running
- `DATETIME_ENDED`: When the ad stopped running (blank if still delivering impressions and budget not exhausted)
- `DATETIME_APPROVED`: The date and time the ad was approved to run.
- `DATETIME_CREATED`: When the ad started running

### `advertising_platform/id_type`

- `PLATFORM_NAME`: The name of the ad platform
- `PLATFORM_URL`: The URL of the ad platform
- `PLATFORM_AD_POLICY`: The public URL of the platform's ad policies and rules
- `IAB_ID`:  IAB ID for ad technology providers. For more details read the [IAB's website "TCF – Transparency & Consent Framework"](https://iabeurope.eu/transparency-consent-framework/).

### `targeting_category/geo_location`

- `GEO_LOCATION_NOT_DISCLOSED`: Default value. Unclear whether geolocation data was used.
- `GEO_LOCATION_NOT_USED`: Geolocation data wasn’t used.
- `GEO_LOCATION_APPROXIMATE`: Geolocation data is based on either fuzzified lat-long or IP-derived location.
- `GEO_LOCATION_PRECISE`: Precise geolocation data, as defined by the IAB TCF v2.0.
- `GEO_LOCATION_EXCLUDED`: Any geographic exclusions.
- `GEO_LOCATION_UNKNOWN_TYPE`: Other geolocation types, including cases where both APPROXIMATE and PRECISE are used or where APPROXIMATE or PRECISE cannot be determined.

### `targeting_category/remarketing`

- `REMARKETING_NOT_DISCLOSED`: Default value. Unclear whether remarketing is used.
- `REMARKETING_NOT_USED`: Remarketing not used.
- `REMARKETING_THIRD PARTY`: The ad targeting is based on online or offline data about you from someone who may not be the advertiser. Value is the name of the third party.
- `REMARKETING_WEBSITE_VISIT`: The ad targeting is based on a previous visit to an advertiser’s website.
- `REMARKETING_EXCLUSIONS`: Any remarketing exclusions.
- `REMARKETING_UNKNOWN_TYPE- `: Other remarketing types not listed or undetermined. For example, `UPLOADED` or `WEBSITE_VISIT` cannot be determined.

### `targeting_category/user_characteristics`

- `USER_CHARACTERISTICS_NOT_USED`: User characteristics weren’t used.
- `USER_CHARACTERISTICS_GENDER`: The ad targeting criteria is (partially) based on either declared or inferred gender.
- `USER_CHARACTERISTICS_AGE_GROUP`: The ad targeting criteria is (partially) based on either declared or inferred age group.
- `USER_CHARACTERISTICS_LANGUAGES`: The ad targeting criteria is (partially) based on either declared or inferred user language(s).
- `USER_CHARACTERISTICS_EXCLUSIONS`: Any exclusions based on user characteristics.
- `USER_CHARACTERISTICS_UNKNOWN_TYPE`: Other user characteristics not listed.

### `targeting_category/user_interests`

- `USER_INTERESTS_NOT_DISCLOSED`: Default value. Unclear whether user interests are used.
- `USER_INTERESTS_NOT_USED`: User interests weren’t used.
- `USER_INTERESTS_EXCLUDED`: User interests that were excluded from targeting.
- `USER_INTERESTS_USED`: The ad targeting criteria is (partially) based on either declared or inferred user interests.

### `targeting_category/context`

- `CONTEXT_NOT_DISCLOSED`: Default value. Unclear whether context is used.
- `CONTEXT_NOT_USED`: Context wasn’t used.
- `CONTEXT_USED`: The ad targeting criteria is (partially) based on either declared or inferred context. Value is the context(s), such as the website(s) or networks being targeted.

### `targeting_category/other`

- `OTHER_NOT_DISCLOSED`: Default value. Unclear whether other information is used.
- `OTHER_NOT_USED`: Other information wasn’t used.
- `OTHER_USED`: The ad targeting criteria is (partially) based on other information, either declared or inferred.

### `targeting_category/audience_size`

- `AUDIENCE_SIZE_NOT_DISCLOSED`: Default value. 
- `AUDIENCE_SIZE_LOWER_BOUND`: Lower bound of the estimated target audience size.
- `AUDIENCE_SIZE_UPPER_BOUND`: Upper bound of the estimated target audience size.

### `spending/details`

- `SPENDING_NOT_DISCLOSED`: Default value. 
- `SPENDING_TOTAL`: The exact amount spent on the ad. 
- `SPENDING_LOWER_BOUND`: The lower bound of spending on the ad (e.g. $500).
- `SPENDING_UPPER_BOUND`: The higher bound of spending on the ad (e.g. $600).

### `delivery/details`

- `DELIVERY_NOT_DISCLOSED`: Default value. 
- `DELIVERY_OPTIMIZATION`: The delivery optimization method selected by the advertiser.

### `reach/impressions`

- `IMPRESSIONS_NOT_DISCLOSED`: Default value. 
- `IMPRESSIONS_LOWER_BOUND`: Lower bound of the number of ad impressions delivered.
- `IMPRESSIONS_UPPER_BOUND`: Upper bound of the number of ad impressions delivered.

### `reach/unique_users`

- `UNIQUE_USERS_NOT_DISCLOSED`: Default value. 
- `UNIQUE_USERS_LOWER_BOUND`: Lower bound of the number of unique users who saw > 1 impression of the ad.
- `UNIQUE_USERS_UPPER_BOUND`: Upper bound of the number of unique users who saw > 1 impression of the ad.

### `reach/engagement`

- `ENGAGEMENT_NOT_DISCLOSED`: Default value. 
- `ENGAGEMENT_CLICKS`: The number of clicks on the ad.
- `ENGAGEMENT_SOCIAL`: The social engagement with the ad.

### `reach/demographics`

- `DEMOGRAPHICS_NOT_DISCLOSED`: Default value. 
- `DEMOGRAPHICS_GENDER`: The reach of the ad, broken down by gender.
- `DEMOGRAPHICS_AGE`: The reach of the ad, broken down by age ranges (25-34, 35-44 etc).

## Formatting the JSON

JSON messages should be minified and escaped. 

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


