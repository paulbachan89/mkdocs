## Working with Active Directory

Now that you have a few Domain Controllers in your Infrastructure, we can now begin exploring the extend that is Microsoft's Active Directory. First thing to know, there is no single tool that you can use to manage all aspects of Active Directory. They are multiple tools and each tools does something different. Before diving into anything, let's talk about Active Directory and it's various tools:

## What is Active Directory


Microsoft Active Directory (AD) is a directory service developed by Microsoft for Windows domain networks. It organizes and manages network resources, such as users, computers, printers, and permissions, in a centralized manner. AD is based on LDAP (Lightweight Directory Access Protocol) and supports authentication and authorization, allowing administrators to control access to resources securely. Active Directory runs on Windows Server and is crucial in managing users, enforcing security policies, and enabling single sign-on (SSO) for seamless access across network services. The core components include:

- **Domain Services (AD DS)** – Stores directory data and manages user interactions with the domain.

- **Lightweight Directory Services (AD LDS)** – Provides similar directory services without requiring a domain.

- **Certificate Services (AD CS)** – Manages digital certificates for security.

- **Federation Services (AD FS)** – Supports SSO across different organizations or applications.

- **Rights Management Services (AD RMS)** – Protects digital information from unauthorized use.

Active Directory domains are often grouped into forests and organized with trust relationships, allowing secure resource sharing across domains and networks.

## Benefits of Active Directory

The goal of Active Directory is to make managing your Domain easy. It grants you a set of that tools that you can use to manage your Environment. These tools range from managing the users and groups, managing your different sites and your domains, but this is just the high level functions. Here are some other things that Active Directory does for us:

## Centralize Data Repository

Active Directory uses a centralized database called NTDS.dit to store digital identities, such as users, applications, and resources, across a network. This database is based on the Joint Engine Technology (JET), allowing Active Directory to handle a large volume of data (up to two billion objects). Each identity in this database is unique and accessible from any authorized point in the network.

One of the core benefits of centralizing identities in Active Directory is that it eliminates the need for duplicate accounts across different systems. Without such centralization, administrators would need to manage user accounts and permissions separately for each system, increasing both workload and the chance of security gaps. With Active Directory, administrators can manage user authentication (proving identity) and authorization (defining what each user can access) from one central console, streamlining network access and reducing administrative overhead.

## Data Replication in Active Directory

In complex environments with multiple locations or high availability needs, organizations often use multiple domain controllers. As we've learned, A domain controller is a server that responds to authentication requests and verifies users on a network. Each domain controller holds a copy of the Active Directory database, which is kept in sync through data replication.

Consider a user, Jane, who works at the headquarters in Toronto, Canada and then needs access from a branch office. If she forgets her password and requests a reset, the change is made on a domain controller at headquarters (e.g., DC01). To ensure Jane can log in from the branch office in 30 minutes, this password change needs to replicate to the branch office’s domain controller at Ottawa (e.g., DC05). Active Directory ensures that updates on one domain controller are quickly synchronized with all other domain controllers in the network.

Microsoft Active Directory handles replication in two main ways:

- **Outbound Replication**: When a domain controller shares changes it made with neighboring controllers, it’s called outbound replication.

- **Inbound Replication**: When a domain controller accepts updates shared by other domain controllers, it’s called inbound replication.

Replication schedules and connections (who replicates with whom) can be tailored to business needs, allowing organizations to balance network traffic and ensure that critical updates are distributed efficiently across all domain controllers. This system ensures seamless access for users, even in geographically distributed or highly available setups, by keeping identity and access data synchronized across the network.

## High Availability in Active Directory

High availability is essential for any system that plays a critical role in an organization, including Active Directory (AD). Ensuring domain controllers are always accessible is vital, as they handle user authentication and access control across the network.

In other systems, high availability often requires additional software or hardware configurations. However, Active Directory domain controllers come with built-in fault tolerance and multi-master replication, which means multiple domain controllers can handle updates simultaneously. This design allows users to authenticate and access resources from any domain controller on the network, even if one or more controllers are temporarily unavailable.

Active Directory’s multi-master database and replication capabilities ensure that all domain controllers stay synchronized. If one domain controller goes down, others can seamlessly continue providing authentication and authorization services without service interruption.

