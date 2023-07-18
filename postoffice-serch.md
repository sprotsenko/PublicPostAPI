# PostOffice Serch

1. **Postcode search for the post office delivery**

Let’s consider the case when the shipment must be delivered to one of the post offices in Brovary city\*.

* Since 2020, the city of Brovary is the administrative centre of Brovary district. However, according to the KOATUU classifier, Brovary is a city of regional subordination.

Post office search shall be performed as follows:

Region -> District -> City -> Post office

**Note.** _The region and district are mandatory, because the name of the locality may coincide with another locality of the neighboring district or region, or even within the same district (please see the example in Annex 1)._

The list of all post offices in the locality can be obtained in three ways:

* by the locality (city) ID (CITY\_ID)
* by the KOATUU (Classification of Objects of the Administrative-Territorial System of Ukraine) code (CITY\_KOATUU)
* or by the KATOTTG (Codifier of Administrative-Territorial units and Territories of Territorial Communities) code (CITY\_KATOTTG)

### **Step 1. Region search** <a href="#step-1-region-search" id="step-1-region-search"></a>

Let’s find information about the region (oblast).

For the URI address classifier (please see the Address Classifier documentation):

https://www.ukrposhta.ua/address-classifier-ws/

**Searching a region by its name**



{% swagger method="get" path="" baseUrl="/get_regions_by_region_ua?region_name=Київська" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
'''

{ "Entries":{ "Entry":\[ { "REGION\_ID": "270", "REGION\_UA": "Київська", "REGION\_EN": "Kyivska", "REGION\_KATOTTG": "32000000000030281", "REGION\_KOATUU": "3200000000", "REGION\_RU": null } ] } }

''''
{% endswagger-response %}
{% endswagger %}

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

The response will provide us with the Region ID REGION\_ID.

With the next request we will get information about the district.

### **Step 2. District search** <a href="#step-2-district-search" id="step-2-district-search"></a>

Let’s find information about the district (rayon).

**Searching district by region ID and the district name**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

The response will provide us with the District ID DISTRICT\_ID.

With the next request we will get information about the locality.

### **Step 3. Locality search** <a href="#step-3-locality-search" id="step-3-locality-search"></a>

Let’s find information about the locality (city).

**Searching locality by district ID and the locality name**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

The response will provide us with the Locality ID CITY\_ID, CITY\_KOATUU or CITY\_KATOTTG.

With the next request we will get information about the post office.

### **Step 4. Post office search** <a href="#step-4-post-office-search" id="step-4-post-office-search"></a>

Let’s find information about the post office in the locality (city).

**Searching post offices by city ID**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

In response for each of the post offices we will receive the field POSTCODE– zip code, which must be specified during the address creation.

**Searching post offices by locality KOATUU code**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

In response for each of the post offices we will receive the field POSTCODE – zip code, which must be specified during the address creation.

Thus, the name of the city gives an opportunity to choose the nearest post office for a shipment delivery.

**Note.** In case of delivery with a mobile post office, the postcode search is made according to the procedure identical to the one used for the stationary post office.

\*\*Please note that the list of post offices may include post offices that are temporarily closed or closed-type post offices (operating within a closed institution, such as the Ministry of Foreign Affairs).\*\*Temporarily closed post offices can be filtered using the LOCK\_CODE field. All active records (open post offices) have LOCK\_CODE = 0.Closed-type post offices do not provide delivery to an address (..2D), but they can perform warehouse delivery (..2W) if the recipient is an employee of that closed institution or an employee of Ukrposhta at that post offices. Closed-type post offices can be filtered using the IS\_SECURITY field, where IS\_SECURITY = 1 for closed-type post offices and IS\_SECURITY = 0 for regular post offices.Searching for post offices using the KATOTTG code is done similarly to the KOATUU code, and the city\_katottg parameter should be specified.

**Searching post offices by locality KATOTTG code**

| **GET** Request                                                           |
| ------------------------------------------------------------------------- |
|                                                                           |
| Response                                                                  |
| ----------------------------Перелік відділень---------------------------- |

The next section contains an example of searching a zip code for courier delivery.

1. **Postcode search for courier delivery**

If the full address of the recipient is known and you need to create a shipment of W2D or D2D type, you should find the postcode of the delivery zone, which serves this address (postcode field in the address creation request).

For example, let’s search for the following address: 251 Kyivska str., Brovary, Kyiv region.

The search shall be conducted in the following order:

Region -> District -> City -> Street -> House

**Note.** _Indication of region and district is mandatory, because the name of the locality may coincide with another locality of the neighboring district or region, or even within the same district (please see the example in Annex 1)._

### **Step 1. Region search** <a href="#step-1-region-search-0" id="step-1-region-search-0"></a>

Let’s find information about the region (oblast).

**Searching a region by its name**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

The response will provide us with the Region ID REGION\_ID.

With the next request we will get information about the district.

### **Step 2. District search** <a href="#step-2-district-search-0" id="step-2-district-search-0"></a>

Let’s find information about the district (rayon).

**Searching district by region ID and the district name**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

The response will provide us with the District ID DISTRICT\_ID.

With the next request we will get information about the locality.

### **Step 3. Locality search** <a href="#step-3-locality-search-0" id="step-3-locality-search-0"></a>

Let’s find information about the locality (city).

**Searching locality by district ID and the locality name**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

The response will provide us with the Locality ID CITY\_ID.

With the next request we will get information about the street.

### **Step 4. Street search** <a href="#step-4-street-search" id="step-4-street-search"></a>

Let’s find information about the street.

**Searching street by locality ID and the street name**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

The response will provide us with the Street ID STREET\_ID.

With the next request we will get information about the house and postcode.

### **Step 5. House search** <a href="#step-5-house-search" id="step-5-house-search"></a>

Let’s find information about the house and the zip code which serves the house.

**Searching house by street ID and the house number**

| **GET** Request |
| --------------- |
|                 |
| Response        |
| {               |

The response will provide us the POSTCODE.

Thus, the house at the address 251 Kyivska str., Brovary, Kyiv region is served by the **postcode** **07405.**

**This postcode must be specified in the postcode field when creating the recipient's address.**
