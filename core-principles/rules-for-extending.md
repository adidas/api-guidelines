# Rules for Extending
Any modification to an existing API design MUST avoid breaking changes and MUST maintain backward compatibility.

In particular any change to an API design MUST follow the following Rules for Extending:

1. **You MUST NOT take anything away** (related: [Minimal Surface Principle](core-principles/minimal-api-surface.md)
, [Robustness Principle](core-principles/robustness.md))
2. **You MUST NOT change processing rules** 
3. **You MUST NOT make optional things required**
4. **Anything you add MUST be optional** (related [Robustness Principle](core-principles/robustness.md))


> NOTE: These rules covers also renaming and changes to identifiers (URIs). Names and identifiers should be stable over the time including their semantics.