To maintain high availability, Microsoft recommends running at least two domain controllers. This redundancy ensures that, even in the event of a hardware failure or network issue with one controller, users and systems continue to have uninterrupted access to network resources.

## Security in Active Directory

In today’s digital landscape, protecting data and identities is crucial, as identity has become a central element of network security. Active Directory (AD) offers a robust set of security features to safeguard digital identities and control access to resources, helping organizations protect against evolving threats.

AD supports multiple authentication methods, such as passwords, certificates, and biometrics, allowing administrators to enforce the appropriate level of security based on organizational requirements. Additionally, AD enables group policies—rules that control security settings and permissions across all users and devices in the network. This allows administrators to apply consistent security policies, like password complexity or login restrictions, across the organization with minimal effort.

AD also provides workflows for managing permissions and access, ensuring that resources are only accessible to authorized users. These features are not limited to users; applications integrated with AD also benefit from these security controls, enabling them to securely authenticate users and manage access based on established policies.

Together, these tools make AD a powerful solution for managing identity security, protecting sensitive data, and maintaining compliance with security standards in a modern business environment.

## Auditing Capabilities in Active Directory

While advanced security policies are essential, regular auditing is equally important for detecting new threats and ensuring ongoing protection of digital identities. Active Directory (AD) includes built-in auditing capabilities that allow administrators to monitor and log critical events, offering insights into user activities and potential security issues.

In an AD environment, various events—such as user authentications, changes to directory services, and access violations—are automatically recorded. These logs are accessible in the Event Viewer and are organized under different categories, making it easy for administrators to review specific types of events.

By examining these logs, administrators can track who accessed the network, what changes were made, and identify unauthorized access attempts. This enables timely responses to security incidents, supports compliance requirements, and helps proactively address potential vulnerabilities. AD’s auditing features play a key role in maintaining a secure identity infrastructure by providing ongoing visibility into user actions and system changes.

## Single Sign-On (SSO) in Active Directory

In many organizations, multiple applications and systems are in use, each with its own authentication method. Managing separate credentials for each application can be burdensome for users and administrators alike. Active Directory (AD) simplifies this with Single Sign-On (SSO), which allows users to authenticate once and gain seamless access to multiple AD-integrated applications and systems.

With SSO, users log in once with their AD credentials, and that session is used to authenticate them across other applications and services in the organization without needing to re-enter their credentials. This not only improves user convenience but also enhances security by reducing the risk of password fatigue, where users might create weak passwords or reuse passwords across systems.

Most modern applications support integration with AD, making SSO a widely applicable solution across various platforms, from on-premises applications to cloud services. By centralizing authentication through AD, organizations can better manage access control, streamline user experiences, and reinforce security across their network.

## Schema Modification in Active Directory

In any database system, a schema defines the structure of how data is stored and how different data elements relate to each other. This concept applies to Active Directory (AD) as well. The Active Directory schema outlines the types of objects that can exist in the directory and the attributes those objects can have.

The Active Directory schema mainly consists of two types of definitions:

- **Object Class Definitions**: These define the various types of objects that can be created in Active Directory, such as users, computers, groups, and organizational units. Each object class serves as a template that specifies which attributes are associated with that type of object.

- **Attribute Definitions**: These define the individual pieces of information (properties) that an object can have. For example, a user object might have attributes like FirstName, LastName, Email, and PhoneNumber.

The number and types of object classes and attributes can vary depending on the version of Active Directory you are using. Importantly, the schema is extensible, meaning you can modify or extend it to suit your organization's specific needs.

### Why Modify the Schema?

Modifying or extending the Active Directory schema is crucial for several reasons:

- Custom Attributes: You might need to store additional information about objects that isn't covered by the default attributes. For example, adding an employee ID or a custom organizational role.

- Application Integration: Some applications require additional object classes or attributes to function properly within Active Directory. By extending the schema, these applications can store and retrieve the necessary data directly from AD.

- Enhanced Functionality: Extending the schema can enable new features and improve how services interact with directory data.

## Active Directory Service Interfaces (ADSI)

To facilitate interaction with Active Directory, Microsoft provides the Active Directory Service Interfaces (ADSI). ADSI is a set of Component Object Model (COM) interfaces that allow developers to programmatically access and manage Active Directory services using various programming languages, such as C++, VBScript, or PowerShell.

