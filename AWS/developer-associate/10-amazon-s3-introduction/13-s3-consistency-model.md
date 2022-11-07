# Amazon S3 - Consistency Model

- Strong Consistency as of December 2020:
- After a:
    - Successful write of a new object (new PUT)
    - or an overwrite or delete of an existing object (overwrite PUT or DELETE)
- any:
    - subsequent read request immediately receives the latest version of the object (read after write consistency)
    - subsequent request immediately reflects changes (list consistency)
- Available at no additional costs, without any performance impact