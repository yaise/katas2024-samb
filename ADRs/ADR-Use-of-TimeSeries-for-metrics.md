# ADR foundation

## Status
Accepted

## Context
We need to collect metrics when key application events occur within the software system so that we can provide analytical and reporting capabilities.

## Decision
We will use a time series database to capture these metrics. 
The reason to use a time series database (as opposed to additional tables in the primary relational database) is 'cos
 -  segregate the read/write metrics patterns from regular application transactions. 
 -  leverage the efficient storage, aggregation and compaction mechanisms meant for time series data.  
 
Additionally, we chose to store all the necessary pieces of information in the metrics themselves. If our metrics only had ids, we'd have to build another layer to dereference the ids in reports and dashboards. The de-referencing would also see the latest data and not the time the metric was generated.

## Consequences
The options for which Time series db to use will depend on what is easier to operate on AWS. AWS TimeStream is a fully managed service but isn't based on open source technology like RDS with Postgres. Influx, TimeScaleDB, Druid are all viable options but need to be either deployed and managed; or consumed via vendor managed service at a premium cost.