Key features of ADSI include:

- Cross-Provider Compatibility: ADSI can interact with different directory service providers, not just Active Directory. This means developers can write applications that work across various directory services.

- Simplified Access: ADSI abstracts the complexities of the underlying protocols (like LDAP), providing simpler methods to perform common tasks such as creating or modifying objects, querying the directory, and handling authentication.

- Customization and Extension: Developers can use ADSI to modify the schema, adding new object classes or attributes as required by their applications.

By understanding and utilizing schema modification in Active Directory, organizations can tailor the directory service to better fit their needs, enhance application functionality, and maintain centralized control over identity and access management.

## How Querying and Indexing Work

- **Querying**: AD uses the Lightweight Directory Access Protocol (LDAP), which allows for complex searches across the directory. Applications or administrators can query AD to retrieve specific data based on various filters, such as username, department, or even security group membership. This allows for flexible and efficient data retrieval across the entire directory.

- **Indexing**: To speed up query responses, AD maintains indexes on frequently searched attributes, like usernames or group memberships. Indexing allows AD to retrieve data more quickly, improving performance, especially in large environments with vast amounts of data. The indexed attributes are optimized for rapid searching, which is critical for supporting complex environments.

### Benefits of Querying and Indexing in Active Directory

- Efficient Data Access: Administrators and applications can easily access the required information without navigating complex organizational structures.

- Reduced Administrative Effort: Centralized querying simplifies management tasks, allowing administrators to gather details on users, computers, or policies quickly, without searching through separate systems.

- Support for Applications: Many applications integrated with AD rely on directory queries to retrieve user data, enabling personalized experiences and centralized access control.

- Enhanced Directory Performance: With indexing, AD can handle large volumes of data while still providing quick responses to queries, ensuring that users and applications experience minimal latency.

By providing these capabilities, Active Directory enables organizations to streamline identity management, make data easily accessible for authorized users and applications, and enhance overall directory performance.

So that's some of the benefits that Active Directory provides. I'm sure there are lots more that I didn't include and you may even find other benefits along the way.

Let's continue

## Understanding Active Directory Components
Active Directory (AD) is made up of two primary types of components:

- Logical Components

- Physical Components

Both types of components play distinct roles in structuring and managing the directory, and each requires careful planning for an effective AD setup.

### Logical Components of Active Directory

When designing an Active Directory (AD) structure, it’s essential to align with the organization’s hierarchy and operational needs. The logical components of AD help structure the directory in a way that supports effective management, security, and scalability.

Active Directory logical objects are divided into two types:

- Container Objects: These can contain other objects, helping organize and manage resources hierarchically. Examples include forests, domains, domain trees, and organizational units (OUs).

- Leaf Objects: These are the smallest components, such as individual users, computers, and groups, which do not contain other objects.

Here’s a breakdown of each logical component:

### Forests

An Active Directory forest is the highest-level container, representing an entire AD instance. It can contain one or more domains and domain trees, sharing a common schema, configuration, and global catalog. Forests are defined by their boundaries and are typically used when an organization has multiple independent groups needing unique namespaces but shared resources.

- Trust Relationships: Domains within a forest have two-way transitive trusts, allowing objects in one domain to recognize and authenticate with objects in another.

- Forest Root Domain: The first domain created becomes the root domain of the forest, and additional domains can be added as child or sibling domains.

- Functional Levels: Forests have functional levels based on the version of AD being used. These levels determine the features and capabilities available within the forest.

### Domains

A domain is a logical grouping within a forest, serving as a security boundary. Each domain contains its own set of objects (users, computers, groups) and can enforce unique security policies.

- Security and Administrative Boundaries: Domains control access permissions for their objects, and permissions set within a domain generally do not extend outside it.

- Domain Partitions: Each domain has a specific partition within the AD database, containing its objects. Domain controllers within the same domain share this partition to ensure consistent data.

- Domain Functional Levels: Like forests, domains have functional levels that enable certain features depending on the server version. The domain functional level must not exceed the forest’s functional level.

### Domain Trees

A domain tree is a collection of domains that share a contiguous namespace and a parent-child relationship. For example, in a domain tree with a parent domain called prblabs.ca, child domains might be blog.prblabs.ca and vpn.prblabs.ca.


