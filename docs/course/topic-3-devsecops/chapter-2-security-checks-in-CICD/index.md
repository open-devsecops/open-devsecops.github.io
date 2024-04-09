---
title: Chapter 2 - Security Checks in CD/CD
layout: default
parent: Topic 3 - DevSecOps
has_children: true
has_toc: false
nav_order: 1
---

# Chapter 2 - Security Checks in CD/CD

## The Importance of Security Checks in Each Stage of The Pipeline


A key component of DevSecOps is the introduction of a secure CI/CD pipeline. As you read in previous chapters, CI/CD is critical to DevSecOps because it:
>> * Automates and embeds security checks early in the development process
* Ensures rapid feedback regarding potential vulnerabilities
* Facilitates a proactive approach to security throughout the lifecycle of the application.

Every organization has a different way of defining their pipeline and the stages involved. Regardless of how many stages there are, it is crucial to ensure every stage has security checks from all realms of IT involved. These stages can generally look like:

* **The Planning phase**: The first step is to develop a product roadmap (threat modeling), which will help identify potential security threats. In threat modeling, potential vulnerabilities are identified and countermeasures are set in place to mitigate those risks.

* **Coding**: As developers begin writing code, take measures to make sure that the code is written in accordance with predefined standards and design guidelines. Use source code scanners to detect pieces of code that might be vulnerable to security threats.

* **Building**: As developers begin committing their source code to a shared repository, they need to make sure that automated tests are triggered to verify that the builds comply with requirements. 

* **Testing**: Once a build is successful, test the software for bugs. If new features are added on, more automated testing is performed.


>> {: .highlight }
The stages of SCLC can also be referred as the 6 stages:
1. Project Planning
2. Gathering Code Requirements & Analysis
3. Design and Build
4. Testing
5. Release
6. Deployment/Maintenance


<div style="text-align: center;">
    <img src="https://qentelli.com/sites/default/files/inline-images/devsecops-pipeline-inside-image.png" alt="CI/CD Pipeline" style="max-width:100%;height:auto;"/>
    <p><em>Source: <a href="https://qentelli.com/thought-leadership/insights/devsecops-pipeline-factors">Qentelli</a></em></p>
</div>

Due to the nature of continuous integration, every change needs to be monitored and made sure that it's safe to release. For every stage, there are multiple different controls that can be embedded to the process, whereas tool integrations are not sufficient by themselves for a secure CI/CD pipeline. Tools must be implemented to support the process mentioned above, but it's important to understand which tools to use and when. Understanding **SAST testing vs. DAST testing** espscially during the build stages will help ensure a secure SDLC.

## SAST vs. DAST
<!-- 
<style>
  table {
    width: 100%;
    border-collapse: collapse;
    border: 1px solid #ddd;
    margin-bottom: 20px;
  }
  th, td {
    padding: 15px;
    text-align: left;
    border-bottom: 1px solid #ddd;
    border-right: 1px solid #ddd;
  }
  th {
    background-color: #333;
    color: #fff;
  }
  th:last-child,
  td:last-child {
    border-right: none;
  }
  ul {
    list-style-type: disc;
    margin-top: 0;
    padding-left: 20px; /* Adjusted padding for the bullets */
  }
  ul li {
    margin-bottom: 5px;
  }
</style>
-->

<table>
  <tr>
    <th>Category</th>
    <th>SAST</th>
    <th>DAST</th>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td>SAST involves analyzing source code, byte code, or binary code of an application without executing it. Its purpose is to detect security vulnerabilities early in the development process by identifying parts of the code that might lead to security breaches.</td>
    <td>DAST involves testing an application’s security by simulating attacks on a running application. It aims to identify vulnerabilities that could be exploited during runtime, such as issues related to user authentication, SQL injection, and cross-site scripting (XSS).</td>

  </tr>
  <tr>
    <td><strong>Timeline</strong></td>
    <td>
      <ul>
        <li>SAST is typically conducted at the very early stages of the development cycle, often integrated into the Integrated Development Environment (IDE) or Continuous Integration/Continuous Deployment (CI/CD) pipeline.</li>
        <li>It is done before the application is run, usually as soon as the code is written.</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Conducted later in the development cycle, often after the application is in a stable build and deployed in a testing environment.</li>
        <li>It is performed on the running application in a safe envrionment, mimicking real-world hacking techniques.</li>
      </ul>
    </td>

  </tr>
  <tr>
    <td><strong>Pros</strong></td>
    <td>
      <ul>
        <li>Can detect vulnerabilities early in the development cycle, reducing the cost and effort of fixing them later</li>
        <li>If you can prevent vulnerabilities in software before you launch, you'll have stronger code and a more reliable application</li>
        <li>SAST can show you exactly where to find issues in the code</li>
        <li>Can be automated and integrated into the development process, facilitating early and regular security checks</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Can identify runtime and environmental issues that SAST cannot detect</li>
        <li>Does not require access to source code, making it applicable to any application</li>
        <li>Offers a real-world perspective on how an attacker might exploit vulnerabilities in a live application</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><strong>Cons</strong></td>
    <td>
      <ul>
        <li>Might produce false positives, requiring additional time for developers to sort through and validate issues</li>
        <li>Only identifies potential security issues in the static code, without considering runtime behavior or external interactions</li>
        <li>Requires access to the application's source code, which might not always be possible for third-party actors</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Heavy reliance on experts to write tests, making it difficult to scale</li>
        <li>Might miss certain types of vulnerabilities that can only be detected by analyzing the source code.</li>
        <li>Can lead to false negatives, as some vulnerabilities might not be detectable during a dynamic scan or might depend on specific conditions to trigger.</li>
      </ul>
    </td>

  </tr>
</table>

### Comparison and Integration:
Integrating both SAST and DAST in the security testing process provides a more comprehensive approach to application security. SAST can identify vulnerabilities early in the code, while DAST can test the application’s behavior in a runtime environment, catching issues that static analysis might miss. Together, they offer a balanced and thorough method for securing applications throughout the development lifecycle.

## Vulnerability scanning
## Examples of widely-used tools in industry


### References
**1.** “What is CI/CD security?” *Red Hat*, [https://www.redhat.com/en/topics/security/what-is-cicd-security#:~:text=CI%2FCD%20security%20is%20used,policies%2C%20and%20ensure%20quality%20assurance.](https://www.redhat.com/en/topics/security/what-is-cicd-security#:~:text=CI%2FCD%20security%20is%20used,policies%2C%20and%20ensure%20quality%20assurance.). Accessed 9 Apr. 2024.

**2.** “Security in every stage of CI/CD pipeline” *AWS*, [https://docs.aws.amazon.com/whitepapers/latest/practicing-continuous-integration-continuous-delivery/security-in-every-stage-of-cicd-pipeline.html](https://docs.aws.amazon.com/whitepapers/latest/practicing-continuous-integration-continuous-delivery/security-in-every-stage-of-cicd-pipeline.html). Accessed 9 Apr. 2024.

**3.** “SAST, DAST, and IAST Security Testing” *Contrast Security*, [https://www.contrastsecurity.com/security-influencers/why-the-difference-between-sast-dast-and-iast-matters](https://www.contrastsecurity.com/security-influencers/why-the-difference-between-sast-dast-and-iast-matters). Accessed 9 Apr. 2024.