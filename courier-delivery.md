---
description: >-
  Here it is described the workflow to get the postcode in case when the
  shipment must be delivered by courier to your home.
---

# Courier delivery

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