- Parent-Child Relationships: The first domain in a domain tree is the parent domain (root domain), and additional domains are created as child domains.

- Trusts: Domain trees maintain two-way transitive trusts between parent and child domains, allowing for authentication requests to be passed up and down the hierarchy.

### Organizational Units (OUs)

**Organizational Units** are containers within a domain, used to organize objects based on similar security and administrative needs, like departments or geographic locations. OUs allow for granular organization without the need for separate domains.

- **Policy Application**: OUs enable the application of Group Policies to specific user or device groups, simplifying security and access management.

- **Delegated Administration**: Admin rights can be delegated at the OU level, allowing specific individuals or groups to manage only their designated OU without impacting the broader domain.

- **Inheritance**: OUs can have nested structures (child OUs), where child OUs inherit permissions and policies from parent OUs, enabling a tiered approach to security and management.

Example Scenario

Imagine a company with multiple departments (Sales, IT, HR) across several regional offices (North America, South America, Africa). Here’s how they might use logical components in Active Directory:


- Forest: The company has one AD forest, company.com, containing all domains.

- Domains: Each regional office could be a domain, such as northamerica.prblabs.ca, southamerica.prblabs.ca, and africa.prblabs.ca, to enforce region-specific policies.

- Domain Tree: The domains share the prblabs.ca namespace and are part of a single domain tree.

- Organizational Units: Within each domain, departments like Sales, IT, and HR are organized into OUs, with additional child OUs for sub-departments or teams as needed.

Using this setup, administrators can apply policies specific to each department or region, manage user permissions efficiently, and delegate control at multiple levels.

By structuring Active Directory with these logical components, organizations can create a flexible, secure, and scalable identity management system that aligns with their unique business requirements.

## Physical Components of Active Directory

Active Directory's physical components focus on the network topology, placement of domain controllers, and site configurations, all of which directly impact replication, authentication, and service location efficiency. Unlike logical components, which can be reorganized more flexibly, physical components are more rigid due to their dependency on hardware and network infrastructure.

### Domain Controllers

A Domain Controller (DC) is a server that hosts the Active Directory Domain Services (AD DS) role and stores a copy of the AD database for its domain. DCs can be either physical or virtual servers and are central to handling authentication, authorization, and directory lookups.

- Multi-Master Replication: Since Windows Server 2000, AD DS supports multi-master replication, meaning any domain controller can make directory changes, which are then replicated to other DCs.

- FSMO Roles: While all DCs have equal permissions, certain critical operations are limited to specific DCs with Flexible Single Master Operations (FSMO) roles. These roles manage functions like schema updates and domain naming.

- Global Catalog Servers: Some DCs act as global catalog servers, which store a partial, searchable replica of every object in the forest. This enables cross-domain searches and authentication without needing to contact every domain. Only the first DC in a domain is automatically set as a global catalog server, and additional ones can be designated based on network needs.

### Active Directory Sites

**Active Directory Sites** represent the physical network topology, grouping DCs within specific network segments to improve replication and authentication efficiency. Sites are especially useful in environments with multiple geographic locations, like branch offices or remote facilities.

- Replication Optimization: Sites allow administrators to control replication schedules and bandwidth usage between locations. For instance, remote sites connected by slower links can be configured to replicate during non-peak hours, reducing strain on network resources.

- Service Location: By associating specific servers with sites, AD DS can direct users to the nearest available resources. For example, users in a Toronto office can be pointed to their local Exchange Server instead of the one in London.

- Local Authentication: When users log in, they’re directed to a local domain controller within their site, minimizing latency and reducing network traffic. AD DS sites ensure that a user in Toronto, for example, authenticates with a Toronto-based DC instead of one in London, making logins faster and more reliable.

### Example Scenario: Multi-Site Configuration

Consider a company with two offices: Toronto and Ottawa. Each office has its own DCs (e.g., DC01 and DC02 in Toronto, DC03 and DC04 in Ottawa) but shares a single AD forest. The network is interconnected by a leased line, with different IP subnets for each location.

- Sites Configuration: The Toronto office has subnets 192.168.148.0/24, 10.10.10.0/24, and 172.25.16.0/24, while the Ottawa office has 10.11.11.0/24 and 172.0.2.0/24. Each site is configured with its respective subnets, ensuring that users authenticate locally and use nearby services.

