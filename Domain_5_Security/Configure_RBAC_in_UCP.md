# Configure RBAC in UCP



## Official Docker Documentation
[Access control model](https://docs.docker.com/datacenter/ucp/2.2/guides/access-control/)

[Tutorial: Role Based Access Control in Universal Control Plane](https://blog.docker.com/2016/03/role-based-access-control-docker-ucp-tutorial/)

## Third Party Resources
[Enforcing Segregation of Duty With Docker UCP & DTR](https://www.contino.io/insights/enforcing-segregation-of-duty-access-control-with-docker-universal-control-plane-trusted-registry)

## Summary

### Grant

A grant is made up of a subject, a role, and a resource collection. A grant defines who (subject) has how much access (role) to a set of resources (collection).

### Subjects

A subject represents a user, team, or organization. A subject is granted a role for a collection of resources.

- **User** : A person that the authentication backend validates. You can assign users to one or more teams and one or more organizations.
- **Organization** : A group of users that share a specific set of permissions, defined by the roles of the organization.
- **Team** : A group of users that share a set of permissions defined in the team itself. A team exists only as part of an organization, and all of its members must be members of the organization. Team members share organization permissions. A team can be in one organization only.

### Roles

A role is a set of permitted API operations that you can assign to a specific subject and collection by using a grant. UCP administrators view and manage roles by navigating to the Roles page. see [Identity roles](./Identity_roles.md)

### Resource collections

Docker EE enables controlling access to swarm resources by using collections. A collection is a grouping of swarm cluster resources that you access by specifying a directory-like path.

Swarm resources that can be placed in to a collection include:

- Physical or virtual nodes
- Containers
- Services
- Networks
- Volumes
- Secrets
- Application configs