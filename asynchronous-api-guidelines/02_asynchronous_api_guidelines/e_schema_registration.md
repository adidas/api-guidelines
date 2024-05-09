# adidas Asynchronous API guidelines

## Asynchronous API guidelines

### Automatic schema registration

Applications **MUST NOT** enable automatic registration of schemas because FDP's operational model for the Schema Registry relies on GitOps (every operation is done through GIT PRs + automated pipelines)