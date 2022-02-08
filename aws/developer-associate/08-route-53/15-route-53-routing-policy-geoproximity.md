# Route 53 - Routing Policies - Geoproximity

- Route traffic to your resources based on geographic location of users and resources
- Ability to shify more traffic to resources based on the defined bias
- To change the size of the geografic region, specify bias values:
    - To expand (1 to 99) - more traffic to the resource
    - To shrink (-1 to -99) - less traffic to resource

- Resources can be:
    - AWS resources (specify AWS region)
    - Non-AWS resources (specify Latitude and Longtitude)
- You must use Route 53 Traffic Flow (advanced) to use this feature


