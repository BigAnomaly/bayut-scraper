[Bayut Scraper](https://apify.com/dhrumil/bayut-scraper?fpr=data)

## 🏡 What is Bayut Real Estate Properties Scraper?

This Bayut properties Scraper will enable you scrape any sale/rent listing from  collection from [bayut.com](https://www.bayut.com/).

You can simply take your listing url from browser and enter it into this actor. This actor will crawl through all pages of particular listing and generate dataset for you.

Listing url is something you get when you perform the search on bayut site. Example listing urls :

- [https://www.bayut.com/for-sale/property/dubai/al-satwa/](https://www.bayut.com/for-sale/property/dubai/al-satwa/)
- [https://www.bayut.com/to-rent/property/dubai/al-satwa/](https://www.bayut.com/to-rent/property/dubai/al-satwa/)
- [https://www.bayut.com/for-sale/3-bedroom-apartments/dubai/dubai-marina/](https://www.bayut.com/for-sale/3-bedroom-apartments/dubai/dubai-marina/)

## 🚪 What can this Bayut Scraper do?

📈 Extract Bayut market data listings on Bayut

👀 This actor is not just scraper but also has monitoring capability. You can turn on monitoring mode and it will give you only newly added properties compared to your previous scrapes.

📩  This actor also helps yu to identify which properties are not listed anymore. Please refer to Identifying delisted properties

⬇️ Download Bayut real estate data in Excel, CSV, JSON, and other formats

## 📚 How do I start scraping with this scraper?

1. Register for your free Apify account [here](https://apify.com/pricing?fpr=z2di7)
2. You don't need to provide your credit card details for free acount. Just click on "Get Started" button on above link and complete the registration only.
3. Free account comes with reasonable credits to try out this actor. This actor also comes with free trial of 3 days without any commitment/upfront charge.
4. Run this actor and verify the scraped data. Apify has huge integration possibilities. You can download the data or push the data into any 3rd party platform directly.

## 🌳 What data can I extract using this tool?

| 📝 | 📝 |
| --- | --- |
| Listing Title | Full Address (displayAddress) |
| Listing URL | Reference Number |
| Permit Number | DED License |
| Bathrooms | Bedrooms |
| Agent Name | Agent Phone |
| Listing Type | Property Type |
| Latitude | Longitude |
| Completion Status | Agency Name |
| Text Description | Formatted HTML Description |
| Amenities | Images |
| Price | Size (sqft) |
| RERA | BRN |
| Furnishing | Zone Name |
| Added On | Community Name |
| Building Name | Broker Info |
| Price Duration | Price Currency |
| Coordinates | Verified |
| Broker License | Similar Transactions |

This tool extracts comprehensive property data including all the above fields for each listing.

## ⬇️ Input

For simple usecase, you just need to provide browser url of search result page & that's all. You can leave other fields as they are to be sensible defaults.

### Input example

```
{
    "listUrls": [
        {
            "url": ""
        }
    ],
    "monitoringMode": false,
	"retrieveUnitNumber" : false,
    "fullPropertyDetails" : false,
    "enableDelistingTracker" : false,
    "addEmptyTrackerRecord" : false
}
```

Understading monitoring mode :

- `monitoringMode` : This option when turned on will only scrape newly added property listings compared to previously scraped properties by this actor. When you keep this option on, it will scraper full list for the first time and then in next run, it will scrape only newly found incremental data.
- `retrieveUnitNumber` : This provides you Unit number of property as well. Turn this on, only if you have [Dubai Property Unit Finder](https://apify.com/dhrumil/dubai-property-unit-finder?fpr=z2di7) actor with you.
- `fullPropertyDetails` : If you don't need aminities, description and photos, please keep this option off. It will increase the scraping speed by multi fold.
- `enableDelistingTracker` : This option when turned on will start tracking date against each property under Apify Key Value store. This KV store can be queried later to find out which properties are delisted.
- `addEmptyTrackerRecord` : This option when turned on will add empty record having only id of property to Apify dataset. This helps you identify whether property is still listed compared to your own database in incremental mode.

## ⬆️ Output

The scraped data is stored in the dataset of each run. The data can be viewed or downloaded in many popular formats, such as *JSON, CSV, Excel, XML, RSS, and HTML*.

### Output example

The result for scraping a single property like this:

```
{
	"id": "11578179",
	"url": "<<property url here>>",
	"title": "2BR + Maid l Prime Location l 0% Commission",
	"displayAddress": "Asas Garden City 2, Jumeirah Garden City, Al Satwa, Dubai, UAE",
	"buildingName": "Asas Garden City 2",
	"communityName": "Jumeirah Garden City",
	"bedrooms": 2,
	"bathrooms": 4,
	"addedOn": {},
	"broker": "fäm Properties - Branch 26",
	"agent": "Mohammed Isham Mohammed",
	"agentInfo": null,
	"agentPhone": "+97144469149",
	"agentWhatsapp": null,
	"agentEmail": null,
	"verified": true,
	"reference": "B-AS-134509",
	"brokerLicenseNumber": "613164",
	"brokerInfo": {
		"active": true,
		"createdAt": "2025-01-30T14:28:10+00:00",
		"externalID": "106435",
		"id": 29876194,
		"licenses": [
			{
				"number": "613164",
				"authority": "DED"
			},
			{
				"number": "1858",
				"authority": "RERA"
			},
			{
				"number": "718828",
				"authority": "DED"
			},
			{
				"number": "978711",
				"authority": "DED"
			}
		],
		"logo": {
			"id": 758550680,
			"url": "<<logo url here>>"
		},
		"name": "fäm Properties - Branch 26",
		"objectID": 29876194,
		"performanceCohort": "underachieving",
		"product": "premium",
		"productScore": 2,
		"roles": [],
		"slug": "fam-properties-branch-26-106435",
		"tier": 1,
		"tr": 1,
		"type": "agency"
	},
	"propertyType": "Apartments",
	"price": 2175000,
	"rera": "71693993635",
	"priceCurrency": "AED",
	"coordinates": {
		"latitude": 25.220599416827,
		"longitude": 55.275293281259
	},
	"type": "for-sale",
	"zoneName": "Al Satwa",
	"size": "1273.00",
	"sizeMin": "1273.00 sqft",
	"furnishing": "unfurnished",
	"amenities": [
		"Centrally Air-Conditioned",
		"Balcony or Terrace",
		"Maids Room"
	],
	"photos": [
		"<<photo urls here>>"
	],
	"descriptionHTML": "<<Formatted description here>>"
}
```

## 💸 Pricing Model & Usage Logic

This actor uses a tiered pay-per-event pricing model, with usage tracked and charged based on the number of properties processed and additional multipliers. Charges are triggered at specific usage thresholds and events.

### 🟢 Charge Events & Tiers

The actor uses a tiered pricing model based on the number of properties processed. Each tier has a specific charge event and rate per 1,000 properties:

> **🔻 Cost Efficiency as You Scale:**
> The tier-based pricing model is designed to reduce your cost per property as your usage increases. The more properties you process, the lower your per-unit cost becomes, helping keep your overall costs under control as you scale up to higher volumes.

#### Starter Tier (`starter-tier-1K`)

For the first 25,000 properties processed, the cost per 1,000 properties is **$10 USD**.
This tier is ideal for small to medium jobs and ensures a low entry cost for initial usage.

#### Growth Tier (`growth-tier-1K`)

For properties processed from 25,000 up to 50,000 the cost per 1,000 properties drops to **$8 USD**.
This tier rewards higher volume usage with a reduced rate, making it cost-effective for scaling up.

#### Scale Tier (`scale-tier-1K`)

For properties processed from 50,000 up to 100,000 the cost per 1,000 properties is **$6 USD**.
This tier is designed for large-scale operations, offering further discounts as your volume increases.

#### Enterprise Tier (`enterprise-tier-1K`)

For properties processed above 100,000 the cost per 1,000 properties is **$5 USD**.
This tier is for enterprise-level usage, providing the lowest rate for very high-volume processing.

Each charge event is triggered automatically as your processed property count crosses into the next tier. The actor tracks usage and applies the correct rate for each tier, ensuring transparent and predictable billing.

These pricing tiers are applied on a **monthly** basis, and your usage count resets at the start of each new month. This ensures you always start fresh and only pay for what you use each month.

#### Example:

- Scraping 100,000 properties in a month:

- $10 per 1K properties for the first 10,000 properties ($100)
- $8 per 1K properties upto 25,000 properties ($120)
- $6 per 1K properties upto 50,000 properties ($150)
- $5 per 1K properties above 50,000 properties ($250)
- **Total:** $620

### ⚡ Additional Usage Parameters (Multipliers)

The actor may apply additional usage multipliers based on your input settings. These do **not** directly charge you extra, but they affect how quickly you use up your monthly quota. The more features you enable, the faster your included usage is consumed.

- **🌐 Residential Proxy Usage:** If you use a residential proxy, an additional 5x usage multiplier will apply. This is due to the higher cost and complexity of residential proxy traffic.
- **🧠 Memory Usage:** If you run the actor with more than 2048 MB of memory, you will be charged an additional usage multiplier. For example, running at 4096 MB will double your usage cost.
- **🏷️ Full Property Details:** Enabling `fullPropertyDetails` will increase your usage multiplier by 5x, as it requires scraping more data per property.
- **🏢 Retrieve Unit Number:** Enabling `retrieveUnitNumber` will increase your usage multiplier by 2x, as it requires additional data extraction per property.
- **🔄 Monitoring Mode:** Enabling `monitoringMode` adds 2 propery count for retrival of tracked propery and 4 properies count as usage storing and tracking new property, as it requires additional logic and storage for incremental scraping.
- **🕵️ Enable Delisting Tracker:** Enabling `enableDelistingTracker` adds 1x to your usage multiplier.
- **📄 Add Empty Tracker Record:** Enabling `addEmptyTrackerRecord` doesn't add any value to multiplier. But it causes flat 1 property count usage (without multiplier) when tracker record is getting pushed.

These multipliers are **cumulative**. For example, if you enable both `fullPropertyDetails` and `enableDelistingTracker`, your additional usage for each property will be by 6x.

> **💡 Tip:**
> For best cost efficiency, run this actor on **2048 MB memory**. The actor is highly optimized for this setting, and using more memory will increase your additional usage charges. Only increase memory if you have a specific need.

## 🏢🔎 Finding Unit Number (Unit No.)

This actor is now **directly integrated** with the [Dubai Property Unit Finder](https://apify.com/dhrumil/dubai-property-unit-finder?fpr=z2di7) actor! 🚀

With this integration, you can:

- Apply a filter or select all properties from a particular building on Bayut.
- Simply turn on the `retrieveUnitNumber` option in your input.
- Instantly get the **unit numbers for all properties in that building**—in one go! Super easy and powerful. 🏢➡️🔢

No more manual lookups or separate runs. Just enable the option and let the integration do the work for you!

> **Note:**
> The Dubai Property Unit Finder actor has its **own pricing and billing**, which is **separate** from this Bayut scraper. When using integration mode, both actors will be billed independently according to their respective pricing models.

## 🔁 Deduplication handled

If multiple list urls contains overlapping results, they will get deduplicated within same run data.

## ⚠️ Disclaimer

This is not an official API provided by bayut. This is just a tool which helps you automate reading public information available on Bayut. This page or tool doesn't store any information protected by IP rights of Bayut. Developer doesn't even store any information available publically on Bayut site. Developer just provides the automation tool and have no obligation towards who/how someone use this tool and make use of the information.

## 🚫 Limitations

Since site allows only 50000 properties per listing/search result, you might want to break down your listing urls into smaller area if it has more than 50K results. Good News is that even if multiple list urls contains overlapping results, they will get deduplicated within same run data.

## 🤝 Related Actors (You may also like)

- [🏠 Property Finder Scraper](https://apify.com/dhrumil/propertyfinder-scraper?fpr=z2di7)
- [🏢 Bayut Scraper](https://apify.com/dhrumil/bayut-scraper?fpr=z2di7)
- [🏡 Dubizzle Scraper](https://apify.com/dhrumil/dubizzle-scraper?fpr=z2di7)
- [🔍 UAE Dubai Property Owner Finder](https://apify.com/dhrumil/uae-dubai-property-owner-finder?fpr=z2di7)
- [🏢 Dubai Property Unit Finder](https://apify.com/dhrumil/dubai-property-unit-finder?fpr=z2di7)

## 🔎 Identifying delisted properties

This actor provides you monitoring mode configuration using which you can get only incremental updates about newly added properties. In case, you also want to identify which properties are delisted from platform, you can use any of the following techniques with the help of this actor.

1. Running Always in full scraper mode :
Run this actor always in full scrape mode and cross check the new incoming batch of data with your existing database. If any property that exists in yoru database but not in newly scraped data batch, that means it's not listed anymore
2. Use Key Value Store generated by scraper :
If your are monitoring very large batch of data and you don't want to scrape everything all the time, this method involves bit of technicality but achieves the goal efectively. Apify has storage feature called [Key-value store](https://docs.apify.com/api/v2/#/reference/key-value-stores/key-collection/get-list-of-keys). When you run this scrape, this scraper stores every single property in key value store along with timestamp in apify store. Inside this store, key is property id itself and value is timestamp like this

```
{ lastSeen : '2023-11-02T05:59:25.763Z'}
```

Whenever you run this scraper, it will update the timestamp against particular id if it finds property on the platform. e.g. if we have 2 proprties with id `prop1` and `prop2` and we scraped them both on November 1, key value storage would look like this :

```
prop1 -> { lastSeen : '2023-11-01T05:59:25.763Z'}
prop2 -> { lastSeen : '2023-11-01T05:59:25.763Z'}
```

Now if you run this scraper again on December 1 and prop1 is not on the platform anymore but prop2 is still there, key value storage would change like this :

```
prop1 -> { lastSeen : '2023-11-01T05:59:25.763Z'}
prop2 -> { lastSeen : '2023-12-01T05:59:25.763Z'}
```

That means if any property has `lastSeen` less than latest batch you loaded, that property is delisted now. You can directly iterate through whole Key value storage using Apify key value storage API to identify this. Please refer to [this](https://docs.apify.com/api/v2/#/reference/key-value-stores/key-collection/get-list-of-keys) API documentation to do the same.

Alternatively, you can iterate through your existing database active properties and use [this](https://docs.apify.com/api/v2/#/reference/key-value-stores/record/get-record) API to identify listing status.

For this approach to work, it's important that you enable this feature via `enableDelistingTracker` (Enable Delisting tracker) input.