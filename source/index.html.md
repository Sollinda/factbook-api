---
title: Sollinda API Documentation

language_tabs:
---

# Introduction

Welcome to Sollinda's API documentation.

If you have any questions regarding this API, please send an email to <a href="mailto:support@sollinda.com">support@sollinda.com</a> and we'll get back to you as soon as we can.

### Base URL

`http://api.sollinda.com/v1`

# Country Profiles

Access profiles of countries, dependent territories, and special areas of geographical interest from The World Factbook as JSON documents, originally published by the Central Intelligence Agency (CIA) in the public domain. For more information on The World Factbook, and the type of data that it offers, please refer directly to [CIA's website](https://www.cia.gov/library/publications/the-world-factbook/), or [this Wikipedia article](http://en.wikipedia.org/wiki/The_World_Factbook).

Profiles are accessed one-by-one by the country's name, two or three-letter abbreviation, numerical identifier, or top-level domain.

### Base URL

`http://api.sollinda.com/v1/country-profiles`


<aside class="notice">This API has been generated and is kept up-to-date using <a href="https://github.com/opendatajson/factbook.json">opendatajson/factbook.json</a>. Many thanks to all contributors of factbook.json for making this API possible.</aside>

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

A specific profile of a country, dependent territory, or special areas of geographical interest as provided by The World Factbook.

### HTTP Request Format

`GET http://api.sollinda.com/v1/country-profiles/<type>/<id>`

### Request Parameters

| Parameter |  |
| --------- | ------- |
| ```type``` | The [Country Identifier Type](#country_identifier_type) used to identify the country.
| ```id``` | The ID of a country for the given ```type``` parameter. The ID should always be lowercased even if the standard referenced in ```type``` uses another convention (e.g. `tw` instead of `TW` when querying for Taiwan).

<aside class="notice">Refer to the list of <a href="#country_identifier_type">Country Identifier Types</a> for a list of supported values for the <code>type</code> parameter.</aside>

### Country Identifier Types

Country profiles are identified either by using the country name or by using a commonly regognized standard such as the two-letter country code used in ISO 3611-1 alpha-2.

For a better understanding of how the standards listed below work, please refer to the links in the description fields. Alternatively, for an exhaustive list of countrie, territories, and associated identifiers, take a look at the [List of Countries](#list-of-countries) request.

| Type&nbsp;Parameter |   |
| --------------- | - |
| ```name``` | The lowercased and underscore-separated name of a country. <br>E.g. `taiwan` for Taiwan or `united_states` for USA.
| ```iso-alpha-2``` | [ISO 3611-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) codes are two-letter country codes as defined in ISO 3166-1. They are most prominently used for Internet's country-specific top-level domains, but also by banks (IBAN and SWIFT), United Nations, and others. <br>E.g. `tw` for Taiwan, `us` for USA, `au` for Australia. |
| ```iso-alpha-3``` | [ISO 3611-1 alpha-3](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3) codes are similar to alpha-2 but uses three letters instead of two.<br> E.g. `chn` for China and `sgp` for Singapore. |
| ```iso-numeric``` | [ISO 3611-1 numeric](https://en.wikipedia.org/wiki/ISO_3166-1_numeric) uses three-digit country codes.<br>E.g. `158` for Taiwan or `250` for France. |
| ```gec``` | [Geopolitical Entities and Codes (GEC)](https://www.cia.gov/library/publications/the-world-factbook/appendix/appendix-d.html) is used by The World Factbook as primary country identifier. Note that this standard differens from the more widely used ISO-3611-1 alpha-2.<br>E.g. `tw` for Taiwan, `au` for Austria.
| ```stanag``` | [STANAG 1059](https://www.cia.gov/library/publications/the-world-factbook/appendix/appendix-d.html) is a three-letter identifier  established and maintained by the NATO for the purpose of providing a common set of geo-spatial identifiers for countries and territories.<br>E.g. `twn` for Taiwan, `tha` for Thailand. |
| ```tld``` | [Top-level Domains](), e.g. `.se` for Sweden or `.tw` for Taiwan. |

<aside class="notice">CIA keeps an up-to-date list of country identifiers <a href="https://www.cia.gov/library/publications/the-world-factbook/appendix/appendix-d.html">here</a></aside>

## List of Country Profiles

```shell
# Request
curl -X GET http://api.sollinda.com/v1/country-profiles/list
```

```javascript
// JSON response
[
  {
    // ...
  }, {
    "name": "taiwan"
    "iso-alpha-2": "tw",
    "iso-alpha-3": "twn"
    "iso-numeric": "158",
    "gec": "twn",
    "nato": "twn",
    "tld": ".tw"
  }, {
    "name": "thailand",
    "iso-alpha-2": "tw",
    "iso-alpha-3": "twn"
    "iso-numeric": "158",
    "gec": "twn",
    "nato": "twn",
    "tld": ".tw"
  }, {
    // ...
  }
]
```

A list of all profiles provided by The World Factbook with associated Country Identifier Types.


### HTTP Request

`GET http://api.sollinda.com/v1/country-profiles/list`

