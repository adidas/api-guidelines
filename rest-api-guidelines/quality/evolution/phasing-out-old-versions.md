# Phasing out Old Versions

An older resource variant or action **MAY** be phased out and eventually removed providing clients were given enough time to accommodate for the change.

Whether a resource or action can be phased out and removed completely depends on the nature of the API and the importance of existing integrations. 

If an interface might be phased out it **MUST** follow the Phasing out Outline as specified in these guidelines. 

> The gist is to never break existing clients. As soon as there is a breaking change a new resource variant should be created leaving the original intact to not break existing integrations. However, over the time it might be desired to remove older, unused variants.

### Phasing out Outline

#### 1. Mark as Deprecated

The deprecation mark **SHOULD** happen both at runtime and in the documentation. 

For the runtime deprecation notice the  [HTTP Sunset Header](https://tools.ietf.org/id/draft-wilde-sunset-header-03.html) **MUST** be used. For the documentation, the resource or action **MUST** be clearly marked in its description as deprecated.

#### 2. Inform Users

Existing API users **MUST** be noticed by available means about the deprecation of the interface. They **SHOULD** be informed about what are the alternatives to using the deprecated functionality and what is the migration path.

#### 3. Remove Documentation of the Deprecated Interface

Eventually, the part of API documentation describing the deprecated interface **MAY** be removed or hidden to prevent new users from using the deprecated resources or actions. 

#### 4. Final Notice

After a sufficient grace period a final deprecation notice **SHOULD** be issued.

#### 5. Remove Deprecated Interface

When there are no users using the deprecated interface, the interface **MAY** be decommissioned. A deprecated resource or action **MUST NOT** be removed if there are known existing integrations using it.

Based one the nature of migration path a redirect to a new variant **SHOULD** be provided.

> Phasing-out, depends on the importance of the APIs and its audience, for business-critical APIs, one never want to risk removing anything. For example [Stripe.com](http://stripe.com/) maintain all past versions. For other, less critical APIs, or APIs where one control its client\(s\), one can be more relaxed about removing deprecated resources.

