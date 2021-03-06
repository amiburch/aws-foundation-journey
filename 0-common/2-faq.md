# Frequently Asked Questions (FAQs)

## General

### Q: Isn't this information already addressed in formal AWS documentation?

For example, in the AWS Control Tower documention.

No, not to our knowledge. This guide take an experience journey based approach to introducing customers to the overall use case, the set of typical requirements, and an overall solution before leading customers through the actual steps to realize a set development environments resting on the initial form of their AWS foundation.

Additionally, since the scope of the initial stage of customers' adoption of AWS extends beyond the domain of any single AWS service, it's difficult for any one AWS service to document such a wide ranging experience.

Moving forward there's an opportunity to introduce this type of documentation and knowlege into more mainstream AWS documentation.

### Q: What are the tenets for principles behind this project?

See [Tenets](1-tenets.md).

## AWS Account Design

### Q: Why aren't Sandbox AWS accounts included in the initial build out?

Since the premise of the initial guides is to help your organizations quickly establish a formal development environment in which experimentation, integration, development, and early testing of the first few application and/or data services can take place before they are rapidly moved through formal testing environments and into production, the traditional role of completely isolated and disconnected sandbox AWS accounts in which your organization's intellectual propertly (IP) including source code is not allowed does not yet apply to this overall scenario.

Instead, a focus of the guides is to establish development team AWS accounts to enable the formal work in support of the first few projects to progress rapidly.

#### Similarities to Traditional Sandbox AWS Accounts
In this very first and minimal stage of the build out, there are similarities between the development team AWS accounts and typical sandbox AWS accounts. For example, the initial lack of on-premises network integration and failrly wide ranging access to AWS services. However, the expectation is that your organization will either 1) require such gaps to be addressed at the outset and before development teams are onboarded, or 2) quickly address these gaps as fast follow-on requirements.

We expect that in most cases the initially provisioned developemnt team AWS accounts will quickly evolve to take on these additional properties. Rather than characterizing the initial development team AWS accounts as sandbox AWS accounts and needing to rename and reposition them later, the decision was made to position them as formal development team AWS accounts from the start.

#### Governed Sandboxes
The notion of ["governed sandboxes"](https://www.flux7.com/blog/aws-best-practice-sandbox-accounts-provide-secure-middle-ground/) is similar to the approach taken in these guides where development teams are provided wide latitude within a set of overall guardrails.

#### Future Role for Traditional Sandboxes
Similar to other aspects of overall AWS account design, the guide intentionally avoids overloading your organization with the fuller "to be" state too early in your cloud adoption journey. Depending on your needs, in the future and perhaps in the larger "foundation" stage of adoption or even earlier as a parallel workstream, the capability to provide truly isolated and ephemeral sandbox AWS accounts to support a specific set of use cases may be addressed.

## Federated Access to AWS Platform

### Q: Why isn't federated access addressed from the start?

Based on our experience, it can commonly take several weeks for an organization to go through the necessary preparation and execution to get true federated access into place. The minimal form of the foundation uses locally managed groups and users in AWS SSO for the first few weeks until a more desirable federated access capability is established.
