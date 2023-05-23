## Federated Identity
The concept of a *centralized or linked electronic identity* is known as _federated identity_.

Federated identity systems handle several concerns:
-   Authentication
-   Authorization
-   User attributes exchange
-   User management

The **authentication** aspect deals with validating user credentials and establishing the identity of the user.

**Authorization** is related to access restrictions (e.g., is the user allowed to access X resource?).

The **attributes exchange** aspect deals with data sharing across different user management systems. For instance, fields such as _"real name"_ may be present in multiple systems. A federated identity system prevents data duplication by linking the related attributes.

Lastly, **user management** is related to the administration (creation, deletion, update) of user accounts. A federated identity system usually provides the means for administrators (or users) to handle accounts across domains or subsystems.

## Single Sign On (SSO)
*SSO* is strictly related to the **authentication** part of a federated identity system. Its only concern is establishing the identity of the user and then sharing that information with each subsystem that requires the data.

Different SSO protocols share session information in different ways, but the essential concept is the same: there is a **central domain**, through which authentication is performed, and then the **session is shared** with other domains in some way.