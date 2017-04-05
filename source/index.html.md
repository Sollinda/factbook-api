---
title: Sollinda API Documentation

language_tabs:
---

# Introduction

Welcome to Sollinda's API documentation.

If you have questions about this API, please send an <a href="mailto:support@sollinda.com">email to us</a> and we'll get back to you. For clarifications and language use, please submit a pull request to sollinda/docs on GitHub.


### Base URL

`http://api.sollinda.com/v1`

# Country Profiles

Access profiles of countries, dependent territories, and special areas of geographical interest. Profiles are accessed one-by-one by the country's name, two or three-letter abbreviation, a numerical identifier, or top-level domain.

The information is sourced from The World Factbook, published by the CIA in the public domain. To explore The World Factbook in its original form, please use [CIA's website](https://www.cia.gov/library/publications/the-world-factbook/). For more information, see [this Wikipedia article](http://en.wikipedia.org/wiki/The_World_Factbook).

### Base URL

`http://api.sollinda.com/v1/country-profiles`


<aside class="notice"><a href="https://github.com/opendatajson/factbook.json">opendatajson/factbook.json</a> is used to generate this API. Many thanks to the contributors of factbook.json for making this possible.</aside>

## Single Country Profile

```shell
# Using type "name"
TYPE=name
ID=taiwan

# Using type "iso-alpha-2"
TYPE=iso-alpha-2
ID=tw

# Using type "iso-alpha-3"
TYPE=iso-alpha-3
ID=twn

# Using type "tld"
TYPE=tld
ID=.tw

# Request
curl -X GET http://api.sollinda.com/v1/country-profiles/$TYPE/$ID
```
```javascript
// JSON response
{
  // ...
  "Geography": {
    "Location": {
      "text": "Eastern Asia, islands bordering the East China Sea, 
        Philippine Sea, South China Sea, and Taiwan Strait, 
        north of the Philippines, off the southeastern coast of China"
    },
    "Geographic coordinates": {
      "text": "23 30 N, 121 00 E"
    },
    "Map references": {
      "text": "Southeast Asia"
    },
    "Area": {
      "total": {
        "text": "35,980 sq km"
      },
      "land": {
        "text": "32,260 sq km"
      },
      "water": {
        "text": "3,720 sq km"
      },
      "note": {
        "text": "includes the Pescadores, Matsu, and Quemoy islands"
      }
    },
    "Area - comparative": {
      "text": "slightly smaller than Maryland and Delaware combined"
    },
    "Land boundaries": {
      "text": "0 km"
    }
    // ...
  }
}
```

The profile of a country, dependent territory, or special areas of geographical interest.

<a target="_blank" href="http://www.jsoneditoronline.org/?url=http%3A%2F%2Fapi.sollinda.com%2Fv1%2Fcountry-profiles%2Fname%2Ftaiwan" style="
  display: inline-block;
  background: #1B62B2;
  font-weight: bold;
  padding:8px 16px;
  text-decoration: none;
  color: white;  
  text-shadow: none;
  border-radius: 3px
">&#9654;&nbsp;&nbsp;&nbsp;Try it out</a>

### HTTP Request Format

`GET http://api.sollinda.com/v1/country-profiles/<type>/<id>`

### Request Parameters

| Parameter |  |
| --------- | ------- |
| ```type``` | The [Country Identifier Type](#country-identifier-types) used to identify the country.
| ```id``` | The ID of a country for the given ```type``` parameter. The ID should be lowercased even if the standard in ```type``` uses a different convention.

<aside class="notice">Refer to the list of <a href="#country-identifier-types">Country Identifier Types</a> for all supported values for the <code>type</code> parameter.</aside>

### Country Identifier Types

Country profiles are identified by using the country name or a regognized standard such as the two-letter country code used in ISO 3611-1 alpha-2.

For more information about the standards, refer to the links in the description fields. Or, for a list of all countries with identifiers, use the [List of Country Profiles](#list-of-country-profiles) endpoint.

| Type&nbsp;Parameter |   |
| --------------- | - |
| ```name``` | The lowercased and underscore-separated name of a country. <br>E.g. `taiwan` for Taiwan or `united_states` for USA.
| ```iso-alpha-2``` | [ISO 3611-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) codes are two-letter country codes as defined in ISO 3166-1. They are most prominently used for Internet's country-specific top-level domains, but also by banks (IBAN and SWIFT), United Nations, and others. <br>E.g. `tw` for Taiwan, `us` for USA, `au` for Australia. |
| ```iso-alpha-3``` | [ISO 3611-1 alpha-3](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3) codes are similar to alpha-2 but uses three letters instead of two.<br> E.g. `chn` for China and `sgp` for Singapore. |
| ```iso-numeric``` | [ISO 3611-1 numeric](https://en.wikipedia.org/wiki/ISO_3166-1_numeric) uses three-digit country codes.<br>E.g. `158` for Taiwan or `250` for France. |
| ```gec``` | [Geopolitical Entities and Codes (GEC)](https://www.cia.gov/library/publications/the-world-factbook/appendix/appendix-d.html) is used by The World Factbook as primary country identifier. Note that this standard differens from the more widely used ISO-3611-1 alpha-2.<br>E.g. `tw` for Taiwan, `au` for Austria.
| ```stanag``` | [STANAG 1059](https://www.cia.gov/library/publications/the-world-factbook/appendix/appendix-d.html) is a three-letter identifier  established and maintained by NATO for the purpose of providing a common set of geo-spatial identifiers for countries and territories.<br>E.g. `twn` for Taiwan, `tha` for Thailand. |
| ```tld``` | [Top-level Domains](https://en.wikipedia.org/wiki/List_of_Internet_top-level_domains#Country_code_top-level_domains), e.g. `.se` for Sweden or `.tw` for Taiwan. |


## List of Country Profiles

```shell
# Request
curl -X GET http://api.sollinda.com/v1/country-profiles/list
```
```javascript
// JSON response
[
  // ... 
  {
    "iso-numeric": "158",
    "iso-alpha-2": "tw",
    "iso-alpha-3": "twn",
    "gec": "tw",
    "name": "taiwan",
    "stanag": "twn",
    "tld": ".tw"
  }, {
    "iso-numeric": "762",
    "iso-alpha-2": "tj",
    "iso-alpha-3": "tjk",
    "gec": "ti",
    "name": "tajikistan",
    "stanag": "tjk",
    "tld": ".tj"
  }, {
    "iso-numeric": "834",
    "iso-alpha-2": "tz",
    "iso-alpha-3": "tza",
    "gec": "tz",
    "name": "tanzania",
    "stanag": "tza",
    "tld": ".tz"
  }
  // ...
]
```

A list of all profiles provided by The World Factbook with associated Country Identifier Types.

<a target="_blank" href="http://www.jsoneditoronline.org/?url=http%3A%2F%2Fapi.sollinda.com%2Fv1%2Fcountry-profiles%2Flist" style="
  display: inline-block;
  background: #1B62B2;
  font-weight: bold;
  padding:8px 16px;
  text-decoration: none;
  color: white;
  text-shadow: none;
  border-radius: 3px
">&#9654;&nbsp;&nbsp;&nbsp;Try it out</a>


### HTTP Request

`GET http://api.sollinda.com/v1/country-profiles/list`

