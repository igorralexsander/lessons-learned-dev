# Cache strategies

Bringing together the knowledge obtained in the last experiences with the use of cache, below I will document some of the strategies learned.

## Sumary

1. Random TTL
2. Remove default and empty values from JSON
3. Avoid use of redis keys

### 1. Random TTL

In case of multiple entities needs to be retrieved from cache engine in same time, we can set random seconds or milliseconds in TTL of each entity, with that, each entity will expire at different times  preventing individual request from having to fetch all the entities from database.

### 2. Remove default and empty values from JSON

When size of final JSON is a problem, just config JSON parser to not write default values like:

```text
    Boolean = false
    Object = null
    Numeric = 0 or null
    String = "" or null
```

### 3. Avoid use of redis keys

When we use `.keys("*")` in redis we are causing lock it. To prevent this we use a strategy where first off all we save all keys in list, after this we create another key and in its value we insert a list of keys generated and when we needs search some keys,
we just retrieve the key which contains a list of other keys and perform a filter in result list.
