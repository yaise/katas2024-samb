# ADR foundation

## Status
Accepted

## Context
We must choose a way to store, report and alert on observability signals(logs, traces, metrics) from our services and infrastructure.

## Decision
We will use the Elastic stack for storing and reporting on Observability signals.
Elastic has pretty robust support for log ingestion, searching and indexing capabilities. 
Elastic is compatible with open telemetry. 
Elastic stack can be run on-prem or the cloud. 

## Consequences
Elastic stack will need to either be deployed on prem or the managed cloud service. Factors like cost, operational overhead, availability, support will need to be considered for choosing on prem vs cloud.
Additional configuration like setting alerts, integrating with PagerDuty and setting up of common dashboard will be required for it to be of real use.