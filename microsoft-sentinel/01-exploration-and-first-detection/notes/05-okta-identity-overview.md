# Step 5 – Explore Okta Identity Events

## Objective

Analyze Okta identity events to understand authentication activity and identify unusual sign-in behavior.

## Query Used

[05-okta-identity-overview.kql](../queries/05-okta-identity-overview.kql)

## Key Findings

The most common identity events observed were:

| Event Type | Result | Count |
|------------|--------|------:|
| user.authentication.* | SUCCESS | 10 |
| policy.evaluate_sign_on | ALLOW | 9 |
| app.oauth2.token.* | SUCCESS | 7 |
| user.session.start | SUCCESS | 5 |
| user.account.privilege.* | SUCCESS | 1 |

The identity activity was primarily composed of successful authentication events and policy evaluations. No significant number of failed authentication attempts was observed during this stage of the investigation.

## Evidence

Screenshot:

`05-okta-identity-overview.png`
