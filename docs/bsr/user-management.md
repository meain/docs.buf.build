---
id: user-management
title: User Management
---

# User Management

## Organization Roles

Every user that is part of an organization will have an explicit role. Note that users are unable to modify their own role. If you need to lower your access please have another organization user perform this action, or, leave the organization and request to be re-added with the desired role.
	
### Owner

- Users that require unrestricted access to the organization, its settings and all resources owned by the organization. 
- Can delete organization. All resources such as repositories, templates and plugins must be deleted before the organization can be deleted.

### Admin

- Can manage user roles, except owners.
- Can add and delete resources such as [repositories](../bsr/overview.md#module), [templates](../bsr/remote-generation/concepts/#template) and [plugins](../bsr/remote-generation/concepts/#plugin).

### Member

- Can view the organization and its members.
- Have the [Base resource role](#base-resource-roles) over the organizations resources, which defaults to [Write](#write).

### Base resource roles

> *Configurable base resource roles are coming soon.*

Every organization has a set of base resource roles that apply to all members of the organization. The following are the default roles:

| Repository | Template | Plugin |
|:--|:--|:--|
| **Write**  | **Write** | **Write** |

Organization owners can modify the base resource roles depending on the requirements of the organization.

## Resource Roles

> *Resource roles coming soon.*

Resources such as repositories, templates and plugins are owned by either an individual user or an organization. In the case of user-owned resources, the user is granted the `Owner` role and for organization-owned resources members inherit the [base resource roles](#base-resource-roles) as defined by the organization.

However, in some situations you'll need to give additional permissions to individual users over a user- or organization-owned resource.

The most common use-cases are:

- Outside collaborators. This is useful when users outside your organization require access to specific resource(s) within the organization, but you do not want them to be a member of the organization.
- Elevated permissions for organization members. This is useful when the organization base resource roles are set to **Read** and specific user(s) require the **Write** or **Admin** role for specific resource(s). 

When computing the role on a resource, the highest role will take precedence. For example, an organization has **Write** as the base repository role, and the user was granted the **Admin** role on a specific repository. The final computed user role on the repository will be **Admin**.

### Owner

- Unrestricted access to the resource.
- Can delete the resource.

### Admin

- Can update the resource settings and deprecation notices.
- Can manage resource roles, except owners.

### Write

- Can perform write operations on resources, such as:
  -  Pushing to a repository 
  -  Creating tags
  -  Updating template versions and plugins

### Read

- Can view the resource.