- Replication: Replication schedules between Toronto and Ottawa are optimized to reduce bandwidth usage during peak hours, ensuring essential data is synchronized without overloading network links.

- Service Location: When a Toronto user accesses their email, they’re directed to the Toronto Exchange Server instead of the one in Ottawa, improving performance and resource efficiency.

## Key Benefits of Active Directory Sites

- Efficient Replication: Sites allow for custom replication schedules and bandwidth control, ensuring that data remains synchronized without affecting other network services.

- Optimized Service Access: Users are directed to the nearest servers for services like email and certificate authorities, minimizing delays and improving responsiveness.

- Reduced Authentication Latency: Local DCs handle user authentication requests, reducing login times and conserving bandwidth across site links.

### Updating Sites with Physical Topology Changes

AD DS sites reflect the network's physical structure, so any topology changes—such as adding new subnets—must be updated in the AD DS configuration. Failing to update site configurations may prevent AD DS from fully utilizing the benefits of optimized replication, service location, and local authentication.

By carefully planning the placement of domain controllers, global catalog servers, and AD DS sites, organizations can optimize Active Directory’s performance, reliability, and manageability across geographically distributed environments.

## Understanding Active Directory Objects

In Active Directory (AD), objects represent entities within an organization, such as users, computers, printers, and groups. Each object in AD has attributes that describe it, similar to how we might use unique characteristics to identify a person. For example, a person’s unique identifier could be a driver license's number or a birth certificate number, while an object's unique attribute might be its serial number. Attributes allow AD to uniquely identify and manage each object.

Types of Active Directory Objects

AD objects fall into two main categories:

- Container Objects: These are objects that can hold other objects. Examples include domains and organizational units (OUs). Container objects help organize and manage other objects within AD, similar to folders in a file system.

- Leaf Objects: These are objects that cannot contain other objects. Examples include user accounts, computers, and service accounts. Leaf objects are typically the entities that perform actions within the network, like logging in or accessing resources.

### Object Attributes

Each AD object has attributes that define its properties. For instance, a user object might include attributes such as:

- First Name
- Last Name
- User Logon Name

Similarly, a computer object might have attributes like the Computer Name. The attributes required for each object depend on its type, defined by an object class within the AD schema.

### The Role of the AD Schema

The Active Directory schema defines the object classes and the attributes associated with each type of object. It’s like a blueprint that specifies which attributes are available for each object type. For example, user objects have attributes like User Logon Name and Email, while computer objects have attributes like Computer Name. This consistency ensures that AD can manage and understand each object’s data, regardless of how many instances of an object type exist.

Just as when filling out an online form, each required attribute must be filled out with data in the correct format. For instance, User Logon Name is mandatory for creating a user account, but Last Name is optional. The schema ensures that attributes meet predefined data formats and requirements, which helps maintain data integrity.

### Custom Attributes

Organizations may sometimes need additional, custom attributes to store information not covered by the default schema. For example, a company might want to add a Employee ID or Department Code attribute to user objects. By extending the schema, administrators can add custom attributes to meet unique operational requirements.

### Example Scenario

Imagine you’re creating a user account in AD for a new employee. During the account creation process, you’ll be prompted to enter attributes like First Name, Last Name, and User Logon Name. These attributes ensure that the user’s identity is clear and distinguishable from others. The attributes you enter follow the schema, which defines which are mandatory (such as User Logon Name) and which are optional (such as Last Name).

If, in the future, the organization wants to track employees by a unique Employee ID that’s not part of the default schema, administrators can modify the schema to add this attribute. This flexibility allows AD to adapt to evolving business needs without sacrificing its core structure.

Understanding objects and their attributes is fundamental to managing AD, as these elements enable efficient organization, access control, and identity management across the network.

## Globally Unique Identifiers (GUIDs) and Security Identifiers (SIDs) in Active Directory

In an Active Directory (AD) environment, unique identifiers are essential for managing and securing large numbers of objects. AD uses two main types of unique identifiers:

- Globally Unique Identifier (GUID)

- Security Identifier (SID)

These identifiers ensure that each object is uniquely recognized, even if other attributes like the name are similar or identical.

### Globally Unique Identifier (GUID)

