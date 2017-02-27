# Common Data Types

## Date and Time Format
Date and Time **MUST** always conform to the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format e.g.: `2017-06-21T14:07:17Z` (date time) or `2017-06-21` (date), it **MUST** use the UTC (without time offsets).

## Duration Format
Duration format **MUST** conform to the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standard e.g.: `P3Y6M4DT12H30M5S` (three years, six months, four days, twelve hours, thirty minutes, and five seconds).

## Time Interval Format
Time Interval format **MUST** conform to the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standard e.g.: `2007-03-01T13:00:00Z/2008-05-11T15:30:00Z`.

## Standard Time Stamps
Where applicable, a resource representation **SHOULD** contain the standard timestamps:

- `created_at`
- `updated_at`
- `finished_at`

#### Example

```json
{
    "created_at": "2017-01-01T12:00:00Z",
    "updated_at": "2017-01-01T13:00:00Z",
    
    ...
}
```

## Language Code Format
Language codes **MUST** conform to the [ISO 639](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) e.g.: `en` for English.

## Country Code Format
Country codes **MUST** conform to the [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) e.g.: `DE` for Germany.

## Currency Format
Currency codes **MUST** conform to the [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) e.g.: `EUR` for Euro.
