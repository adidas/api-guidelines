# Rules for Extending

Any modification to an existing API **MUST** avoid breaking changes and **MUST** maintain backward compatibility.

In particular, any change to an API **MUST** follow the following **Rules for Extending**:

1. **You MUST NOT take anything away** \(related: [Minimal Surface Principle](minimal-api-surface.md)

   , [Robustness Principle](robustness.md)\)

2. **You MUST NOT change processing rules** 
3. **You MUST NOT make optional things required**
4. **Anything you add MUST be optional** \(related [Robustness Principle](robustness.md)\)

> NOTE: These rules cover also renaming and change to identifiers \(URIs\). Names and identifiers should be stable over the time including their semantics.

