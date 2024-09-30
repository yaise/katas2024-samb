# ADR foundation

## Status
Accepted

## Context
With the rise of cloud computing, microservices architectures, and increasingly complex business requirements, the need for software and infrastructure observability is greater than ever.
We must choose a way to collect and transport observability signals(logs, traces, metrics) from our services.

## Decision
We will use [Open Telemetry](https://opentelemetry.io/docs/what-is-opentelemetry) for capturing and transporting Observability signals.
Open Telemetry is an open standard (vendor-agnostic) and supports zero code instrumentation in multiple languages.
It allows us to choose from multiple vendors for backend storage and visualization systems (like Prometheus, NewRelic, Elastic)   

## Consequences
We will need to use the correct SDK for our language and choose how to run them alongside the service. 