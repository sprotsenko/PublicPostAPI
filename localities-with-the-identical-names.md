---
cover: .gitbook/assets/deokupovani-900х450.png
coverY: 0
---

# Localities with the identical names

Within one district there may exist several localities with the same name. For example, the village Lisove in Lviv region. Let’s get information about the locality by region ID (273 - Lviv region) and the locality name “Lisove”.

In the Lviv region, there are 5 localities with the name “Lisove”.&#x20;

Moreover, 3 of them are located in the Buskiy district, but all of them belong to different village councils (OWNOF field): Velyki Mosty, Brodivske and Busk. Each locality has a different CITY\_ID. This must be taken into account when searching for an address or post office.&#x20;

{% hint style="info" %}
Localities in the same district with the same name may differ in type. For example, the town of Bar and the village of Bar in the Bar district of Vinnytsia region. In this case, the type of locality must be taken into account (CITYTYPE\_UA).&#x20;
{% endhint %}

A similar situation may also refer to the streets. For example, the Dniprovskii entrance, passage, boulevard and lane in Kharkiv city. Consider the type of street (SHORTSTREETTYPE\_UA or STREETTYPE\_UA).
