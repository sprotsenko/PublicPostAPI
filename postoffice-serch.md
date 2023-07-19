---
description: >-
  Here it is described the workflow to get the postcode in case when the
  shipment must be delivered to the postoffice.
---

# Postoffice delivery

Let’s consider the case when the shipment must be delivered to one of the post offices in Brovary city\*.

Since 2020, the city of Brovary is the administrative centre of the Brovary district. However, according to the KOATUU classifier, Brovary is a city of regional subordination.

Post office search shall be performed as follows:

Region -> District -> City -> Post office

**Note.** _The region and district are mandatory, because the name of the locality may coincide with another locality of the neighbouring district or region, or even within the same district (please see the example in Annex 1)._

The list of all post offices in the locality can be obtained in three ways:

* by the locality (city) ID (CITY\_ID)
* by the KOATUU (Classification of Objects of the Administrative-Territorial System of Ukraine) code (CITY\_KOATUU)
* or by the KATOTTG (Codifier of Administrative-Territorial units and Territories of Territorial Communities) code (CITY\_KATOTTG)

### **Step 1. Region Search** <a href="#step-1-region-search" id="step-1-region-search"></a>

Let’s find information about the region (oblast).

For the URI address classifier (please see the Address Classifier documentation):

https://www.ukrposhta.ua/address-classifier-ws/

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_regions_by_region_ua" method="get" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

The response will provide us with the Region ID REGION\_ID.

With the next request, we will get information about the district.

### **Step 2. District Search** <a href="#step-2-district-search" id="step-2-district-search"></a>

Let’s find information about the district (rayon).

**Searching district by region ID and the district name**

The response will provide us with the District ID DISTRICT\_ID.

With the next request, we will get information about the locality.

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_districts_by_region_id_and_district_ua" method="get" expanded="true" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

### **Step 3. Locality search** <a href="#step-3-locality-search" id="step-3-locality-search"></a>

Let’s find information about the locality (city).

**Searching locality by district ID and the locality name**

The response will provide us with the Locality ID CITY\_ID, CITY\_KOATUU or CITY\_KATOTTG.

With the next request, we will get information about the post office.

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_city_by_region_id_and_district_id_and_city_ua" method="get" expanded="true" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

### **Step 4. Post office search** <a href="#step-4-post-office-search" id="step-4-post-office-search"></a>

Let’s find information about the post office in the locality (city).

**Searching post offices by city ID**

In response for each of the post offices, we will receive the field POSTCODE– zip code, which must be specified during the address creation.

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_postoffices_by_postcode_cityid_cityvpzid" method="get" expanded="true" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

**Searching post offices by locality KOATUU code**

In response for each of the post offices, we will receive the field POSTCODE – zip code, which must be specified during the address creation.

Thus, the name of the city gives an opportunity to choose the nearest post office for shipment delivery.

**Note.** In the case of delivery with a mobile post office, the postcode search is made according to the procedure identical to the one used for the stationary post office.

\*\*Please note that the list of post offices may include post offices that are temporarily closed or closed-type post offices (operating within a closed institution, such as the Ministry of Foreign Affairs).\*\*Temporarily closed post offices can be filtered using the LOCK\_CODE field. All active records (open post offices) have LOCK\_CODE = 0. Closed-type post offices do not provide delivery to an address (..2D), but they can perform warehouse delivery (..2W) if the recipient is an employee of that closed institution or an employee of Ukrposhta at that post office. Closed-type post offices can be filtered using the IS\_SECURITY field, where IS\_SECURITY = 1 for closed-type post offices and IS\_SECURITY = 0 for regular post offices. Searching for post offices using the KATOTTG code is done similarly to the KOATUU code, and the city\_katottg parameter should be specified.

**Searching post offices by locality KATOTTG code**

The next section contains an example of searching a zip code for courier delivery.
