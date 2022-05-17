# DynamoDB - Basic APIs

## Writing data

- PutItem
    - Creates a new item of fully replace an old item (same primary key)
    - Consumes WCU
- UpdateItem
    - Edits an existing item's attributes or adds a new item if it doesnt exist
    - Can be used to implement Atomic Counters - a numeric attribute that's unconditionally incremented
- Conditional Writes
    - Accept a write/update/delete only of conditions are met, otherwise returns an error
    - Helps with concurrent access to items
    - No performance impact

## Reading data

- GetItem
    - Read based on Primary Key
    - Primary Key can be HASH or HASH+Range
    - Eventually Consistent Read (default)
    - Option to use Strongly Consistent Reads (more RCU - might take longer)
    - ProjectionExpression can be specified to retrieve only certain attributes
- Query
    - returns items based on:
        - KeyConditionExpression
            - Partition Key value (must be = operator) - required
            - Sort key value (=, <, <=, >, >=, between, begins with) - optional
        - FilterExpression
            - Additional filtering after the query operation (before data is returned to you)
            - Use only with non-key attributes (does not allow HAS or RANGE attributes)
    - returns
        - The number of items specified in Limit
        - Or up to 1 MB of data
    - Ability to do pagination on the results
    - Can query table, a Local Secondary Index, or a Global Secondary Index
- Scan
    - scan the entire table and then filter out data (inefficient)
    - Returns up to 1MB of data - use pagination to keep on reading
    - Consumes a lot of RCU
    - Limit impact using Limit or reduce the size of the result and pause
    - For faster performance, use Parallel Scan
        - Multiple workers scan multiple data segments at the same time
        - Increases the thoughput and RCU consumed
        - Limit the impact of parallel scans just like you would for scans
    - Can use ProjectionExpression & FilterExpression (no changes to RCU)

## Deleting data

- DeleteItem
    - Delete an individual item
    - Ability to perform a conditional delete
- DeleteTable
    - Delete a whole table and all it's items
    - Much quicker deletion than calling DeleteItem on all items

## Batch Operations

- Allows you to save in latency by reducing the number of API calls
- Operations are done in parallel for better efficiency
- Part of a batch can fail, in which case we need to try again for the failed items

- BatchWriteItem
    - Up to 25 PutItem and/or DeleteItem in one call
    - Up to 16MB of data written, up to 400KB of data per item
    - Can't update items (use UpdateItem)
- BatchGetItem
    - Return items from one or more tables
    - Up to 100 items, up to 16MB of data
    - Items are retrieved in parallel to minimize latency

