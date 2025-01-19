# Authenticated, Non-Authenticated, and Agent-Based Scanning Project

![Private Net Overview](https://github.com/user-attachments/assets/a92713d4-4c30-4b5e-b336-0be8075a24cf)

## Introduction/Objective
<p align="justify">The primary objective of this project is to explore and evaluate the effectiveness of three distinct scanning methodologies: authenticated, non-authenticated, and agent-based scanning. The goal is to understand their application, strengths, and limitations in identifying vulnerabilities within an IT environment. By leveraging Tenable's advanced scanning capabilities and hosting a controlled lab environment in Microsoft Azure, this project aims to demonstrate real-world use cases and provide actionable insights for cybersecurity professionals.</p>

> Disclaimer: Windows VMs were selected as the target environment for this project to maintain consistency and relevance in evaluating the differences between authenticated, non-authenticated, and agent-based scanning methodologies. The intention is not to compare the results across operating systems but to showcase the variation in results and use cases among the scan types. Windows was chosen due to its prevalence in enterprise environments and its suitability for demonstrating comprehensive vulnerability scanning scenarios.

## Components, Tools, and Technologies Employed
1. **Tenable:**
   - **Nessus:** For vulnerability assessment and scanning.
   - **Tenable.io:** For managing and reporting vulnerabilities in the cloud.
2. **Microsoft Azure:**
   - **Virtual Machines (VMs):** Configured with Windows and Linux for testing.
   - **Azure Active Directory:** To manage authenticated scanning scenarios.
3. **Technologies:**
   - **Secure Shell (SSH):** For Linux-based authenticated scanning.
   - **Remote Desktop Protocol (RDP):** For Windows-based authenticated scanning.
   - **Tenable Agents:** Deployed on VM instances to perform agent-based scans.
4. **Testing Environment:**
   - All resources were hosted within a private network in Microsoft Azure.
   - Windows VMs were selected in particular to represent the data 
   - A local scan engine was deployed within the private network to facilitate communication with Tenable.
   - Private IP addresses were exclusively used when configuring scan targets.
   - Test datasets and simulated vulnerabilities using vulnerable applications.

## Non-Authenticated Scanning
### Description:
Non-authenticated scanning involves probing a system externally without any credentials. It simulates an attacker's perspective, providing insights into vulnerabilities exposed to unauthorized users.

![image](https://github.com/user-attachments/assets/1a1a1018-64d0-498c-9d64-fefd066d5520)

### Process:
1. Configured a non-authenticated scan profile in Tenable Nessus.
2. Deployed scans across Azure-hosted VMs using their private IP addresses.
3. Captured results related to open ports, outdated software, and exposed services.

### Key Observations:
- Limited in-depth insights compared to credentialed scans.
- Effective in identifying surface-level vulnerabilities such as open ports and default configurations.
- Useful for evaluating perimeter defenses. <br><br>

## Authenticated Scanning
### Description:
Authenticated scanning involves using valid credentials to access system resources, providing deeper visibility into vulnerabilities.

![image](https://github.com/user-attachments/assets/7793d68e-aa9e-4999-a8d3-f1c033d6d450)

### Process:
1. Set up credentials for both Windows (RDP) and Linux (SSH) VMs.
2. Configured an authenticated scan profile in Tenable Nessus.
3. Ran scans using administrative access on private IP addresses, enabling comprehensive data collection.

### Key Observations:
- Identified more detailed vulnerabilities, including outdated patches and insecure configurations.
- Highlighted misconfigurations in user permissions and system policies.
- Required careful management of credential security. <br><br>

## Agent-Based Scanning
### Description:
Agent-based scanning uses lightweight agents installed on endpoints to continuously monitor and report vulnerabilities.

![image](https://github.com/user-attachments/assets/68bc3d4d-b1b1-4440-b13a-304ef4463eb4)

### Process:
1. Installed Tenable agents on Azure VMs.
2. Configured the agent-based scanning policy.
3. Collected vulnerability data directly from the endpoint.

### Key Observations:
- Provided real-time monitoring and analysis.
- Effective for systems with limited network connectivity or segmentation.
- Reduced network overhead compared to traditional scanning.

## Result Comparison Chart From The Different Scanning Types

![Auth, Non-Auth, Based Result Comparison](https://github.com/user-attachments/assets/4d809c07-24bc-4bca-b586-5806b3dca6b4)

<p align="justify">The analysis shows distinct differences in vulnerability detection across the three scanning types. Non-Authenticated Scanning identified only surface-level vulnerabilities, with 6 medium and 1 low severity, failing to detect any critical or high-severity issues. Authenticated Scanning uncovered 1 critical, 11 high, 18 medium, and 1 low-severity vulnerability, leveraging credentialed access for deeper insights. Agent-Based Scanning provided the most comprehensive coverage, detecting 1 critical, 15 high, 17 medium, and 1 low-severity vulnerability, benefiting from continuous monitoring and endpoint-specific analysis. These results underscore the need for a layered scanning approach, combining methods to ensure thorough vulnerability management and remediation.</p><br><br>

| **Aspect**                | **Non-Authenticated**             | **Authenticated**              | **Agent-Based**               |
|---------------------------|-----------------------------------|--------------------------------|--------------------------------|
| Depth of Analysis         | Surface-level                    | Comprehensive                 | Comprehensive                 |
| Credential Requirements   | None                             | Required                      | None (after installation)     |
| Real-Time Monitoring      | No                               | No                            | Yes                          |
| Network Overhead          | Medium                           | High                          | Low                          |
| Detection of Misconfigurations | Limited                         | Detailed                     | Detailed                     |
| Scalability               | High                             | Medium                        | High                         |

> The table highlights key trade-offs: Non-Authenticated Scanning is scalable but limited to surface-level analysis. Authenticated Scanning provides detailed insights but requires credentials and incurs high network overhead. Agent-Based Scanning offers comprehensive, real-time analysis with low overhead and high scalability, requiring initial agent setup.

## Insights
1. **Non-Authenticated Scanning:** Useful for external assessments but lacks the depth needed for internal vulnerability management.
2. **Authenticated Scanning:** Provides a granular view of system vulnerabilities but requires robust credential management.
3. **Agent-Based Scanning:** Offers continuous monitoring and is ideal for hybrid or segmented networks but necessitates agent deployment and maintenance.
4. Combining these methods can provide a layered approach to vulnerability management, ensuring comprehensive security coverage.

## Conclusion
<p align="justify">This project highlights the unique strengths and limitations of authenticated, non-authenticated, and agent-based scanning methodologies. By employing Tenable's tools in a controlled Azure environment, the findings emphasize the importance of choosing the appropriate scanning method based on specific security needs. All scans were performed within a private network, leveraging private IP addresses for secure and controlled testing. Moving forward, organizations should consider integrating these methods into a cohesive vulnerability management strategy to enhance their cybersecurity posture.</p>

