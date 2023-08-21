---
description: Enabling better SEO for local businesses, automatically, via the Duda API
---

# Local Business Schema

Schema.org helps robots & crawlers understand facts about a website, business, people, or the content on a web page. Duda has made it easy to enable LocalBusiness schema on your website by filling in the content library of a website you're building. Duda makes sure that you add enough data and the right kind of data to accurately reflect schema. This is important to make sure that the schema is valid with Google and other search engines that rely on schema. [We fully follow Google's LocalBusiness Schema recommendations outlined here.](https://developers.google.com/search/docs/data-types/local-business).

{% hint style="warning" %}
**Heads up: Single Location Support**

Today, we only pull data from the primary/first location in the content library and do not support multiple locations for schema implementation.
{% endhint %}

### Objectives and Outcomes

In this tutorial you will learn how to enable LocalBusiness schema on your website. You will do this by filling in the content library of a website you are building.

### 1. Enable Schema

Due to the requirements of schema, Duda makes you enable schema for each website you want to enable it on. We also do this because implementing schema incorrectly or with bad data can cause harm to your website by providing crawlers and search engines with inaccurate information about your business. This could lead to confusing search engines or people trying to contact the wrong business.

Local Business Schema can be enabled and disabled via the [Update Site API](../../reference/partner-api-reference/sites.md#update-site-1). To do so, you must provide a _true_ or _false_ value in the schemas block of your Site Object.

**Enabling Local Business Schema on an existing site:**

{% tabs %}
{% tab title="curl" %}
```bash
curl --request POST \
  --url https://api.duda.co/api/sites/multiscreen/update/site_name \
  --header 'Authorization: Basic 123abc=' \
  --header 'Content-Type: application/json' \
  --data '{"schemas":{"local_business":{"enabled": true}}}'
```
{% endtab %}
{% endtabs %}

**Disabling Local Business Schema on an existing site:**

{% tabs %}
{% tab title="curl" %}
```bash
curl --request POST \
  --url https://api.duda.co/api/sites/multiscreen/update/site_name \
  --header 'Authorization: Basic 123abc=' \
  --header 'Content-Type: application/json' \
  --data '{"schemas":{"local_business":{"enabled": false}}}'
```
{% endtab %}
{% endtabs %}

### 2. Check the Schema Status

The [Site Details](../../reference/partner-api-reference/sites.md#get-site-1) endpoint returns a [schemas object](../../reference/partner-api-reference/sites.md#schemas) that includes the Local Business Schema status as well as any missing fields. Check the status property to see if the information is valid, or if additional fields should be populated within the content library.

{% tabs %}
{% tab title="curl" %}
```bash
curl --request GET \
  --url https://api.duda.co/api/sites/multiscreen/site_name \
  --header 'Authorization: Basic 123abc='
```
{% endtab %}

{% tab title="JSON - Response" %}
```json
{
 ...
  "schemas": {
    "local_business": {
      "enabled": true,
      "status": "MISSING_REQUIRED_FIELDS",
      "missing_required_fields": [
        "Business Name",
        "Geo Coordinates",
        "Physical Address"
      ],
      "missing_recommended_fields": [
        "Phone Number",
        "Image"
      ]
    }
  },
...
}
```
{% endtab %}
{% endtabs %}

In this example, several required fields are missing - the Business Name, Geo Coordinates, and Physical address. In addition, a Phone Number and Image should be added to generate a more complete schema object. This information can be added using the Content APIs as described below. If all fields are complete and the enabled property is set to true, a JSON-LD schema object will automatically be created on the next publish.

### 3. Add or Update Local Business Information

Use the [Update Content API](../../reference/partner-api-reference/site-content.md#update-content-library-1) to add values for the Local Business Information fields. Make sure to [Publish](../../reference/partner-api-reference/site-content.md#publish-content-library-1) any changes you make before checking the status again to ensure all fields are filled.

### 4. Schema Validation

Before generating schema for websites, Duda verifies that we have the minimum required data to enable it. This is to prevent errors while implementing schema. You can see the required fields below. Information about which fields are required is also returned in the GET Site API call, so you know which fields are required and recommended.

We also recommend that once you add schema to a website, you verify that it works with the [Google Rich Results Test](https://search.google.com/test/rich-results). This verifies that Google can see the schema and leverage it to its greatest effect.

### 5. Data Fields

LocalBusiness schema represents the core pieces of data for a business with a physical location. Below is a list of the content library fields that Local Business Schema pulls from.

Data in the content library can be set with the [Content API](../../reference/partner-api-reference/site-content.md#content-library-object) or inside of the content library in the Duda editor.

{% hint style="warning" %}
**Heads up: Data accuracy**

Duda does not verify the data entered into the content library. For example, if you input an invalid address, Duda has no way to know this. Please ensure you insert accurate information into the content library.
{% endhint %}

| Content Library Field                 | Required | Description                                                                                                                                                                                                                                   |
| ------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Business Name (Not location name)** | Yes      | The name of the business as it is most commonly represented to customers.                                                                                                                                                                     |
| **Address**                           | Yes      | The physical address of the business. If there is no in-person store or location that can be visited, we recommend not enabling schema.                                                                                                       |
| **Geo**                               | Yes \*   | The LAT/LON that represents the businesses location. \* Duda will try to generate this automatically based on the address sent in the content library, but we might fail.                                                                     |
| **Social Networks**                   | No       | The social profiles of the business. In Schema, this is represented as 'sameAs' which means this is other URLs where this business can be found online.                                                                                       |
| **Business Hours**                    | No       | The hours that the business is open.                                                                                                                                                                                                          |
| **Image (under business images)**     | Yes      | <p>A group of images that represent the business. While this is not required for Schema, the Google validation tools require it. So, Duda makes this required as well.<br><br>Note: Image is the same as 'Business Images' in the editor.</p> |
| **Email**                             | No       | An email address to contact the business.                                                                                                                                                                                                     |
| **Phone**                             | No       | A phone number where the business can be contacted at.                                                                                                                                                                                        |
| **Logo**                              | No       | A logo that represents the business. While not required, we strongly recommend it.                                                                                                                                                            |
| **About us (under Business Text)**    | No       | A short description giving a short overview of the business.                                                                                                                                                                                  |

### 6. Republish Website

If you're enabling schema across any website, you'll need to republish the website to make sure the changes you've made are live and reflected on the web.

If you're republishing many sites via the API, please take note of [our API rate limits](../../reference/partner-api-reference/#rate-limits).

### 7. Business Types

Schema.org supports a range of different types of business that more closely align with what the actual business does. There are over 150 different types supported today. If you can't find any that aligns with the type of business the website is built for, you can leave the `type` field set to `null`, this will default to the generic `LocalBusiness` type.

Here is a list of all the supported schema business types:

* AnimalShelter
* ArchiveOrganization
* AutomotiveBusiness
  * AutoBodyShop
  * AutoDealer
  * AutoPartsStore
  * AutoRental
  * AutoRepair
  * AutoWash
  * GasStation
  * MotorcycleDealer
  * MotorcycleRepair
* ChildCare
* Dentist
* DryCleaningOrLaundry
* EmergencyService
  * FireStation
  * Hospital
  * PoliceStation
* EmploymentAgency
* EntertainmentBusiness
  * AdultEntertainment
  * AmusementPark
  * ArtGallery
  * Casino
  * ComedyClub
  * MovieTheater
  * NightClub
* FinancialService
  * AccountingService
  * AutomatedTeller
  * BankOrCreditUnion
  * InsuranceAgency
* FoodEstablishment
  * Bakery
  * BarOrPub
  * Brewery
  * CafeOrCoffeeShop
  * Distillery
  * FastFoodRestaurant
  * IceCreamShop
  * Restaurant
  * Winery
* GovernmentOffice
  * PostOffice
* HealthAndBeautyBusiness
  * BeautySalon
  * DaySpa
  * HairSalon
  * HealthClub
  * NailSalon
  * TattooParlor
* HomeAndConstructionBusiness
  * Electrician
  * GeneralContractor
  * HVACBusiness
  * HousePainter
  * Locksmith
  * MovingCompany
  * Plumber
  * RoofingContractor
* InternetCafe
* LegalService
  * Attorney
  * Notary
* Library
* LodgingBusiness
  * BedAndBreakfast
  * Campground
  * Hostel
  * Hotel
  * Motel
  * Resort
    * SkiResort
* MedicalBusiness
  * CommunityHealth
  * Dentist
  * Dermatology
  * DietNutrition
  * Emergency
  * Geriatric
  * Gynecologic
  * MedicalClinic
    * CovidTestingFacility
  * Midwifery
  * Nursing
  * Obstetric
  * Oncologic
  * Optician
  * Optometric
  * Otolaryngologic
  * Pediatric
  * Pharmacy
  * Physician
  * Physiotherapy
  * PlasticSurgery
  * Podiatric
  * PrimaryCare
  * Psychiatric
  * PublicHealth
* ProfessionalService
* RadioStation
* RealEstateAgent
* RecyclingCenter
* SelfStorage
* ShoppingCenter
* SportsActivityLocation
  * BowlingAlley
  * ExerciseGym
  * GolfCourse
  * HealthClub
  * PublicSwimmingPool
  * SkiResort
  * SportsClub
  * StadiumOrArena
  * TennisComplex
* Store
  * AutoPartsStore
  * BikeStore
  * BookStore
  * ClothingStore
  * ComputerStore
  * ConvenienceStore
  * DepartmentStore
  * ElectronicsStore
  * Florist
  * FurnitureStore
  * GardenStore
  * GroceryStore
  * HardwareStore
  * HobbyShop
  * HomeGoodsStore
  * JewelryStore
  * LiquorStore
  * MensClothingStore
  * MobilePhoneStore
  * MovieRentalStore
  * MusicStore
  * OfficeEquipmentStore
  * OutletStore
  * PawnShop
  * PetStore
  * ShoeStore
  * SportingGoodsStore
  * TireShop
  * ToyStore
  * WholesaleStore
* TelevisionStation
* TouristInformationCenter
* TravelAgency