The GUID is a 128-bit value assigned to every object in AD, including users, computers, and groups. This identifier is stored in the objectGUID attribute and remains constant for the lifetime of the object, even if the object is moved or modified within the directory.

Key points about GUIDs:

- Universally Unique: Although not absolutely guaranteed, GUIDs are highly unlikely to be duplicated due to the complex algorithms used in their generation.

- Permanent: Once assigned, the GUID remains unchanged until the object is deleted.

- Global Validity: GUIDs are valid across AD domains, making them useful for applications that need to locate objects consistently.

- Efficient Searches: When an application or service in AD needs to search for an object, querying by the GUID yields accurate results since it is unique to each object.

You can view the GUID for an AD object using PowerShell:

```
Get-ADUser -Identity username | Select-Object ObjectGUID
```

In this command, replace username with the actual username. The ObjectGUID attribute will display the GUID assigned to the user.

### Security Identifier (SID)

The SID is a unique identifier for security purposes, specific to the domain in which the object exists. Every user, group, and computer object has a SID stored in its objectSid attribute. SIDs are essential in access control as they are used in Access Control Lists (ACLs) to determine an object’s permissions.

Key points about SIDs:

- Domain-Specific: SIDs are unique within their domain, not globally. If an object is moved to a different domain, it will receive a new SID.

- sIDHistory: When an object (such as a user) is migrated to a new domain, its old SID is saved in the sIDHistory attribute. This allows the user to retain access to resources assigned under the previous SID, preventing the need to reconfigure ACLs.

- Access Control: AD resources reference SIDs to allow or deny access based on permissions set in the ACL. Without sIDHistory, an object moving to a new domain could lose access to its resources until ACLs are updated.
You can view the SID for a user account with the following PowerShell command:

```
Get-ADUser -Identity username | Select-Object SID
```

In this command, replace username with the actual username. The SID attribute will display the SID assigned to the user.

### Example Scenario

Consider a scenario where a user account is moved from one domain to another. When the user is migrated:

- New SID: A new SID is generated for the user in the new domain.

- SID History: The old SID is stored in the sIDHistory attribute, allowing the user to retain access to resources in the previous domain without needing to adjust every ACL.

When the user authenticates, the system checks both the new SID and any SIDs in sIDHistory, ensuring the user’s access rights are maintained across domain boundaries.

Summary of Differences

| Attribute         | GUID                                                   | SID                                                              |
|:-----------------:|:------------------------------------------------------:|:----------------------------------------------------------------:|
| Uniqueness        | Globally unique across AD domains                      | Unique within the domain                                         |
| Persistence       | Stays the same unless the object is deleted            | Changes when the object moves to another domain                  |
| Usage             | Identifies objects in global catalogs and applications | Used in access control and ACLs                                  |
| Storage Attribute | objectGUID                                             | objectSid                                                        |
| sIDHistory        | Not applicable                                         | Stores previous SIDs when migrating between domains              |

Understanding GUIDs and SIDs is critical for managing and securing AD objects. GUIDs ensure consistent identification across domains, while SIDs enable secure access control within and between domains, supporting AD’s identity and access management structure.

## Distinguished Names in Active Directory

In Active Directory (AD), a Distinguished Name (DN) uniquely identifies an object by specifying its exact location within the directory’s hierarchical structure. Similar to a postal address that pinpoints a person’s location from country down to house number, a DN traces the object’s path within AD, starting from the root and moving through each level down to the object itself.

### Components of a Distinguished Name

A DN in Active Directory is built from three main naming attributes:

- Organization Name (O) or Organizational Unit Name (OU): The organization represents the root-level domain, and OU represents the object’s organizational unit (or container) within the directory. For example, if a user is in the “IT” department within “Sales,” the OUs might look like OU=Sales,OU=IT.

- Domain Component (DC): This attribute reflects the domain name and aligns with the DNS structure. If the DNS name for a domain is prblabs.ca, it’s represented as DC=prblabs,DC=ca.

- Common Name (CN): This refers to the individual object, such as a specific user or computer within the directory. For example, CN=John Smith uniquely identifies a user named John Smith.

### Example of a Distinguished Name

Suppose we have a user named John Smith in the prblabs.ca domain, located in the default Users container. The DN for this user would be:

