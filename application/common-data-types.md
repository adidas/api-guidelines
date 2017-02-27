# Common Data Types

## Date and Time Format
Date and Time **MUST** always conform to the [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) format e.g. `2017-06-21T14:07:17Z` (date time) or `2017-06-21` (date), it **MUST** use the UTC (without time offsets).

## Duration Format
Duration format **MUST** conform to the [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) standard. 

#### Example
`P3Y6M4DT12H30M5S` represents a duration of "three years, six months, four days, twelve hours, thirty minutes, and five seconds".

## Time Interval Format
Time Interval format **MUST** conform to the [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) standard. 

## Standard Time Stamps
Where applicable, a resource representation **SHOULD** contain the standard timestamps:

- `created_at`
- `updated_at`
- `finished_at`

#### Example

```json
{
...
"created_at": "2017-01-01T12:00:00Z",
"updated_at": "2017-01-01T13:00:00Z",
...
}
```



## Language format

## Country format

## Currency format

