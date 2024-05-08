# adidas Asynchronous API guidelines

## Asynchronous API guidelines

### Common data types

The API types **MUST** adhere to the formats defined below:

| Data type | Standard | Example |
| --------- | -------- | ------- |  
| Date and Time | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | 2017-06-21T14:07:17Z (Always use UTC) |
| Date | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | 2017-06-21 |
| Duration | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | P3Y6M4DT12H30M5S |
| Time interval | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | 2007-03-01T13:00:00Z/2008-05-11T15:30:00Z |
| Timestamps | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | 2017-01-01T12:00:00Z |
| Language Codes | [ISO 639](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) | en <-> English |
| Country Code | [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) | DE <-> Germany |
| Currency | [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) | EUR <-> Euro |