```
CN=John Smith,CN=Users,DC=prblabs,DC=ca
```
Breaking this down:

- DC=prblabs,DC=ca: Specifies the domain prblabs.ca.

- CN=Users: Points to the Users container within the domain.

- CN=John Smith: Specifies the actual user object.

### Relative Distinguished Name (RDN)

An RDN is the portion of a DN that is unique within its immediate parent container. In the above example, CN=John Smith is the RDN within the CN=Users container. Active Directory allows duplicate RDNs (e.g., two objects named "John Smith"), but only if they reside in different containers. Within the same container, RDNs must be unique.

### How Distinguished Names and SIDs Differ

- Distinguished Name (DN): Reflects the hierarchical path to an object and changes if the object is moved to a different container (e.g., from one OU to another).

- Security Identifier (SID): A unique identifier tied to the domain. The SID remains unchanged as long as the object stays within the same domain, even if its DN changes.

### Example Scenario: Moving an Object

If you move the user "John Smith" from the IT OU to a new HR OU, the DN will update to reflect the new path:

CN=John Smith,OU=HR,DC=prblabs,DC=ca

While the DN changes due to the new location, the SID remains the same, as the object hasn’t left the domain. This allows AD to maintain a stable identity for the object while recognizing its new location.

Distinguished Names are essential for locating and managing objects within AD, helping applications and services retrieve specific objects by their unique paths.

## Active Directory Server Roles

Active Directory (AD) includes five main server roles, each serving a unique purpose within the AD environment. These roles can be installed and configured individually or together to create a comprehensive identity and access management solution.

### Active Directory Domain Services (AD DS)

AD DS is the foundational role of Active Directory, responsible for storing directory data and managing user, computer, and group information within a domain. It enables core functions like authentication, authorization, and directory-based management of network resources.

### PowerShell cmdlet to install AD DS:

```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```

### Active Directory Federation Services (AD FS)

AD FS enables single sign-on (SSO) across different organizations or applications, allowing users to access multiple systems with one set of credentials. It’s often used for cloud services, allowing secure identity federation between on-premises AD and external platforms.

### PowerShell cmdlet to install AD FS:

```
Install-WindowsFeature AD FS-Federation -IncludeManagementTools
```

### Active Directory Lightweight Directory Services (AD LDS)

AD LDS provides directory services without requiring a full AD DS deployment. It’s a lightweight, flexible option for applications that need directory services without integrating into a domain, commonly used in scenarios like web authentication and application-specific directories.

PowerShell cmdlet to install AD LDS:

```
Install-WindowsFeature ADLDS -IncludeManagementTools
```

### Active Directory Rights Management Services (AD RMS)

AD RMS protects sensitive information by applying usage restrictions, such as limiting who can view, edit, or print documents. It’s widely used to enforce data protection policies within organizations. AD RMS has two main subfeatures:

- AD Rights Management Server
- Identity Federation Support

PowerShell cmdlets to install AD RMS:

```
Install-WindowsFeature ADRMS -IncludeManagementTools
# Install all subfeatures:
Install-WindowsFeature ADRMS -IncludeAllSubFeature
```

### Active Directory Certificate Services (AD CS)

AD CS provides a public key infrastructure (PKI) for issuing and managing digital certificates, which secure communications and data encryption. AD CS includes multiple subroles, including:

- Certification Authority (CA)

- Certificate Enrollment Policy Web Service

- Certificate Enrollment Web Service

- Certification Authority Web Enrollment

- Network Device Enrollment Service

- Online Responder

### PowerShell cmdlet to install AD CS:

```
Install-WindowsFeature AD-Certificate -IncludeManagementTools
# Install specific subfeatures:
Install-WindowsFeature ADCS-Cert-Authority,ADCS-Web-Enrollment -IncludeManagementTools
```

### Additional PowerShell Commands

List Available Roles: To view all available roles and their names for PowerShell installation, use:

```
Get-WindowsFeature
```

- Include Management Tools: When installing a role, adding -IncludeManagementTools ensures that management tools for the role are installed.

Each of these roles can be installed and configured through Windows Server Manager or PowerShell on Windows Server versions from 2008 onward, including Windows Server 2022. These server roles enable AD to offer versatile and comprehensive solutions for identity management, authentication, and data protection across the network.