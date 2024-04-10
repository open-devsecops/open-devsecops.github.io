---
title: Chapter 3 - Deployment
layout: default
parent: Topic 2 - CI/CD
has_toc: false
nav_order: 3
---

# Introduction to Deployment
Transitioning from the exploration of DevOps and CI/CD, we now turn our attention to the critical phase of deployment. Deployment is where coding efforts from developers merge, and attempt to integrate into the existing software. With so many people making changes to the same product, there are bound to be inconsistencies and issues when pushing code. That is where deployment best practices within CI/CD come in. 

> **Problem Space**
>
> ⚠️ Imagine two developers are both working on projects for several months in a large organization. Ani is working on changing the current API used in the product, and Mariam is pulling from the current state of that API for her code. After working to get their projects working, they both push at the same time.
>
> Narek, a long time user of their site, is looking to buy pants. All of a sudden, the site is down! This was because when Ani and Mariam pushed there was no automatic testing and there were several integration issues:
>   - **Endpoint Mismatch**: Mariam's new features expect certain responses from the API that Ani has since altered or deprecated, leading to unexpected behavior and failures in feature operation.
>   - **Database Schema Changes**: Ani's API update included modifications to the database schema that Mariam's code was not designed to accommodate, resulting in broken database queries and data consistency issues.
>
> It might seem as though it was Ani and Mariam's lack of communication at fault for not communicating before building and deploying, but imagine they are working in a company as large as Amazon or Boeing. It would be impractical and redundant to expect to know every developer's job.




## Deployment Environments
| Environment           | Purpose                                        | Characteristics                                                                                                                                                         | CI/CD Role                                                                     | 
|-----------------------|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| 💻 Development        | Initial coding and testing by developers.      | - Runs on local machines or a dev server. <br> - Frequent changes and updates. <br> - Connected to a test database. <br> - Debugging tools are enabled.                | The starting point in the CI/CD process. Triggers the initial build and unit tests. |
| 🚦 Staging            | Final testing before going live. Acts as a pre-production replica. | - Closely mimics the production environment. <br> - Stable and isolated for accurate testing. <br> - Hosts the release candidate version.                           | Used for performance, integration, and user acceptance testing. Final checks before production.             |
| 🌐 Production         | The live environment used by end-users.         | - The most stable and secure. <br> - Contains real user data and faces the internet. <br> - Performance monitoring and error logging are carefully balanced.          | The final stage of the pipeline. If all checks pass, code is deployed here.     |

<br>

![image](https://github.com/open-devsecops/open-devsecops.github.io/assets/35845527/6c306e97-b563-4cc7-baff-8d79ddc45bdf)
_Source: [DevOps.com](/https://devops.com/i-want-to-do-continuous-deployment/)_

## Deployment Strategies

Deployment strategies are crucial for managing the transition of code from development through to production. Choosing the right strategy ensures that deployments are smooth, risks are minimized, and the user experience remains uninterrupted. Here are some common deployment strategies used in modern software development:

1. 🔄 **Blue-Green Deployment**: Alternating between two identical environments to switch versions.

   | Pros              | Cons                 |
   |-------------------|----------------------|
   | Easy rollback     | Resource intensive   |
   | Minimal downtime  | Complex setup        |

   **Use Case**: Ideal for critical applications where zero downtime is essential.

  
2. 🐦 **Canary Deployment**: Gradually rolling out changes to a small subset of users first.

   | Pros                              | Cons                              |
   |-----------------------------------|-----------------------------------|
   | Low risk with smaller user impact | Requires monitoring and analytics |
   | Real user feedback                | More complex release process      |

   **Use Case**: Best suited for applications with a large user base to gauge the impact of new changes.

3. 🌊 **Rolling Deployment**: Updating application instances in phases, without taking down the entire app.

   | Pros                       | Cons                                 |
   |----------------------------|--------------------------------------|
   | High availability          | Not suitable for database changes    |
   | No need for additional infrastructure | Potential for brief inconsistency |

   **Use Case**: Services requiring constant availability and those with enough instances to support a phased rollout.

4. 🚦 **Feature Toggles**: Releasing features hidden behind toggles, which can be enabled conditionally.

   | Pros                          | Cons                              |
   |-------------------------------|-----------------------------------|
   | Flexible control over features | Complexity in managing toggles    |
   | Easy rollback of features     | Risk of technical debt            |

   **Use Case**: Testing new features in live environments or rolling out features gradually.

5. 🔀 **A/B Testing Deployment**: Deploying two versions to compare which performs better based on specific metrics.

   | Pros                            | Cons                             |
   |---------------------------------|----------------------------------|
   | Data-driven decision making     | Requires traffic segmentation    |
   | Clear insight into user preferences | Increased complexity           |

   **Use Case**: Optimizing user experience and validating hypotheses about user behavior.

6. 🆕 **Immutable Deployments**: Every deployment creates a new environment, and traffic is switched over once ready.

   | Pros                               | Cons                                  |
   |------------------------------------|---------------------------------------|
   | Consistency and reliability       | Higher infrastructure costs           |
   | Simplifies rollback               | Requires automation for efficiency    |

   **Use Case**: Suitable for cloud-native applications where infrastructure can be easily replicated and managed as code.



## Utilizing Web Hooks for Continuous Integration
### What is a Web Hook?
When deploying code, you want to make sure it is automatically running through several relevant tests without you triggering them every single time. A webhook is like a notification for your CI/CD tests, that you have done something with your code. To set up a webhook, you first need to define rules that it follows:

1. **Choose Trigger Events:** During the webhook setup process in GitHub, you specify which events will trigger the webhook. This could be a variety of actions, such as:
- **Pushes:** Every time someone pushes code to the repository.
- **Pull Requests:** When a new pull request is opened, closed, or merged.
- **Releases:** When a new release is created.
- **Branch or Tag Creation:** When a new branch or tag is created.

2. **Set the Payload URL:** This is where you want GitHub to send the notification. The URL is provided by the service you want to notify (your CI/CD platform, for example).

3. **Configure Content Type:** This determines how the data is formatted when sent to the receiver. JSON is a common format.

4. **Determine Security Options:** If your receiving service requires it, you might also set up a secret token that GitHub will use to sign the data, adding a layer of security to ensure the data is only accepted if it’s verified as coming from GitHub.

Then, once you want to make a change, the following happens:
1. **You push code to GitHub** - This is you updating your repository with new changes.
2. **GitHub sends a webhook** - Because of the rule you set up, GitHub notifies your CI/CD tool that something happened (like a code push).
3. **CI/CD tool starts tests** - The CI/CD tool, now informed by the webhook, starts running the tests or actions you've configured it to perform upon receiving such a notification.

<details>
  <Summary>Sources</Summary>
  - https://devops.com/i-want-to-do-continuous-deployment/
  - https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html
  - https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/deployment-strategies.html
  - https://thenewstack.io/deployment-strategies/
  - https://www.plutora.com/blog/deployment-strategies-6-explained-in-depth
  - https://codefresh.io/learn/ci-cd-pipelines/ci-cd-process-flow-stages-and-critical-best-practices/#:~:text=The%20deploy%20stage%20is%20the,it%20accessible%20to%20end%2Dusers.
  - https://www.redhat.com/en/topics/automation/what-is-a-webhook
  - https://hookdeck.com/webhooks/guides/what-are-webhooks-how-they-work
  - https://docs.github.com/en/webhooks/about-webhooks 
  - https://www.youtube.com/watch?v=mrkQ5iLb4DM 
</details>
