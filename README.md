[Bayut Scraper](https://apify.com/fatihtahta/Bayut-scraper?fpr=data)

# Enterprise Grade Bayut Scraper

**Slug:** `fatihtahta/Bayut-scraper`

## Overview

Enterprise Grade Bayut Scraper collects structured property and agency data from Bayut, including listing titles, prices, locations, bedroom and bathroom counts, area, contact details, agency information, and related availability metadata. It is built for teams that need dependable real estate records for analysis, enrichment, reporting, and operational workflows. [Bayut](https://www.bayut.com) is one of the leading real estate marketplaces in the UAE, which makes it a valuable source for tracking supply, pricing, rental activity, and broker presence across key markets. Instead of manually reviewing listings and broker pages, you can run consistent data collection jobs and receive JSON output that is ready for downstream use. The result is less manual work, faster refresh cycles, and a cleaner path from discovery to analysis.

## Why Use This Actor

- **Market research and analytics:** Track inventory, pricing bands, bedroom mix, and listing activity across areas such as Dubai Marina, Business Bay, or Yas Island.
- **Product and content teams:** Build market pages, neighborhood comparisons, and listing intelligence views with structured property and agency data.
- **Developers and data engineering pipelines:** Feed dashboards, ETL jobs, catalogs, and data warehouses with standardized JSON records.
- **Lead generation and enrichment:** Identify agencies, brokers, and active listings for prospecting, segmentation, and CRM enrichment workflows.
- **Monitoring and competitive tracking:** Watch selected locations, developers, agencies, or property categories over time to spot changes in supply and positioning.

## Input Parameters

Provide any combination of URLs, queries, and filters to focus the run. For this actor, the supported public inputs are location and optional listing filters.

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `deal_type` | `string` | Listing side of the market to collect. Allowed values: `for_sale`, `for_rent`. | `for_sale` |
| `location` | `string` | Bayut location name, such as `Dubai Marina`, `Business Bay`, `Jumeirah Village Circle`, or `Yas Island`. | – |
| `min_price` | `number` | Lowest price to include in the results. | – |
| `max_price` | `number` | Highest price to include in the results. | – |
| `residential_property_type` | `string[]` | Residential property categories to include. Allowed values: `apartment`, `townhouse`, `villa_compound`, `land`, `building`, `villa`, `penthouse`, `hotel_apartment`, `floor`. | – |
| `commercial_property_type` | `string[]` | Commercial property categories to include. Allowed values: `office`, `warehouse`, `villa`, `land`, `building`, `industrial_land`, `showroom`, `shop`, `labour_camp`, `bulk_unit`, `floor`, `factory`, `mixed_use_land`, `other_commercial`. | – |
| `rent_frequency` | `string` | Rental billing period to include for rental runs. Allowed values: `yearly`, `monthly`, `weekly`, `daily`, `any`. Ignored for sale listings. | `any` |
| `bedroom_count` | `string[]` | Bedroom counts to include. Allowed values: `studio`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8_plus`. | – |
| `bathroom_count` | `string[]` | Bathroom counts to include. Allowed values: `1`, `2`, `3`, `4`, `5`, `6_plus`. | – |
| `min_area` | `number` | Minimum property size in square feet. | – |
| `max_area` | `number` | Maximum property size in square feet. | – |
| `developer` | `string` | Developer name to match, such as `Emaar`, `DAMAC`, or `Binghatti`. | – |
| `agent` | `string[]` | One or more agent or agency names to include. | – |
| `keywords` | `string[]` | Free-text terms to narrow the results, such as `furnished`, `waterfront`, `off-plan`, or `payment plan`. | – |
| `with_floor_plans` | `boolean` | When `true`, keep only listings that include floor plan information. | – |
| `limit` | `integer` | Maximum number of listings to save. | – |

## Example Inputs

This actor's public input model is location and filter based, so the examples below use supported parameters only.

### Scenario: location-based sales snapshot

```
{
  "deal_type": "for_sale",
  "location": "Dubai Marina",
  "residential_property_type": ["apartment"],
  "bedroom_count": ["1", "2"],
  "min_price": 900000,
  "max_price": 2500000,
  "with_floor_plans": true,
  "limit": 250
}
```

### Scenario: keyword-guided rental tracking

```
{
  "deal_type": "for_rent",
  "location": "Business Bay",
  "rent_frequency": "yearly",
  "keywords": ["furnished", "canal view"],
  "bathroom_count": ["1", "2"],
  "min_area": 600,
  "max_price": 180000,
  "limit": 300
}
```

### Scenario: targeted commercial inventory run

```
{
  "deal_type": "for_rent",
  "location": "Jebel Ali",
  "commercial_property_type": ["warehouse", "office"],
  "min_area": 5000,
  "max_area": 25000,
  "keywords": ["fitted"],
  "agent": ["White & Co"],
  "limit": 100
}
```

## Output

### 6.1 Output destination

The actor writes results to an Apify dataset as JSON records. And the dataset is designed for direct consumption by analytics tools, ETL pipelines, and downstream APIs without post-processing.

### 6.2 Record envelope (all items)

Every record includes the same stable envelope:

- **type** *(string, required)*: Record category. Current values are `property` and `agency`.
- **id** *(number, required)*: Stable Bayut entity identifier. In JSON output, this may sometimes be serialized as a numeric string, so normalize it in downstream systems if needed.
- **url** *(string, required)*: Public URL for the entity page.

Recommended idempotency key: `type + ":" + id`

Use this key for deduplication and upserts when the same entity appears across multiple runs or overlapping inputs.

### 6.3 Examples

Example: property (`type = "property"`)

```
{
  "type": "property",
  "id": "14476801",
  "url": "https://www.bayut.com/property/details-14476801.html",
  "canonicalUrl": "https://www.bayut.com/property/details-14476801.html",
  "sourceUrl": "https://www.bayut.com/for-sale/property/",
  "seedId": "c903e349664c",
  "seedType": "query",
  "seedValue": "https://www.bayut.com/for-sale/property/",
  "pageIndex": 1,
  "title": "10% Down Payment | Near Al Maktoum Airport | 8.2% ROI | Oasis Residences Dubai South",
  "price": "1080000.0",
  "priceNumeric": 1080000,
  "currency": "AED",
  "location": "UAE, Dubai, Dubai South, Residential District, Oasis Residences",
  "referenceNumber": "105798-jLLICu-ao",
  "agencyName": "Jusur Properties",
  "purpose": "for-sale",
  "bedrooms": 2,
  "bathrooms": 3,
  "area": 97.98112016640002,
  "furnishingStatus": "furnished",
  "completionStatus": "under-construction",
  "publishedAt": "2026-04-03T15:31:51+00:00",
  "fingerprint": "b8520158ad691f562306",
  "ownerId": 2679756,
  "userExternalId": "2679756",
  "sourceId": 1,
  "state": "active",
  "geography": {
    "lat": 24.951278,
    "lng": 55.224639
  },
  "product": "superhot",
  "productLabel": "default",
  "productVariant": "Signature 30 days",
  "title_l1": "شقة مفروشة بغرفتي نوم",
  "title_l2": "2 卧室公寓 1080000 AED",
  "title_l3": "Квартира, 2 спальни, 1080000 AED",
  "externalId": "14476801",
  "slug": "10-down-payment-near-airport-14476801",
  "project": {
    "id": 9426255,
    "externalId": "3073",
    "completionStatus": "under-construction",
    "agency": {
      "externalId": "655",
      "name": "Al Helal Al Zahaby Real Estate Development L. L. C",
      "name_l1": "Al Helal Al Zahaby Real Estate Development L. L. C",
      "name_l2": "Al Helal Al Zahaby Real Estate Development L. L. C",
      "name_l3": "Al Helal Al Zahaby Real Estate Development L. L. C",
      "slug": "al-helal-al-zahaby-real-estate-development-l-l-c",
      "slug_l1": "al-helal-al-zahaby-real-estate-development-l-l-c",
      "slug_l2": "al-helal-al-zahaby-real-estate-development-l-l-c",
      "slug_l3": "al-helal-al-zahaby-real-estate-development-l-l-c"
    }
  },
  "createdAt": 1772905993,
  "updatedAt": 1775230311,
  "reactivatedAt": 1772905993,
  "rooms": 2,
  "baths": 3,
  "coverPhoto": {
    "id": 825124817,
    "externalId": "264892660",
    "title": "Exterior Entrance.jpg",
    "orderIndex": 0,
    "nimaScore": 6.001063600103487,
    "main": true,
    "type": "listing"
  },
  "photoCount": 26,
  "videoCount": 0,
  "panoramaCount": 0,
  "phoneNumber": {
    "mobile": "+971501527294",
    "phone": "+97145772890",
    "whatsapp": "971545695868",
    "phoneNumbers": ["+97145772890"],
    "mobileNumbers": ["+971501527294"]
  },
  "contactMethodAvailability": {
    "whatsapp": true,
    "sms": true,
    "email": true,
    "call": true
  },
  "contactName": "Aldwin John",
  "agency": {
    "id": 29850413,
    "objectId": 29850413,
    "name": "Jusur Properties",
    "name_l1": "جسور للعقارات",
    "name_l2": "Jusur Properties",
    "name_l3": "Jusur Properties",
    "externalId": "105798",
    "product": "premium",
    "productScore": 2,
    "location": "Dubai",
    "location_l1": "دبي",
    "location_l2": "迪拜",
    "location_l3": "Дубай",
    "licenses": [
      {
        "number": "31487",
        "authority": "RERA"
      }
    ],
    "logo": {
      "id": 747388075,
      "url": "https://bayut-production.s3.eu-central-1.amazonaws.com/image/747388075/example"
    },
    "slug": "jusur-properties-105798",
    "slug_l1": "jusur-properties-105798",
    "slug_l2": "jusur-properties-105798",
    "slug_l3": "jusur-properties-105798",
    "tr": 3,
    "roles": ["unified_agency", "bayut_exclusive", "bayut_propel"],
    "active": true,
    "createdAt": "2024-10-28T05:40:52+00:00",
    "commercialNumber": null,
    "shortNumber": null,
    "type": "agency"
  },
  "isVerified": true,
  "verification": {
    "updatedAt": 1775230312.658723,
    "eligible": true,
    "status": "verified",
    "verifiedAt": 1775230311,
    "trucheckedAt": 1775230311
  },
  "extraFields": {
    "dldBuildingNK": "tabu-780333678",
    "dldPropertySk": "14476801"
  },
  "ownerAgent": {
    "externalId": "2679756",
    "name": "Aldwin John",
    "name_l1": "Aldwin John",
    "name_l2": "Aldwin John",
    "name_l3": "Aldwin John",
    "user_image": "https://bayut-production.s3.eu-central-1.amazonaws.com/image/819363295/example",
    "user_image_id": 819363295,
    "isTruBroker": false,
    "slug": "aldwin-john-2679756",
    "state": "active",
    "isProfileCompleted": true,
    "isComplete": true
  },
  "offplanDetails": {
    "saleType": "new",
    "originalPrice": null,
    "paidPrice": null,
    "dldWaiver": null
  },
  "completionDetails": {
    "startDate": null,
    "completionDate": 1814385600,
    "completionPercentage": 22
  },
  "paymentPlanSummaries": [
    {
      "preHandoverPercentageSum": 50,
      "postHandoverPercentageSum": 50,
      "breakdown": {
        "downPaymentPercentage": 10,
        "preHandoverPercentage": 40,
        "handoverPercentage": 10,
        "postHandoverPercentage": 40
      }
    }
  ],
  "agentAdStoriesCount": 0,
  "hasUnitPlan": false,
  "hasMatchingFloorPlans": false,
  "photoIds": [825124817, 825124818, 825124831],
  "hidePrice": false,
  "locationPurposeTier": 2,
  "objectId": "11053180",
  "searchId": 11053180,
  "locationHierarchy": [
    {
      "id": 1,
      "level": 0,
      "externalId": "5001",
      "name": "UAE",
      "name_l1": "الإمارات",
      "name_l2": "阿联酋",
      "name_l3": "ОАЭ",
      "slug": "/uae"
    },
    {
      "id": 2,
      "level": 1,
      "externalId": "5002",
      "name": "Dubai",
      "name_l1": "دبي",
      "name_l2": "迪拜",
      "name_l3": "Дубай",
      "slug": "/dubai"
    },
    {
      "id": 3355,
      "level": 2,
      "externalId": "8881",
      "name": "Dubai South",
      "name_l1": "دبي الجنوب",
      "name_l2": "迪拜南部街区",
      "name_l3": "Дубай Саут",
      "slug": "/dubai/dubai-south",
      "type": "neighbourhood"
    }
  ],
  "categoryHierarchy": [
    {
      "id": 1,
      "level": 0,
      "externalId": "1",
      "name": "Residential",
      "name_l1": "سكني",
      "name_l2": "居住物业",
      "name_l3": "Жилые",
      "slug": "residential",
      "slug_l1": "residential",
      "slug_l2": "residential",
      "slug_l3": "residential",
      "nameSingular": "Residential",
      "nameSingular_l1": "سكني",
      "nameSingular_l2": "居住物业",
      "nameSingular_l3": "Жилые"
    },
    {
      "id": 2,
      "level": 1,
      "externalId": "4",
      "name": "Apartments",
      "name_l1": "شقق",
      "name_l2": "公寓",
      "name_l3": "Апартаменты",
      "slug": "apartments",
      "slug_l1": "apartments",
      "slug_l2": "apartments",
      "slug_l3": "apartments",
      "nameSingular": "Apartment",
      "nameSingular_l1": "شقة",
      "nameSingular_l2": "公寓",
      "nameSingular_l3": "Квартира"
    }
  ]
}
```

Example: agency (`type = "agency"`)

```
{
  "type": "agency",
  "id": "10212",
  "url": "https://www.bayut.com/brokers/white-co-10212/",
  "canonicalUrl": "https://www.bayut.com/brokers/white-co-10212/",
  "sourceUrl": "https://www.bayut.com/brokers/dubai/dubai-marina/?agents_type=agencies&location_external_id=5003&location_id=36",
  "seedId": "70b14b1f68e9",
  "seedType": "query",
  "seedValue": "dubai marina",
  "pageIndex": 1,
  "title": "White & Co",
  "location": "Dubai",
  "agencyName": "White & Co",
  "purpose": "for-sale for-rent",
  "fingerprint": "d9cbfa0952006c4765ae",
  "name_l1": "وايت وشركاه",
  "name_l2": "White & Co",
  "name_l3": "White & Co",
  "agentsCount": 425,
  "externalId": "10212",
  "product": "featured",
  "logo": {
    "id": 101127274,
    "url": "https://bayut-production.s3.eu-central-1.amazonaws.com/image/101127274/example"
  },
  "slug": "white-co-10212",
  "slug_l1": "white-co-10212",
  "slug_l2": "white-co-10212",
  "slug_l3": "white-co-10212",
  "locations": [
    {
      "id": 2,
      "objectId": 2,
      "name": "Dubai",
      "name_l1": "دبي",
      "name_l2": "迪拜",
      "name_l3": "Дубай",
      "externalId": "5002",
      "slug": "/dubai",
      "slug_l1": "/dubai",
      "slug_l2": "/dubai",
      "slug_l3": "/dubai",
      "_geoloc": {
        "lat": 25.024769324449,
        "lng": 55.359007938377
      },
      "geography": {
        "lat": 25.024769324449,
        "lng": 55.359007938377
      },
      "geo_point": [55.359007938377, 25.024769324449],
      "level": 1,
      "hierarchy": [
        {
          "id": 1,
          "level": 0,
          "externalId": "5001",
          "name": "UAE",
          "name_l1": "الإمارات",
          "name_l2": "阿联酋",
          "name_l3": "ОАЭ",
          "slug": "/uae",
          "slug_l1": "/uae",
          "slug_l2": "/uae",
          "slug_l3": "/uae"
        },
        {
          "id": 2,
          "level": 1,
          "externalId": "5002",
          "name": "Dubai",
          "name_l1": "دبي",
          "name_l2": "迪拜",
          "name_l3": "Дубай",
          "slug": "/dubai",
          "slug_l1": "/dubai",
          "slug_l2": "/dubai",
          "slug_l3": "/dubai"
        }
      ],
      "adCount": 252171,
      "aliases": [],
      "type": null,
      "trackID": "5002",
      "roles": null,
      "completionStatus": "both",
      "hasChildren": true
    }
  ],
  "stats": {
    "adsSaleCount": 3009,
    "adsRentCount": 2915,
    "adsCount": 5924,
    "purposes": ["for-sale", "for-rent"],
    "locationsWithAds": [4096, 1, 2, 4099, 4100],
    "trubrokerAgentCount": 289,
    "trubrokerAgentsProfileImageIDs": [172559356, 172559357, 172559371],
    "categoryTypes": ["Warehouses", "Hotel Apartments", "Townhouses", "Penthouses", "Villas", "Apartments", "Floors", "Plots", "Shops", "Offices"],
    "categoryTypes_l1": ["مستودعات", "شقق فندقية", "تاون هاوس"],
    "categoryTypes_l2": ["仓库", "酒店式公寓", "联排别墅"],
    "categoryTypes_l3": ["Складские помещения", "Апартаменты в отеле", "Таунхаусы"],
    "serviceAreas": ["Reem", "DAMAC Lagoons", "Downtown Dubai", "Palm Jumeirah", "Dubai Marina", "Business Bay"],
    "serviceAreas_l1": ["ريم", "داماك لاجونز", "وسط مدينة دبي"],
    "serviceAreas_l2": ["瑞姆小区", "大马士革湖住宅", "迪拜市中心"],
    "serviceAreas_l3": ["Реем", "Дамак Лагунс", "Дубай Даунтаун"]
  },
  "phoneNumber": {},
  "contactMethodAvailability": {
    "sms": false,
    "email": true,
    "call": false
  },
  "createdAt": "2021-01-05T03:11:33+00:00",
  "agencySg": 1,
  "exStatus": 0,
  "eliteStatus": true,
  "objectId": "29591365",
  "searchId": 29591365
}
```

## Field reference

### Shared envelope fields

- **type** *(string, required)*: Record type. Current values are `property` and `agency`.
- **id** *(number, required)*: Stable entity identifier.
- **url** *(string, required)*: Public entity URL.
- **canonicalUrl** *(string, optional)*: Canonical public URL for the entity.
- **sourceUrl** *(string, optional)*: Public source page where the record was discovered.
- **seedId** *(string, optional)*: Stable identifier for the originating input.
- **seedType** *(string, optional)*: Origin category for the input, such as `query`.
- **seedValue** *(string, optional)*: Original input value associated with the record.
- **pageIndex** *(number, optional)*: Result page number where the record was found.
- **fingerprint** *(string, optional)*: Stable fingerprint for change detection or deduplication support.

### Property fields (`type = "property"`)

- **title** *(string, required)*: Listing title.
- **price** *(string, optional)*: Raw price value as returned in the source record.
- **priceNumeric** *(number, optional)*: Normalized numeric price.
- **currency** *(string, optional)*: Listing currency, typically `AED`.
- **location** *(string, optional)*: Human-readable location path.
- **referenceNumber** *(string, optional)*: Public listing reference number.
- **agencyName** *(string, optional)*: Agency name shown on the listing.
- **purpose** *(string, optional)*: Listing purpose, such as `for-sale` or `for-rent`.
- **bedrooms** *(number, optional)*: Bedroom count.
- **bathrooms** *(number, optional)*: Bathroom count.
- **area** *(number, optional)*: Property area.
- **furnishingStatus** *(string, optional)*: Furnishing state when provided.
- **completionStatus** *(string, optional)*: Build or delivery status.
- **publishedAt** *(string, optional)*: Listing publication timestamp.
- **ownerId** *(number, optional)*: Internal owner identifier.
- **userExternalId** *(string, optional)*: External user identifier.
- **sourceId** *(number, optional)*: Source system identifier.
- **state** *(string, optional)*: Listing state, such as `active`.
- **geography.lat** *(number, optional)*: Latitude.
- **geography.lng** *(number, optional)*: Longitude.
- **product** *(string, optional)*: Listing promotion tier.
- **productLabel** *(string, optional)*: Display label for the promotion tier.
- **productVariant** *(string, optional)*: Promotion package variant.
- **title_l1** *(string, optional)*: Localized title variant.
- **title_l2** *(string, optional)*: Localized title variant.
- **title_l3** *(string, optional)*: Localized title variant.
- **externalId** *(string, optional)*: External listing identifier.
- **slug** *(string, optional)*: URL slug.
- **project.id** *(number, optional)*: Related project identifier.
- **project.externalId** *(string, optional)*: External project identifier.
- **project.completionStatus** *(string, optional)*: Project completion status.
- **project.agency.externalId** *(string, optional)*: Related project agency identifier.
- **project.agency.name** *(string, optional)*: Related project agency name.
- **project.agency.name_l1** *(string, optional)*: Localized project agency name.
- **project.agency.name_l2** *(string, optional)*: Localized project agency name.
- **project.agency.name_l3** *(string, optional)*: Localized project agency name.
- **project.agency.slug** *(string, optional)*: Related project agency slug.
- **project.agency.slug_l1** *(string, optional)*: Localized project agency slug.
- **project.agency.slug_l2** *(string, optional)*: Localized project agency slug.
- **project.agency.slug_l3** *(string, optional)*: Localized project agency slug.
- **createdAt** *(number, optional)*: Record creation timestamp.
- **updatedAt** *(number, optional)*: Record update timestamp.
- **reactivatedAt** *(number, optional)*: Reactivation timestamp when available.
- **rooms** *(number, optional)*: Alternate room count field.
- **baths** *(number, optional)*: Alternate bathroom count field.
- **coverPhoto.id** *(number, optional)*: Cover image identifier.
- **coverPhoto.externalId** *(string, optional)*: External cover image identifier.
- **coverPhoto.title** *(string, optional)*: Cover image title.
- **coverPhoto.orderIndex** *(number, optional)*: Cover image sort order.
- **coverPhoto.nimaScore** *(number, optional)*: Cover image quality score when available.
- **coverPhoto.main** *(boolean, optional)*: Whether the image is the primary cover image.
- **coverPhoto.type** *(string, optional)*: Cover image type.
- **photoCount** *(number, optional)*: Total number of photos.
- **videoCount** *(number, optional)*: Total number of videos.
- **panoramaCount** *(number, optional)*: Total number of panorama assets.
- **phoneNumber.mobile** *(string, optional)*: Primary mobile number.
- **phoneNumber.phone** *(string, optional)*: Primary phone number.
- **phoneNumber.whatsapp** *(string, optional)*: WhatsApp contact number.
- **phoneNumber.phoneNumbers** *(array[string], optional)*: Additional phone numbers.
- **phoneNumber.mobileNumbers** *(array[string], optional)*: Additional mobile numbers.
- **contactMethodAvailability.whatsapp** *(boolean, optional)*: Whether WhatsApp contact is available.
- **contactMethodAvailability.sms** *(boolean, optional)*: Whether SMS contact is available.
- **contactMethodAvailability.email** *(boolean, optional)*: Whether email contact is available.
- **contactMethodAvailability.call** *(boolean, optional)*: Whether call contact is available.
- **contactName** *(string, optional)*: Public contact name.
- **agency.id** *(number, optional)*: Agency identifier.
- **agency.objectId** *(number, optional)*: Agency object identifier.
- **agency.name** *(string, optional)*: Agency name.
- **agency.name_l1** *(string, optional)*: Localized agency name.
- **agency.name_l2** *(string, optional)*: Localized agency name.
- **agency.name_l3** *(string, optional)*: Localized agency name.
- **agency.externalId** *(string, optional)*: External agency identifier.
- **agency.product** *(string, optional)*: Agency promotion tier.
- **agency.productScore** *(number, optional)*: Agency promotion score.
- **agency.location** *(string, optional)*: Agency location.
- **agency.location_l1** *(string, optional)*: Localized agency location.
- **agency.location_l2** *(string, optional)*: Localized agency location.
- **agency.location_l3** *(string, optional)*: Localized agency location.
- **agency.licenses[]** *(array[object], optional)*: Agency license records.
- **agency.licenses[].number** *(string, optional)*: License number.
- **agency.licenses[].authority** *(string, optional)*: Issuing authority.
- **agency.logo.id** *(number, optional)*: Agency logo identifier.
- **agency.logo.url** *(string, optional)*: Agency logo URL.
- **agency.slug** *(string, optional)*: Agency slug.
- **agency.slug_l1** *(string, optional)*: Localized agency slug.
- **agency.slug_l2** *(string, optional)*: Localized agency slug.
- **agency.slug_l3** *(string, optional)*: Localized agency slug.
- **agency.tr** *(number, optional)*: Agency score or ranking field when present.
- **agency.roles** *(array[string], optional)*: Agency role labels.
- **agency.active** *(boolean, optional)*: Whether the agency is active.
- **agency.createdAt** *(string, optional)*: Agency creation timestamp.
- **agency.commercialNumber** *(string, optional)*: Commercial registration number when available.
- **agency.shortNumber** *(string, optional)*: Short contact number when available.
- **agency.type** *(string, optional)*: Agency record type label.
- **isVerified** *(boolean, optional)*: Whether the listing is verified.
- **verification.updatedAt** *(number, optional)*: Verification update timestamp.
- **verification.eligible** *(boolean, optional)*: Whether the listing is eligible for verification.
- **verification.status** *(string, optional)*: Verification status.
- **verification.verifiedAt** *(number, optional)*: Verification timestamp.
- **verification.trucheckedAt** *(number, optional)*: Trucheck timestamp.
- **extraFields.dldBuildingNK** *(string, optional)*: Extra building identifier.
- **extraFields.dldPropertySk** *(string, optional)*: Extra property identifier.
- **ownerAgent.externalId** *(string, optional)*: Owner agent identifier.
- **ownerAgent.name** *(string, optional)*: Owner agent name.
- **ownerAgent.name_l1** *(string, optional)*: Localized owner agent name.
- **ownerAgent.name_l2** *(string, optional)*: Localized owner agent name.
- **ownerAgent.name_l3** *(string, optional)*: Localized owner agent name.
- **ownerAgent.user_image** *(string, optional)*: Owner agent image URL.
- **ownerAgent.user_image_id** *(number, optional)*: Owner agent image identifier.
- **ownerAgent.isTruBroker** *(boolean, optional)*: Whether the agent has TruBroker status.
- **ownerAgent.slug** *(string, optional)*: Owner agent slug.
- **ownerAgent.state** *(string, optional)*: Owner agent state.
- **ownerAgent.isProfileCompleted** *(boolean, optional)*: Whether the agent profile is completed.
- **ownerAgent.isComplete** *(boolean, optional)*: Whether the agent record is complete.
- **offplanDetails.saleType** *(string, optional)*: Off-plan sale type.
- **offplanDetails.originalPrice** *(number, optional)*: Original price when provided.
- **offplanDetails.paidPrice** *(number, optional)*: Paid price when provided.
- **offplanDetails.dldWaiver** *(string, optional)*: DLD waiver detail when present.
- **completionDetails.startDate** *(number, optional)*: Project start date timestamp.
- **completionDetails.completionDate** *(number, optional)*: Expected completion date timestamp.
- **completionDetails.completionPercentage** *(number, optional)*: Completion progress percentage.
- **paymentPlanSummaries[]** *(array[object], optional)*: Payment plan summaries.
- **paymentPlanSummaries[].preHandoverPercentageSum** *(number, optional)*: Aggregate pre-handover percentage.
- **paymentPlanSummaries[].postHandoverPercentageSum** *(number, optional)*: Aggregate post-handover percentage.
- **paymentPlanSummaries[].breakdown.downPaymentPercentage** *(number, optional)*: Down payment share.
- **paymentPlanSummaries[].breakdown.preHandoverPercentage** *(number, optional)*: Pre-handover share.
- **paymentPlanSummaries[].breakdown.handoverPercentage** *(number, optional)*: Handover share.
- **paymentPlanSummaries[].breakdown.postHandoverPercentage** *(number, optional)*: Post-handover share.
- **agentAdStoriesCount** *(number, optional)*: Number of agent ad stories.
- **hasUnitPlan** *(boolean, optional)*: Whether a unit plan is present.
- **hasMatchingFloorPlans** *(boolean, optional)*: Whether matching floor plans are available.
- **photoIds** *(array[number], optional)*: Related photo identifiers.
- **hidePrice** *(boolean, optional)*: Whether price display is suppressed.
- **locationPurposeTier** *(number, optional)*: Location purpose tier.
- **objectId** *(string, optional)*: Object identifier.
- **searchId** *(number, optional)*: Search index identifier.
- **locationHierarchy[]** *(array[object], optional)*: Structured location hierarchy.
- **locationHierarchy[].id** *(number, optional)*: Location node identifier.
- **locationHierarchy[].level** *(number, optional)*: Depth in the location hierarchy.
- **locationHierarchy[].externalId** *(string, optional)*: External location identifier.
- **locationHierarchy[].name** *(string, optional)*: Location node name.
- **locationHierarchy[].name_l1** *(string, optional)*: Localized location name.
- **locationHierarchy[].name_l2** *(string, optional)*: Localized location name.
- **locationHierarchy[].name_l3** *(string, optional)*: Localized location name.
- **locationHierarchy[].slug** *(string, optional)*: Location path slug.
- **locationHierarchy[].type** *(string, optional)*: Location node type.
- **categoryHierarchy[]** *(array[object], optional)*: Structured category hierarchy.
- **categoryHierarchy[].id** *(number, optional)*: Category node identifier.
- **categoryHierarchy[].level** *(number, optional)*: Depth in the category hierarchy.
- **categoryHierarchy[].externalId** *(string, optional)*: External category identifier.
- **categoryHierarchy[].name** *(string, optional)*: Category name.
- **categoryHierarchy[].name_l1** *(string, optional)*: Localized category name.
- **categoryHierarchy[].name_l2** *(string, optional)*: Localized category name.
- **categoryHierarchy[].name_l3** *(string, optional)*: Localized category name.
- **categoryHierarchy[].slug** *(string, optional)*: Category slug.
- **categoryHierarchy[].slug_l1** *(string, optional)*: Localized category slug.
- **categoryHierarchy[].slug_l2** *(string, optional)*: Localized category slug.
- **categoryHierarchy[].slug_l3** *(string, optional)*: Localized category slug.
- **categoryHierarchy[].nameSingular** *(string, optional)*: Singular category name.
- **categoryHierarchy[].nameSingular_l1** *(string, optional)*: Localized singular category name.
- **categoryHierarchy[].nameSingular_l2** *(string, optional)*: Localized singular category name.
- **categoryHierarchy[].nameSingular_l3** *(string, optional)*: Localized singular category name.

### Agency fields (`type = "agency"`)

- **title** *(string, required)*: Agency display name.
- **location** *(string, optional)*: Primary agency location.
- **agencyName** *(string, optional)*: Agency name, repeated for convenience.
- **purpose** *(string, optional)*: Purpose coverage, such as `for-sale for-rent`.
- **name_l1** *(string, optional)*: Localized agency name.
- **name_l2** *(string, optional)*: Localized agency name.
- **name_l3** *(string, optional)*: Localized agency name.
- **agentsCount** *(number, optional)*: Number of agents associated with the agency.
- **externalId** *(string, optional)*: External agency identifier.
- **product** *(string, optional)*: Agency promotion tier.
- **logo.id** *(number, optional)*: Logo identifier.
- **logo.url** *(string, optional)*: Logo URL.
- **slug** *(string, optional)*: Agency slug.
- **slug_l1** *(string, optional)*: Localized agency slug.
- **slug_l2** *(string, optional)*: Localized agency slug.
- **slug_l3** *(string, optional)*: Localized agency slug.
- **locations[]** *(array[object], optional)*: Locations associated with the agency.
- **locations[].id** *(number, optional)*: Location identifier.
- **locations[].objectId** *(number, optional)*: Location object identifier.
- **locations[].name** *(string, optional)*: Location name.
- **locations[].name_l1** *(string, optional)*: Localized location name.
- **locations[].name_l2** *(string, optional)*: Localized location name.
- **locations[].name_l3** *(string, optional)*: Localized location name.
- **locations[].externalId** *(string, optional)*: External location identifier.
- **locations[].slug** *(string, optional)*: Location slug.
- **locations[].slug_l1** *(string, optional)*: Localized location slug.
- **locations[].slug_l2** *(string, optional)*: Localized location slug.
- **locations[].slug_l3** *(string, optional)*: Localized location slug.
- **locations[].geography.lat** *(number, optional)*: Location latitude.
- **locations[].geography.lng** *(number, optional)*: Location longitude.
- **locations[].geo_point** *(array[number], optional)*: Longitude and latitude pair.
- **locations[].level** *(number, optional)*: Hierarchy depth.
- **locations[].hierarchy[]** *(array[object], optional)*: Parent location hierarchy.
- **locations[].hierarchy[].id** *(number, optional)*: Parent location identifier.
- **locations[].hierarchy[].level** *(number, optional)*: Parent location depth.
- **locations[].hierarchy[].externalId** *(string, optional)*: Parent location external identifier.
- **locations[].hierarchy[].name** *(string, optional)*: Parent location name.
- **locations[].hierarchy[].name_l1** *(string, optional)*: Localized parent location name.
- **locations[].hierarchy[].name_l2** *(string, optional)*: Localized parent location name.
- **locations[].hierarchy[].name_l3** *(string, optional)*: Localized parent location name.
- **locations[].hierarchy[].slug** *(string, optional)*: Parent location slug.
- **locations[].hierarchy[].slug_l1** *(string, optional)*: Localized parent location slug.
- **locations[].hierarchy[].slug_l2** *(string, optional)*: Localized parent location slug.
- **locations[].hierarchy[].slug_l3** *(string, optional)*: Localized parent location slug.
- **locations[].adCount** *(number, optional)*: Number of ads in that location.
- **locations[].aliases** *(array[string], optional)*: Alternate location names.
- **locations[].type** *(string, optional)*: Location type.
- **locations[].trackID** *(string, optional)*: Tracking identifier.
- **locations[].roles** *(array[string], optional)*: Location roles.
- **locations[].completionStatus** *(string, optional)*: Completion status coverage for the location.
- **locations[].hasChildren** *(boolean, optional)*: Whether the location has child nodes.
- **stats.adsSaleCount** *(number, optional)*: Number of sale ads.
- **stats.adsRentCount** *(number, optional)*: Number of rental ads.
- **stats.adsCount** *(number, optional)*: Total ads count.
- **stats.purposes** *(array[string], optional)*: Purpose categories covered by the agency.
- **stats.locationsWithAds** *(array[number], optional)*: Location identifiers where the agency has ads.
- **stats.trubrokerAgentCount** *(number, optional)*: Number of TruBroker agents.
- **stats.trubrokerAgentsProfileImageIDs** *(array[number], optional)*: Image identifiers for TruBroker profiles.
- **stats.categoryTypes** *(array[string], optional)*: Property categories covered by the agency.
- **stats.categoryTypes_l1** *(array[string], optional)*: Localized property categories.
- **stats.categoryTypes_l2** *(array[string], optional)*: Localized property categories.
- **stats.categoryTypes_l3** *(array[string], optional)*: Localized property categories.
- **stats.serviceAreas** *(array[string], optional)*: Agency service areas.
- **stats.serviceAreas_l1** *(array[string], optional)*: Localized service areas.
- **stats.serviceAreas_l2** *(array[string], optional)*: Localized service areas.
- **stats.serviceAreas_l3** *(array[string], optional)*: Localized service areas.
- **phoneNumber** *(object, optional)*: Phone data object, which may be empty.
- **contactMethodAvailability.sms** *(boolean, optional)*: Whether SMS contact is available.
- **contactMethodAvailability.email** *(boolean, optional)*: Whether email contact is available.
- **contactMethodAvailability.call** *(boolean, optional)*: Whether call contact is available.
- **createdAt** *(string, optional)*: Agency record creation timestamp.
- **agencySg** *(number, optional)*: Agency grouping field when present.
- **exStatus** *(number, optional)*: Agency status field when present.
- **eliteStatus** *(boolean, optional)*: Whether the agency has elite status.
- **objectId** *(string, optional)*: Agency object identifier.
- **searchId** *(number, optional)*: Search index identifier.

## Data guarantees & handling

- **Best-effort extraction:** fields may vary by region, session, availability, and UI experiments.
- **Optional fields:** null-check in downstream code.
- **Deduplication:** recommend `type + ":" + id`.

## How to Run on Apify

1. Open the Actor in Apify Console.
2. Configure your listing type, location, and any optional property, price, size, developer, agent, or keyword filters.
3. Set the maximum number of outputs to collect.
4. Click **Start** and wait for the run to finish.
5. Download results in JSON, CSV, Excel, or other supported formats.

## Scheduling & Automation

### Scheduling

**Automated Data Collection**

You can schedule recurring runs to keep your property and agency dataset fresh without manual intervention. This is useful for regular market snapshots, rental tracking, and ongoing monitoring workflows.

- Navigate to **Schedules** in Apify Console
- Create a new schedule (daily, weekly, or custom cron)
- Configure input parameters
- Enable notifications for run completion
- Optional: add webhooks for automated processing

### Integration Options

- **Webhooks:** Trigger downstream actions when a run completes.
- **Zapier:** Connect to 5,000+ apps without coding.
- **Make (Integromat):** Build multi-step automation workflows.
- **Google Sheets:** Export results to a spreadsheet.
- **Slack/Discord:** Receive notifications and summaries.
- **Email:** Send automated reports via email.

## Performance

- **Small runs (< 1,000 outputs):** ~2–3 minutes
- **Medium runs (1,000–5,000 outputs):** ~5–15 minutes
- **Large runs (5,000+ outputs):** ~15–30 minutes

Execution time varies based on filters, result volume, and how much information is returned per record.

## Compliance & Ethics

### Responsible Data Collection

This actor collects publicly available **real estate listing and agency** information from **[https://www.bayut.com](https://www.bayut.com)** for legitimate business purposes. Common use cases include:

- **Real estate** research and market analysis
- **Pricing intelligence and rental tracking**
- **Listings enrichment and portfolio monitoring**

Users are responsible for ensuring their collection and use of data complies with applicable laws, regulations, and the target site's terms. This section is informational and not legal advice.

### Best Practices

- Use collected data in accordance with applicable laws, regulations, and the target site's terms
- Respect individual privacy and personal information
- Use data responsibly and avoid disruptive or excessive collection
- Do not use this actor for spamming, harassment, or other harmful purposes
- Follow relevant data protection requirements where applicable (e.g., GDPR, CCPA)

## Support

For help, use the Issues section on the actor page or contact through the actor page support channel. Include the input you used with any sensitive values redacted, the run ID, a short note on expected versus actual behavior, and, if helpful, a small output sample.