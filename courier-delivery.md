---
description: >-
  Here it is described the workflow to get the postcode in case when the
  shipment must be delivered by courier to your home.
---

# Courier delivery

If the full address of the recipient is known and you need to create a shipment of W2D or D2D type, you should find the postcode of the delivery zone, which serves this address (postcode field in the address creation request).

For example, let’s search for the following address: 251 Kyivska str., Brovary, Kyiv region.

The search shall be conducted in the following order:

Region -> District -> City -> Street -> House

{% hint style="info" %}
**Note.** _Indication of region and district is mandatory, because the name of the locality may coincide with another locality of the neighboring district or region, or even within the same district (please see the example in Annex 1)._
{% endhint %}

### **Step 1. Region Search** <a href="#step-1-region-search-0" id="step-1-region-search-0"></a>

Let’s find information about the region (oblast).

**Searching a region by its name**

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_regions_by_region_ua" method="get" expanded="true" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

The response will provide us with the Region ID REGION\_ID.

With the next request, we will get information about the district.

### **Step 2. District Search** <a href="#step-2-district-search-0" id="step-2-district-search-0"></a>

Let’s find information about the district (rayon).

**Searching district by region ID and the district name**

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_districts_by_region_id_and_district_ua" method="get" expanded="true" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

The response will provide us with the District ID DISTRICT\_ID.

With the next request, we will get information about the locality.

### **Step 3. Locality search** <a href="#step-3-locality-search-0" id="step-3-locality-search-0"></a>

Let’s find information about the locality (city).

**Searching locality by district ID and the locality name**

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_city_by_region_id_and_district_id_and_city_ua" method="get" expanded="true" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

The response will provide us with the Locality ID CITY\_ID.

With the next request, we will get information about the street.

### **Step 4. Street search** <a href="#step-4-street-search" id="step-4-street-search"></a>

Let’s find information about the street.

**Searching street by locality ID and the street name**

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_street_by_region_id_and_district_id_and_city_id_and_street_ua" method="get" expanded="true" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

The response will provide us with the Street ID STREET\_ID.

With the next request, we will get information about the house and postcode.

### **Step 5. House search** <a href="#step-5-house-search" id="step-5-house-search"></a>

Let’s find information about the house and the zip code which serves the house.

**Searching houses by street ID and the house number**

{% swagger src=".gitbook/assets/openapiSearchAddress.yaml" path="/get_addr_house_by_street_id" method="get" expanded="true" %}
[openapiSearchAddress.yaml](.gitbook/assets/openapiSearchAddress.yaml)
{% endswagger %}

The response will provide us with the POSTCODE.

Thus, the house at the address 251 Kyivska str., Brovary, Kyiv region is served by the **postcode** **07405.**

**This postcode must be specified in the postcode field when creating the recipient's address.**
