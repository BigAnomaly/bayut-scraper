[Bayut Scraper](https://apify.com/ahmed_jasarevic/bayut-scraper?fpr=data)

# 🏗️ High-Fidelity Bayut Real Estate & Project Scraper

Maximize your real estate market intelligence with the most comprehensive **Bayut.com Scraper** on the Apify platform. Unlike standard tools, this Actor extracts deep-level JSON metadata, providing a 360-degree view of property projects, developer portfolios, and financial structures in Dubai and the UAE.

## 🌟 Why This Scraper Outperforms the Rest

When scraping high-security platforms like Bayut, most bots get blocked by Cloudflare or return "surface-level" data. Our solution uses **Playwright Stealth technology** to mimic human behavior and tap into internal API endpoints, delivering data that is usually hidden from the front-end user.

### 💎 Premium Data Points Extracted:

- **Detailed Payment Plans:** Extract full milestone breakdowns (e.g., 20% downpayment, 1% monthly installments). Perfect for financial analysis and mortgage lead gen.
- **Exact Geolocation:** High-precision `lat` and `lng` coordinates and internal `geography` objects for GIS mapping and heatmaps.
- **Developer & Agency Insights:** Full profiles of developers (like DAMAC, Emaar), including logos, licensing info, and creation dates.
- **Unit Breakdown & Availability:** Detailed lists of every unit type within a project (Villas, Townhouses, Apartments) with specific area sizes (`areaMin`, `areaMax`) and pricing.
- **Multilingual Content:** Full descriptions and titles in **English, Arabic (l1), Chinese (l2), and Russian (l3)**—ideal for international real estate portals.
- **High-Res Media:** Direct S3 links to cover photos, marketing images, and 3D floor plans.

---

## 🚀 Key Features & SEO Benefits

- **Anti-Bot Bypass (WAF Protection):** Engineered to bypass Cloudflare and perimeter security using residential proxies and human-like interaction intervals.
- **SEO-Ready Output:** The data is structured in clean JSON/CSV formats, ready to be imported into your own real estate website to boost your local SEO with fresh, detailed content.
- **Smart Pagination:** Handles Bayut’s strict `page_size` limits (max 24) automatically, ensuring you don't miss a single listing.
- **Advanced Amenities Mapping:** Categorized features from "Health and Fitness" (Swimming Pools, Gyms) to "Family & Recreation" (Cafeterias, Parks).

---

## 📊 Data Schema Preview

Every result provides a massive JSON object. Below is a snapshot of the high-value fields you will receive:

| Field | Description | Use Case |
| --- | --- | --- |
| `paymentPlans` | Full financial breakdown of installments | ROI & Financial Modeling |
| `_geoloc` | Precise GPS coordinates | Interactive Map Integrations |
| `description_l1` | Native Arabic descriptions | Multi-language Website Support |
| `unitCategories` | Breakdown of unit types (Villas vs Townhouses) | Inventory Analysis |
| `amenities` | Lists of building/community features | Feature-based Filtering |

---

## ⚙️ How to Start Scraping

1. **Start URL:** Go to [Bayut.com](https://www.bayut.com), apply your filters (Location, Category, Purpose), and copy the resulting URL or the API search endpoint.
2. **Max Pages:** Set the depth of your crawl (e.g., 10 pages will yield up to 240 projects).
3. **Proxy Configuration:** **MANDATORY.** Use Apify Residential Proxies (Targeting UAE is recommended for the best bypass rates).
4. **Launch:** Hit "Run" and watch the dataset populate with rich, actionable data.

---

## 📥 Input Configuration

The Actor accepts a JSON configuration that allows you to pinpoint exactly what data you need. Below is an example of a standard setup using **Residential Proxies** (highly recommended for stability).

### Input Example

```
{
  "startUrl": "https://www.bayut.com/api/projects/cpl/search?category=1&location=5003&purpose=for-sale",
  "maxPages": 3,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": [
      "RESIDENTIAL"
    ],
    "countryCode": "AE"
  }
}
```

### Input Fields Breakdown:

- **`startUrl`** (Required): The initial API search URL from Bayut. You can easily obtain this by filtering properties on the website and copying the request URL. It contains parameters like `location`, `category`, and `purpose`.
- **`maxPages`** (Optional): Defines the depth of the scrape. Each page typically contains **24 high-fidelity project listings**. Default is `5`.
- **`proxyConfiguration`** (Required): To bypass sophisticated WAF (Web Application Firewalls), the use of **Residential Proxies** with UAE (`AE`) country targeting is essential.

---

## 📤 Output Data Structure

The scraper produces a comprehensive dataset where each item represents a detailed project or property listing. Unlike basic scrapers, this output includes **nested objects** for financial plans, multilingual SEO content, and precise geospatial data.

### Key Output Fields Highlight:

- **`id` & `externalID`**: Unique identifiers for database synchronization and duplicate prevention.
- **`title` & `slug`**: SEO-friendly titles and URL slugs in multiple languages (English, Arabic, etc.).
- **`_geoloc`**: Precise latitude and longitude for map rendering and spatial analysis.
- **`price`**: Raw numerical price values, ideal for market trend calculations and currency conversions.
- **`description`**: Full HTML-formatted descriptions containing marketing copy and project highlights.
- **`paymentPlans`**: A detailed array of payment milestones, percentages, and installment descriptions.
- **`units`**: An array of available unit types within the project, including room counts, area sizes, and specific price ranges for each.
- **`agency`**: Complete developer/agency profile including brand names and high-resolution logos.
- **`amenities`**: Categorized lists of building features (e.g., "Health and Fitness", "Recreation and Family").
- **`photos`**: An array of marketing image objects with direct URLs to Bayut's high-res CDN.

---

```
{
	"id": 8921427,
	"objectID": 8921427,
	"ownerID": null,
	"externalID": "2826",
	"type": "project",
	"hash": "3118c65",
	"slug": "hayat_3-2826",
	"state": "active",
	"purpose": "for-sale",
	"_geoloc": {
		"lat": 24.855907523683,
		"lng": 55.106394865459
	},
	"geography": {
		"lat": 24.855907523683,
		"lng": 55.106394865459
	},
	"product": null,
	"description": "<p>Dubai South introduces Hayat 3, an upcoming development designed to offer a modern lifestyle. The freehold project will feature a range of spacious residences, designed to cater to contemporary family living. The design will incorporate large windows and open-plan layouts to maximise natural light and ventilation, while high-quality finishes provide a refined and modern aesthetic. Surrounded by landscaped green spaces and pedestrian-friendly pathways, the off-plan community will promote a healthy and sustainable lifestyle. The development by Dubai South will be positioned within a rapidly expanding area that benefits from proximity to Al Maktoum International Airport, major highways, schools and leisure destinations. </p>",
	"description_l1": "<p>أطلقت شركة دبي الجنوب العقارية مشروع حياة 3 السكني في منطقة دبي الجنوب، وهو مشروع سكني قيد الإنشاء، مصمم لتوفير نمط حياة عصري ومتكامل. يتضمن المشروع مجموعة متنوعة من الوحدات السكنية الفسيحة التي تلائم متطلبات العائلات الحديثة. ويعتمد تصميم هذه المنازل على النوافذ الواسعة والمخططات الداخلية المفتوحة لتعزيز الإضاءة والتهوية الطبيعية، مع تشطيبات عالية الجودة تبرز الطابع العصري. </p><p>\n</p><p>يمتاز المشروع كذلك بمساحاته الخضراء وممراته الصديقة للمشاة، مما يعزز من أسلوب الحياة الصحي والمستدام. كما يقع ضمن منطقة حيوية بالقرب من مطار آل مكتوم الدولي، والطرق السريعة الرئيسية، مما يتيح للسكان الوصول بسهولة إلى العديد من خيارات المدارس والمتاجر والوجهات الترفيهية. </p>",
	"description_l2": "<p>Dubai South introduces Hayat 3, an upcoming development designed to offer a modern lifestyle. The freehold project will feature a range of spacious residences, designed to cater to contemporary family living. The design will incorporate large windows and open-plan layouts to maximise natural light and ventilation, while high-quality finishes provide a refined and modern aesthetic. Surrounded by landscaped green spaces and pedestrian-friendly pathways, the off-plan community will promote a healthy and sustainable lifestyle. The development by Dubai South will be positioned within a rapidly expanding area that benefits from proximity to Al Maktoum International Airport, major highways, schools and leisure destinations. </p>",
	"description_l3": "<p>Dubai South introduces Hayat 3, an upcoming development designed to offer a modern lifestyle. The freehold project will feature a range of spacious residences, designed to cater to contemporary family living. The design will incorporate large windows and open-plan layouts to maximise natural light and ventilation, while high-quality finishes provide a refined and modern aesthetic. Surrounded by landscaped green spaces and pedestrian-friendly pathways, the off-plan community will promote a healthy and sustainable lifestyle. The development by Dubai South will be positioned within a rapidly expanding area that benefits from proximity to Al Maktoum International Airport, major highways, schools and leisure destinations. </p>",
	"location": [
		{
			"id": 1,
			"level": 0,
			"externalID": "5001",
			"name": "UAE",
			"name_l1": "الإمارات",
			"name_l2": "阿联酋",
			"name_l3": "ОАЭ",
			"slug": "/uae"
		},
		{
			"id": 2,
			"level": 1,
			"externalID": "5002",
			"name": "Dubai",
			"name_l1": "دبي",
			"name_l2": "迪拜",
			"name_l3": "Дубай",
			"slug": "/dubai"
		},
		{
			"id": 3355,
			"level": 2,
			"externalID": "8881",
			"name": "Dubai South",
			"name_l1": "دبي الجنوب",
			"name_l2": "迪拜南部街区",
			"name_l3": "Дубай Саут",
			"slug": "/dubai/dubai-south",
			"type": "neighbourhood"
		},
		{
			"id": 89211,
			"level": 3,
			"externalID": "22194",
			"name": "Hayat",
			"name_l1": "حياة",
			"name_l2": "Hayat",
			"name_l3": "Hayat",
			"slug": "/dubai/dubai-south/hayat",
			"type": "neighbourhood"
		},
		{
			"id": 89214,
			"level": 4,
			"externalID": "22196",
			"name": "Hayat 3",
			"name_l1": "حياة 3",
			"name_l2": "Hayat 3",
			"name_l3": "Hayat 3",
			"slug": "/dubai/dubai-south/hayat/hayat-3",
			"type": "neighbourhood"
		}
	],
	"category": [
		{
			"id": 1,
			"level": 0,
			"externalID": "1",
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
			"id": 8,
			"level": 1,
			"externalID": "16",
			"name": "Townhouses",
			"name_l1": "تاون هاوس",
			"name_l2": "联排别墅",
			"name_l3": "Таунхаусы",
			"slug": "townhouses",
			"slug_l1": "townhouses",
			"slug_l2": "townhouses",
			"slug_l3": "townhouses",
			"nameSingular": "Townhouse",
			"nameSingular_l1": "تاون هاوس",
			"nameSingular_l2": "联排别墅",
			"nameSingular_l3": "Таунхаус"
		}
	],
	"agency": {
		"id": 29796754,
		"objectID": 29796754,
		"name": "Dubai South",
		"name_l1": "دبي الجنوب",
		"name_l2": "Dubai South",
		"name_l3": "Dubai South",
		"externalID": "581",
		"product": null,
		"productScore": null,
		"location": null,
		"licenses": [],
		"logo": {
			"id": 676991372,
			"url": "https://bayut-production.s3.eu-central-1.amazonaws.com/image/676991372/0803d11fc9f24686aa268ad21e175ce2"
		},
		"slug": "dubai-south",
		"slug_l1": "دبي-الجنوب",
		"slug_l2": "dubai-south",
		"slug_l3": "dubai-south",
		"tr": 4,
		"roles": [],
		"active": true,
		"createdAt": "2024-04-24T10:26:46.458242+00:00",
		"commercialNumber": null,
		"shortNumber": null,
		"type": "developer"
	},
	"rooms": 3,
	"baths": 0,
	"area": 298.86907968,
	"price": 3400000,
	"hidePrice": false,
	"createdAt": 1751978766.828013,
	"updatedAt": 1751978766.82802,
	"extraFields": {
		"dldPropertySK": "2826"
	},
	"coverPhoto": {
		"id": 783762457,
		"externalID": "15678",
		"title": "Cover Image",
		"orderIndex": 1,
		"nimaScore": 6.0173739231765335,
		"main": true,
		"type": "listing"
	},
	"photoIDs": [
		783762457,
		823521689,
		823521692,
		823521693
	],
	"photos": [
		{
			"id": 783762457,
			"externalID": "15678",
			"title": "Cover Image",
			"orderIndex": 1,
			"nimaScore": 6.0173739231765335,
			"type": "listing"
		},
		{
			"id": 823521689,
			"externalID": "18285",
			"title": "Marketing Image 1",
			"orderIndex": 2,
			"nimaScore": 7.691161165056201,
			"type": "listing"
		},
		{
			"id": 823521692,
			"externalID": "18286",
			"title": "Marketing Image 2",
			"orderIndex": 3,
			"nimaScore": 6.917353956536431,
			"type": "listing"
		},
		{
			"id": 823521693,
			"externalID": "18287",
			"title": "Marketing Image 3",
			"orderIndex": 4,
			"nimaScore": 5.908861309751444,
			"type": "listing"
		}
	],
	"floorPlans": [],
	"videos": [],
	"amenities": [
		{
			"externalGroupID": 3,
			"groupRank": 3,
			"text": "Health and Fitness",
			"text_l1": "الصحة و اللياقة",
			"text_l2": "阳台",
			"text_l3": "Здоровье и Фитнесс",
			"amenities": [
				{
					"text": "Gym or Health Club",
					"text_l1": "صالة رياضية أو نادي صحي",
					"text_l2": "健身房或健身俱乐部",
					"text_l3": "Тренажерный зал или оздоровительный клуб",
					"value": "",
					"rank": 3,
					"slug": "gym-or-health-club",
					"format": "checkbox",
					"externalID": 22
				},
				{
					"text": "Swimming Pool",
					"text_l1": "مسبح",
					"text_l2": "附近医院",
					"text_l3": "Бассейн",
					"value": "",
					"rank": 6,
					"slug": "swimming-pool",
					"format": "checkbox",
					"externalID": 45
				}
			]
		},
		{
			"externalGroupID": 2,
			"groupRank": 4,
			"text": "Recreation and Family",
			"text_l1": "الترفيه والأسرة",
			"text_l2": "景观",
			"text_l3": "Отдых и семья",
			"amenities": [
				{
					"text": "Kids Play Area",
					"text_l1": "منطقة لعب للأطفال",
					"text_l2": "儿童娱乐区",
					"text_l3": "Детская игровая площадка",
					"value": "",
					"rank": 3,
					"slug": "kids-play-area",
					"format": "checkbox",
					"externalID": 34
				}
			]
		}
	],
	"completionDetails": {
		"startDate": null,
		"completionDate": 1843243200,
		"completionPercentage": null
	},
	"contactMethodAvailability": {
		"whatsapp": false,
		"sms": false,
		"email": false,
		"call": false
	},
	"title": "Hayat 3",
	"title_l1": "حياة 3",
	"title_l2": "Hayat 3",
	"title_l3": "Hayat 3",
	"units": [
		{
			"id": 1213118,
			"externalID": "25202",
			"active": true,
			"name": "Type 1 - Edge Unit",
			"name_l1": "Type 1 - Edge Unit",
			"name_l2": "Type 1 - Edge Unit",
			"name_l3": "Type 1 - Edge Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 3,
			"baths": 0,
			"areaMin": 314.38388736,
			"areaMax": null,
			"priceMin": null,
			"priceMax": null,
			"photos": [
				{
					"id": 824714240,
					"externalID": "d6e6c28ebca94b0d114de8ce2006f8f4f31daee3",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 1,
			"floorPlan3dURL": null
		},
		{
			"id": 1661178,
			"externalID": "33193",
			"active": true,
			"name": "Type 2 - Middle Unit",
			"name_l1": "Type 2 - Middle Unit",
			"name_l2": "Type 2 - Middle Unit",
			"name_l3": "Type 2 - Middle Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 3,
			"baths": 0,
			"areaMin": 298.86907968,
			"areaMax": null,
			"priceMin": 3400000,
			"priceMax": null,
			"photos": [
				{
					"id": 824714244,
					"externalID": "39d0e64c88bd7920d84cd11b19b4d04959e872df",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 2,
			"floorPlan3dURL": null
		},
		{
			"id": 1661177,
			"externalID": "33194",
			"active": true,
			"name": "Type 1 - Middle Unit",
			"name_l1": "Type 1 - Middle Unit",
			"name_l2": "Type 1 - Middle Unit",
			"name_l3": "Type 1 - Middle Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 4,
			"baths": 0,
			"areaMin": 353.12445504000004,
			"areaMax": null,
			"priceMin": null,
			"priceMax": null,
			"photos": [
				{
					"id": 824714242,
					"externalID": "2ac5264244024d59435fd38a98d15abda42c45b8",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 3,
			"floorPlan3dURL": null
		},
		{
			"id": 1661296,
			"externalID": "33195",
			"active": true,
			"name": "Type 2 - Edge Unit",
			"name_l1": "Type 2 - Edge Unit",
			"name_l2": "Type 2 - Edge Unit",
			"name_l3": "Type 2 - Edge Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 4,
			"baths": 0,
			"areaMin": 383.87536128000005,
			"areaMax": null,
			"priceMin": null,
			"priceMax": null,
			"photos": [
				{
					"id": 824714243,
					"externalID": "415029eab53d73adfbc971f6f736624e77816cbb",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 4,
			"floorPlan3dURL": null
		},
		{
			"id": 1661294,
			"externalID": "33196",
			"active": true,
			"name": "Type 1 - Edge Unit",
			"name_l1": "Type 1 - Edge Unit",
			"name_l2": "Type 1 - Edge Unit",
			"name_l3": "Type 1 - Edge Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 5,
			"baths": 0,
			"areaMin": 460.14875712,
			"areaMax": null,
			"priceMin": null,
			"priceMax": null,
			"photos": [
				{
					"id": 824714241,
					"externalID": "d392cdafcee5b89b286a790ca5caba91535d7dfc",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 5,
			"floorPlan3dURL": null
		},
		{
			"id": 1661298,
			"externalID": "33197",
			"active": true,
			"name": "Type 2 - Middle Unit",
			"name_l1": "Type 2 - Middle Unit",
			"name_l2": "Type 2 - Middle Unit",
			"name_l3": "Type 2 - Middle Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 5,
			"baths": 0,
			"areaMin": 357.76960704000004,
			"areaMax": null,
			"priceMin": null,
			"priceMax": null,
			"photos": [
				{
					"id": 824714245,
					"externalID": "59ad92f84011c55acc68edb5b31edb5d06542d60",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 6,
			"floorPlan3dURL": null
		},
		{
			"id": 1661299,
			"externalID": "33200",
			"active": true,
			"name": "Type 3 - Edge Unit",
			"name_l1": "Type 3 - Edge Unit",
			"name_l2": "Type 3 - Edge Unit",
			"name_l3": "Type 3 - Edge Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 5,
			"baths": 0,
			"areaMin": 460.14875712,
			"areaMax": null,
			"priceMin": null,
			"priceMax": null,
			"photos": [
				{
					"id": 824714246,
					"externalID": "8041beb1093e3ed312253afb82bd3b8d88570b52",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 7,
			"floorPlan3dURL": null
		},
		{
			"id": 1661300,
			"externalID": "33201",
			"active": true,
			"name": "Type 4 - Edge Unit",
			"name_l1": "Type 4 - Edge Unit",
			"name_l2": "Type 4 - Edge Unit",
			"name_l3": "Type 4 - Edge Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 5,
			"baths": 0,
			"areaMin": 456.61844160000004,
			"areaMax": null,
			"priceMin": null,
			"priceMax": null,
			"photos": [
				{
					"id": 824714247,
					"externalID": "56dc82042b6cb79ca8b2244233488309eac12481",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 8,
			"floorPlan3dURL": null
		},
		{
			"id": 1661301,
			"externalID": "33202",
			"active": true,
			"name": "Type 5 - Edge Unit",
			"name_l1": "Type 5 - Edge Unit",
			"name_l2": "Type 5 - Edge Unit",
			"name_l3": "Type 5 - Edge Unit",
			"category": [
				{
					"id": 1,
					"level": 0,
					"externalID": "1",
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
					"id": 8,
					"level": 1,
					"externalID": "16",
					"name": "Townhouses",
					"name_l1": "تاون هاوس",
					"name_l2": "联排别墅",
					"name_l3": "Таунхаусы",
					"slug": "townhouses",
					"slug_l1": "townhouses",
					"slug_l2": "townhouses",
					"slug_l3": "townhouses",
					"nameSingular": "Townhouse",
					"nameSingular_l1": "تاون هاوس",
					"nameSingular_l2": "联排别墅",
					"nameSingular_l3": "Таунхаус"
				}
			],
			"rooms": 5,
			"baths": 0,
			"areaMin": 423.26625024000003,
			"areaMax": null,
			"priceMin": null,
			"priceMax": null,
			"photos": [
				{
					"id": 824714248,
					"externalID": "65daf22a7f8346c6df3716a737f7dd893361fa6a",
					"title": null,
					"orderIndex": 1,
					"type": "floor_plan"
				}
			],
			"order": 9,
			"floorPlan3dURL": null
		}
	],
	"completionStatus": "under-construction",
	"unitCategories": [
		[
			{
				"id": 1,
				"level": 0,
				"externalID": "1",
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
				"id": 8,
				"level": 1,
				"externalID": "16",
				"name": "Townhouses",
				"name_l1": "تاون هاوس",
				"name_l2": "联排别墅",
				"name_l3": "Таунхаусы",
				"slug": "townhouses",
				"slug_l1": "townhouses",
				"slug_l2": "townhouses",
				"slug_l3": "townhouses",
				"nameSingular": "Townhouse",
				"nameSingular_l1": "تاون هاوس",
				"nameSingular_l2": "联排别墅",
				"nameSingular_l3": "Таунхаус"
			}
		]
	],
	"unitRooms": [
		3,
		3,
		4,
		4,
		5,
		5,
		5,
		5,
		5
	],
	"unitBaths": [
		0,
		0,
		0,
		0,
		0,
		0,
		0,
		0,
		0
	],
	"hasPropertyAds": true,
	"propertyAdCount": 6,
	"locationCompletionStatus": "off-plan",
	"isProjectOwned": false,
	"documents": [
		{
			"title": {
				"en": null,
				"ar": null,
				"zh": null,
				"ru": null
			},
			"fileSource": "https://bayut-production.s3.eu-central-1.amazonaws.com/file/1572620/a4406cc274cc48baadc461c0bcf5461e.pdf",
			"isActive": true,
			"tag": "project_brochure"
		}
	],
	"tierSlot": 0,
	"additionalCategories": [
		[
			{
				"id": 1,
				"level": 0,
				"externalID": "1",
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
				"id": 5,
				"level": 1,
				"externalID": "3",
				"name": "Villas",
				"name_l1": "فلل",
				"name_l2": "别墅",
				"name_l3": "Виллы",
				"slug": "villas",
				"slug_l1": "villas",
				"slug_l2": "villas",
				"slug_l3": "villas",
				"nameSingular": "Villa",
				"nameSingular_l1": "فیلا",
				"nameSingular_l2": "别墅",
				"nameSingular_l3": "Вилла"
			}
		],
		[
			{
				"id": 1,
				"level": 0,
				"externalID": "1",
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
				"id": 8,
				"level": 1,
				"externalID": "16",
				"name": "Townhouses",
				"name_l1": "تاون هاوس",
				"name_l2": "联排别墅",
				"name_l3": "Таунхаусы",
				"slug": "townhouses",
				"slug_l1": "townhouses",
				"slug_l2": "townhouses",
				"slug_l3": "townhouses",
				"nameSingular": "Townhouse",
				"nameSingular_l1": "تاون هاوس",
				"nameSingular_l2": "联排别墅",
				"nameSingular_l3": "Таунхаус"
			}
		]
	]
}
```

> **Pro Tip:** You can download the resulting dataset in **JSON, CSV, Excel, or XML** formats directly from the Apify platform for easy integration into your CRM or internal property management system.

---