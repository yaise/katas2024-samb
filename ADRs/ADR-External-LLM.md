# Use of Large Language Models and LLM Gateway

## Status

**Accepted**

## Context

ClearView has use cases for advanced job matching and summarization/bias removal. We are evaluating the use of Large Language Models (LLMs) 
for these use cases. Although developing LLMs in-house is an option, utilizing external LLM providers offers a quicker 
and potentially more cost-efficient solution. Numerous third-party providers, such as OpenAI, Google, and Azure, offer advanced models 
that can be easily integrated into our platform via APIs, delivering cutting-edge performance without the
need for internal development or maintenance.

## Decision
- We will integrate an external LLM provider to handle job matching and job summarization, leveraging their advanced capabilities
and reducing internal infrastructure needs. 

- All Outbound calls to external LLM will be routed via External LLM Gateway so that we are not locked into a specific vendor
and have ability to integrate/switch between one or more external LLM provider without effecting any of the consumers of the models. 

### **Rationale**
- **Access to Advanced Models**: External providers offer sophisticated LLMs optimized for tasks such as language understanding and matching.
- **Reduced Complexity**: Using external services eliminates the need for internal machine learning infrastructure.
- **Faster Implementation**: This approach accelerates the delivery of job matching and summarization features.
- **Cost Efficiency**: It reduces upfront costs, shifting expenses to a scalable usage-based model.

## Consequences

The external LLM gateway will enable integration with large language models in a loosely coupled manner.

