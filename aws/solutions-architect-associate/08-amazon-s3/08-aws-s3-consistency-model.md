# AWS S3 - Consistency model

- Read after write consistency for PUTS of new objects
    - As soon as an object is written, we can retrieve it (PUT 200 -> GET 200)
    - This is true, except if we did a GET before to see if the object existed (GET 404 -> PUT 200 -> GET 404) - eventually consistent
- Eventual Consistency for DELETES and PUTS of existing objects
    - If we read an object after updating, we might get the older version
    - If we delete an object, we might still be able to retrieve it for a short time