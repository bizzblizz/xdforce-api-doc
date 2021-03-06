# Monitors

## Create Monitors (Basic Settings)

Users can create new monitors through this endpoint.

### HTTP Request

`POST /api/v1/monitors/new`

> The above command returns JSON structured like this on SUCCESS:

```json
{
    "ok": true,
    "id": "MONITOR_ID",
    "rev": "DOCUMENT_REVISION_HASH"
}
```

> The above command returns JSON structured like this in case of any ERROR:

```json
{
  "ok": false,
  "message": "ERROR_MESSAGE"
}
```

### Query Parameters

Parameter | Type | Description | Required
--------- | ------- | ----------- | --------
name | String | Name or Address of the website to be monitored | Yes
category | String | Category of the Monitor | Yes
wantsDesktop | Boolean | Accept desktop traffic as good traffic | No
wantsPhone | Boolean | Accept mobile traffic as good traffic | No
wantsTablet | Boolean | Accept tablet/device traffic as good traffic | No
mismatchRedirectUrl | String | Redirect URL for unwanted impressions | No
dangerRedirectUrl | String | Redirect URL for dangerous impressions | No

<aside class="notice">
mismatchRedirectUrl and dangerRedirectUrl will only be available to the users with premium/upgraded plans.
</aside>

## Edit Monitors Settings

Users can edit monitor settings through this endpoint.

### HTTP Request

`PUT /api/v1/monitors/<MONITOR_ID>`

> The above command returns JSON structured like this on SUCCESS:

```json
{
    "ok": true,
    "id": "MONITOR_ID",
    "rev": "DOCUMENT_REVISION_HASH"
}
```

> The above command returns JSON structured like this in case of any ERROR:

```json
{
  "ok": false,
  "message": "ERROR_MESSAGE"
}
```

### Query Parameters

Parameter | Type | Description | Required
--------- | ------- | ----------- | --------
name | String | Name or Address of the website to be monitored | Yes
category | String | Category of the Monitor | Yes
wantsDesktop | Boolean | Accept desktop traffic as good traffic | No
wantsPhone | Boolean | Accept mobile traffic as good traffic | No
wantsTablet | Boolean | Accept tablet/device traffic as good traffic | No
mismatchRedirectUrl | String | Redirect URL for unwanted impressions | No
dangerRedirectUrl | String | Redirect URL for dangerous impressions | No

<aside class="notice">
mismatchRedirectUrl and dangerRedirectUrl will only be available to the users with premium/upgraded plans.
</aside>

## Set Monitor Geo Locations

Users Geo Locations to the respective Monitor

`PUT /api/v1/monitors/<MONITOR_ID>/setgeographicarea`

> The above command returns JSON structured like this on SUCCESS:

```json
{
    "ok": true,
    "id": "MONITOR_ID",
    "rev": "DOCUMENT_REVISION_HASH"
}
```

> The above command returns JSON structured like this in case of any ERROR:

```json
{
  "ok": false,
  "message": "ERROR_MESSAGE"
}
```

### Query Parameters

Parameter | Type | Options | Default | Description | Required
--------- | ---- | ------- | ------- | ----------- | --------
geoStrategy | String | coordinates, regions | coordinates | Set geographic strategy | Yes
addresses | Array of String | | | List of addresses (if selected `coordinates`) | Yes
regions | Array of String | | | List of countries as regions (if selected `regions`) | No

* `addresses` must be given, if geoStrategy is set as ***coordinates***.
* `regions` is effective(optionally), if geoStrategy is set as ***regions***. If no region is given, geo location will be set for all regions.

<aside class="notice">
When selecting coordinates, try to provide an address as specific as possible for a better result. Location of the address consisting latitude and longitude will be updated automatically when updating the monitors geographic location.
</aside>

## List All Monitors

This endpoint will list all the active monitors of a user.

`GET /api/v1/monitors`

> The above command returns JSON structured like this:

```json
{
  "ok": true,
  "message": {
    "monitors": [
    {
      "_id": "13OG0C57B101",
      "_rev": "60-c96ab2a1547ce4c26c1c11407af8324c",
      "type": "Monitor",
      "accountId": "16VM0C2cuD02",
      "name": "Sample Monitor 1",
      "domain": "",
      "category": "",
      "wantsDesktop": false,
      "wantsPhone": false,
      "wantsTablet": false,
      "geoStrategy": "coordinates",
      "dangerRedirectUrl": "",
      "mismatchRedirectUrl": "",
      "archived": false,
      "blacklist": [],
      "coordinates":
        [
          {
            "address": "Kolkata",
            "latitude": 22.572646,
            "longitude": 88.36389500000001,
            "radius": 25
          },
          {
            "address": "Delhi",
            "latitude": 28.6139391,
            "longitude": 77.2090212,
            "radius": 25
          }
        ]
      },
      {
        "_id": "12zu0CELWG01",
        "_rev": "1-6466ba5e64216c44db51553ff05e8fb7",
        "type": "Monitor",
        "accountId": "16VM0C2cuD02",
        "name": "Sample Monitor 2",
        "domain": "",
        "category": "Blog - Cultural",
        "wantsDesktop": true,
        "wantsPhone": true,
        "wantsTablet": true,
        "geoStrategy": "regions",
        "regions":
          [
            {
              "country": "*",
              "region": "*"
            }
          ],
        "dangerRedirectUrl": "",
        "mismatchRedirectUrl": "",
        "archived": false,
        "coordinates": [],
        "blacklist": []
      }
    ]
  }
}
```

