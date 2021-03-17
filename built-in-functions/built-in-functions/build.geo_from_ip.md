# build.geo\_from\_ip

### Function Description

`build.geo_from_ip` is one of build.security built in function that returns a detailed geolocation object for the given `ip_address` using the [Maxmind](https://dev.maxmind.com/geoip/geoip2/geolite2/) GeoLite2 Database.

### Function format

`build.geo_from_ip(ip)`

**Parameters:**  
- `ip` - The IP Address that we want to query geolocation attributes.

### Function Usage Example

```text
geo := build.geo_from_ip("27.7.199.7")
geo.Subdivisions[_].IsoCode == user_ctx.subdivisions[_]
```



The function we use returns the data to an object named `geo` that will contain:JSON

```text
{
  "City": {
    "Names": {
    "de": "Delhi",
    "en": "Delhi",
    "es": "Delhi",
    "fr": "Delhi",
    "ja": "デリー",
    "pt-BR": "Deli",
    "ru": "Дели",
    "zh-CN": "德里"
    }
  },
  "Continent": {
    "Code": "AS",
    "Names": {
    "de": "Asien",
    "en": "Asia",
    "es": "Asia",
    "fr": "Asie",
    "ja": "アジア",
    "pt-BR": "Ásia",
    "ru": "Азия",
    "zh-CN": "亚洲"
    }
  },
  "Country": {
    "IsInEuropeanUnion": false,
    "IsoCode": "IN",
    "Names": {
    "de": "Indien",
    "en": "India",
    "es": "India",
    "fr": "Inde",
    "ja": "インド",
    "pt-BR": "Índia",
    "ru": "Индия",
    "zh-CN": "印度"
    }
  },
  "Location": {
    "AccuracyRadius": 1,
    "Latitude": 28.6858,
    "Longitude": 77.231,
    "MetroCode": 0,
    "TimeZone": "Asia/Kolkata"
  },
  "Postal": {
    "Code": "110054"
  },
  "RegisteredCountry": {
    "IsInEuropeanUnion": false,
    "IsoCode": "IN",
    "Names": {
    "de": "Indien",
    "en": "India",
    "es": "India",
    "fr": "Inde",
    "ja": "インド",
    "pt-BR": "Índia",
    "ru": "Индия",
    "zh-CN": "印度"
    }
  },
  "RepresentedCountry": {
    "GeoNameID": 0,
    "IsInEuropeanUnion": false,
    "IsoCode": "",
    "Names": null,
    "Type": ""
  },
  "Subdivisions": [
    {
    "IsoCode": "DL",
    "Names": {
        "de": "Delhi",
        "en": "National Capital Territory of Delhi",
        "fr": "Delhi"
    }
    }
  ],
  "Traits": {
    "IsAnonymousProxy": false,
    "IsSatelliteProvider": false
  }
}
```

### Rules using `build.geo_from_ip` examples

Using `build.geo_from_ip` return JSON object \(`geo.attribute`\) will allow you to build rules based on geolocation environmental attributes such as:

* `geo.city.Names` and `go.Country.Names`- Allows comparison made on a city or country basis, thereby restricting access of employees in international organizations to data that is not related to their base country /branch.
* `geo.IsInEuropeanUnion` - by using this attribute you can know if the request source or address is within a European country and create GDPR authorization rules.
* `geo.Traits.IsAnonymousProxy` can assist you in building rules that deny requests from anonymous proxies that are marked as a suspicious source.

