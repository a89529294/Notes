## __Fundamentals of Billing__

### Compute
### Storage
### Outbound Data

## __Cloud Billing Models__

### On Demand
### Savings Plan

Similar to _Reservation_. See [[Pricing Models for EC2]]
### Spot

Pay for excess capacity, but this is not guaranteed
### Reservation

Similar to _Savings Plan_. See [[Pricing Models for EC2]]

## __AWS Lambda Pricing__

`(nr * cr) + (nr * cgs * m * s)`
- `nr` number of requests
- `cr` cost per request
- `cgs` cost per GB per second
- `m` memory allocated (from 128mb to 10,240mb), remember to adjust it to gb for calc
- `s` seconds that each function takes

`nr * cr` is the _request pricing_
`nr * cgs * m * s` is the _duration pricing_

One thing to note is, _ephemeral storage_, which is the storage for the function itself can cost money if you allocate more than the default 512mb.

## __Tools for Billing__

### Billing and Cost Management

Overview, simplified
### Cost Explorer (Under Billing and Cost Management)

Visual, detailed
### Data Exports (Under Billing and Cost Management)

CSV format, extremely detailed
### Budgets (Under Billing and Cost Management)

Setting up alerts when spending exceeds target