> The above command returns JSON structured like this in case of any ERROR:

```json
{
  "ok": false,
  "message": "ERROR_MESSAGE"
}
```

## List All Archived Monitors

This endpoint will list all the archived monitors of a user.

`GET /api/v1/monitors?archived=true`

> The above command returns JSON structured like this:

```json
{
  "ok": true,
  "message": {
    "monitors": [
    {
      "_id": "13OG0C57B101",
      "_rev": "60-c96ab2a1547ce4c26c1c11407af8324c",
      "type": "Monitor",
      "accountId": "16VM0C2cuD02",
      "name": "Sample Monitor 1",
      "domain": "",
      "category": "",
      "wantsDesktop": false,
      "wantsPhone": false,
      "wantsTablet": false,
      "geoStrategy": "coordinates",
      "dangerRedirectUrl": "",
      "mismatchRedirectUrl": "",
      "archived": true,
      "blacklist": [],
      "coordinates":
        [
          {
            "address": "Kolkata",
            "latitude": 22.572646,
            "longitude": 88.36389500000001,
            "radius": 25
          },
          {
            "address": "Delhi",
            "latitude": 28.6139391,
            "longitude": 77.2090212,
            "radius": 25
          }
        ]
      },
      {
        "_id": "12zu0CELWG01",
        "_rev": "1-6466ba5e64216c44db51553ff05e8fb7",
        "type": "Monitor",
        "accountId": "16VM0C2cuD02",
        "name": "Sample Monitor 2",
        "domain": "",
        "category": "Blog - Cultural",
        "wantsDesktop": true,
        "wantsPhone": true,
        "wantsTablet": true,
        "geoStrategy": "regions",
        "regions":
          [
            {
              "country": "*",
              "region": "*"
            }
          ],
        "dangerRedirectUrl": "",
        "mismatchRedirectUrl": "",
        "archived": true,
        "coordinates": [],
        "blacklist": []
      }
    ]
  }
}
```

> The above command returns JSON structured like this in case of any ERROR:

```json
{
  "ok": false,
  "message": "ERROR_MESSAGE"
}
```

## Fetch a Monitor

This endpoint will provide the details of a monitor.

`GET /api/v1/monitors/<MONITOR_ID>`

> The above command returns JSON structured like this:

```json
{
    "ok": true,
    "message": {
        "monitor": {
            "_id": "13OG0C57B101",
            "_rev": "60-c96ab2a1547ce4c26c1c11407af8324c",
            "type": "Monitor",
            "accountId": "16VM0C2cuD02",
            "name": "Sample Monitor",
            "domain": "",
            "category": "Personal Blog",
            "wantsDesktop": false,
            "wantsPhone": false,
            "wantsTablet": false,
            "geoStrategy": "coordinates",
            "dangerRedirectUrl": "",
            "mismatchRedirectUrl": "",
            "archived": false,
            "blacklist": [],
            "coordinates": [
                {
                    "address": "Kolkata",
                    "latitude": 22.572646,
                    "longitude": 88.36389500000001,
                    "radius": 25
                },
                {
                    "address": "Delhi",
                    "latitude": 28.6139391,
                    "longitude": 77.2090212,
                    "radius": 25
                }
            ]
        }
    }
}
```

## Get a Monitor's Embed Code

This endpoint will provide the embed code of a monitor.

`GET /api/v1/monitors/<MONITOR_ID>/embedcode`

> The above command returns JSON structured like this:

```json
{
    "ok": true,
    "message": "<script type=\"text/javascript\" src=\"http//localhost:3003/tracker\"></script><script type=\"text/javascript\">xDForce.track(\"12zu0CELWG01\");</script>;"
}
```

## Delete / Archive a Monitor

Users can archive a monitor through this endpoint.

`DELETE /api/v1/monitors/<MONITOR_ID>`

> The above command returns JSON structured like this:

```json
{
    "ok": true,
    "message": "Monitor archived successfully"
}
```