# Route 53 - Records TTL (Time to Live)

The DNS clients will cache the result for the dns record, the TTL states for how long will it be cached.

- High TTL - e.g. 24 hours
    - less traffic on route 53
    - possibly outdated records
- Low TTL - e.g. 60 seconds
    - more traffic on route 53 ($$)
    - Records are outdated for less time
    - Easy to change records

Except for alias records, TTL is mandatory for each DNS record.

