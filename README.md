# Windows Active Directory Lab

## Objective
The objective of this project was to simulate a corporate enterprise network by deploying a Windows Server 2022 domain environment and provisioning Windows 11 client machines using VirtualBox. This lab focuses on core system administration skills, including Active Directory identity management, Group Policy enforcement, and automated vulnerability mitigation using Action1 patch management.

## Skills Demonstrated
*   **Systems Administration:** Deployed, configured, and managed Windows Server 2022 and Windows 11 endpoints.
*   **Identity & Access Management:** Administered Active Directory Domain Services (AD DS) utilizing template accounts and logical Organizational Unit (OU) structures.
*   **Security & Policy Enforcement:** Designed and implemented Group Policy Objects (GPOs) to enforce security protocols and standardize system configurations.
*   **Vulnerability Management:** Integrated Action1 to automate remote software deployments and OS patch management across the domain.

## Tools and Technologies
*   **Hypervisor:** Oracle VM VirtualBox
*   **Servers:** Windows Server 2022 (Domain Controller)
*   **Clients:** Windows 11 Pro
*   **Core Services:** Active Directory (AD DS), DNS, DHCP
*   **Endpoint Management:** Action1 (RMM & Patch Management)

## Environment Architecture
*   **Domain Name:** `DAVID`
*   **Virtual Network:** VirtualBox Internal Network
*   **Domain Controller (`WA-01`):** Hosts AD DS, DNS, and serves as the primary management node.
*   **Client Endpoints (`AD1`):** Windows 11 machines joined to the domain.
*   **Patch Management:** Action1 cloud console communicating with locally installed agents on domain machines.

<img width="754" height="530" alt="ADUC" src="https://github.com/user-attachments/assets/01473e08-0826-42d9-ae00-4b8b4344fcee" />

## Key Configurations & Deployment Steps

### 1. Infrastructure Deployment
*   Provisioned a VirtualBox environment to simulate an enterprise setup.
*   Installed Windows Server 2022, assigned static IP addressing, and promoted the server to a Domain Controller.
*   Provisioned Windows 11 virtual machines and successfully joined them to the newly established domain.

### 2. Active Directory Administration
*   Created Organizational Unit (OU) hierarchy to separate Users, groups, and Administrative accounts.
*   Created **Template User Accounts** to streamline the onboarding process and ensure consistent permissions and group memberships for new hires.

### 3. Group Policy Implementation
*Developed and linked GPOs across specific OUs to enforce domain-wide standards:*
*   **Account Policies:** Password age, length, and complexity requirements, account lockout threshold
*   **User Configurations:** enforcing corporate desktop wallpapers, prevent Changing Desktop Icons \ Themes
* Mapped shared network drives

### 4. Patch Management & Automation (Action1)
*   Deployed the Action1 agent to all domain-joined Windows 11 endpoints and Windows server.
*   Used Action1 console to push critical Windows updates and third-party software updates.
*   Secured the AD environment by verifying patch compliance and mitigating simulated software vulnerabilities remotely.
<img width="1920" height="963" alt="action1_pic1" src="https://github.com/user-attachments/assets/aab35941-22f8-42e6-83f0-b38e9f3fdad5" />

## Challenges & Troubleshooting
*   **Issue:** Windows server 2022 was not successfully pulling the Action1 updates over the network.
    *   **Resolution:** Take Windows Server 2022 from Internal Network to Bridged Adapter so that Windows server was connected to the internet to receive the updates from Action1
