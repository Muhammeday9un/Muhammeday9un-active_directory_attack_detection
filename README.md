# Active Directory Attack Detection using Sigma Rules

This project aims to enhance the detection of Active Directory (AD) attacks by developing Sigma rules tailored to identify various types of attacks in AD environments. Sigma is a generic signature format used for the detection of suspicious activities across different systems and platforms, and it can be adapted to address specific attack vectors in Active Directory environments.

## Project Overview

Active Directory is a critical component of most enterprise networks, providing centralized management of users, computers, and resources. However, it is also a frequent target for attackers seeking to exploit vulnerabilities for privilege escalation, lateral movement, and other malicious activities. This project focuses on developing Sigma rules to detect such attack scenarios in AD environments.

### Features

- **Sigma Rule Development**: Custom Sigma rules designed to detect a variety of Active Directory attack techniques.
- **Detection for Common AD Attacks**: Includes rules for detecting attack techniques such as:
  - Password Spraying
  - Kerberoasting
  - DCShadow
  - Skeleton Key
  - LDAP Injection
  - ZeroLogon
  - PrintNightmare
  - And more...
- **Ease of Use**: The Sigma rules are written in a simple, clear, and reusable format, making them compatible with SIEM (Security Information and Event Management) tools such as Elastic Stack, Splunk, and more.
- **Automated Detection**: Once implemented, these rules can be used to automatically identify potential malicious activity in Active Directory systems, reducing the workload for security teams.

## Getting Started

To use the Sigma rules from this repository, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Muhammeday9un/active_directory_attack_detection.git
   ```
2. **Setup Your SIEM**:
   Configure your SIEM platform to ingest and process Sigma rule files. Refer to your SIEM’s documentation for instructions on how to import Sigma rules.
   
3. **Apply the Sigma Rules**:
   Implement the Sigma rules in your environment based on your SIEM tool and the specific AD environment configurations. The rules are designed to detect a wide range of AD-specific attacks and alert on suspicious activities.

4. **Test and Monitor**:
   Once the Sigma rules are applied, continuously monitor alerts generated by the system. Fine-tune the rules as needed based on the nature of the environment and false-positive detection.

## Example of Rule

Here's an example of a Sigma rule designed to detect a Kerberoasting attack:

```yaml
title: Detection of Kerberoasting Attack
id: eae7ed0a-1b1f-4bfb-b2c7-1fefbe4a92d2
status: experimental
description: |
  This rule detects potential Kerberoasting attacks by looking for anomalous service ticket requests in the Active Directory environment.
logsource:
  product: windows
  service: security
detection:
  selection:
    EventID: 4769
    ServiceName: '.*'
  condition: selection
fields:
  - EventID
  - ServiceName
falsepositives:
  - Normal user service account activity
level: high
```

## Contributing

Contributions to the project are welcome! If you would like to improve the detection rules, add new ones, or report issues, please feel free to submit a pull request or open an issue.

### Steps to Contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Implement your changes or improvements.
4. Commit your changes (`git commit -m "Add new detection rule"`).
5. Push to your forked repository (`git push origin feature-branch`).
6. Open a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

