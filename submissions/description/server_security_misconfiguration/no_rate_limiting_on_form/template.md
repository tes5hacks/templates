# No Rate Limiting on Form

## Overview of the Vulnerability

Rate limiting is a strategy to limit the frequency of a repeat action within a particular time frame. This ensures that a service doesn’t become unresponsive or unavailable due to too many requests exhausting the application's resources. A lack of rate limiting on this endpoint allows an attacker to send a large number of requests to the server and potentially cause accelerated service usage for the business or exhaust the application resources.

## Business Impact

No rate limiting on a form can result in reputational damage to the organization if the rate limiting prevents legitimate form submissions and responses. It also has the potential to cause accelerated service usage, which can incur a direct financial cost in environments with SaaS services or pay on demand systems.

## Steps to Reproduce

1. Enable a HTTP intercept proxy, such as Burp Suite or OWASP ZAP, to record and intercept web traffic from your browser
1. Using a browser, sign into the application
1. Navigate to {{url}} and fill out the form
1. Submit the form while using the HTTP intercept proxy to intercept the request
1. Using the HTTP intercept proxy, re-issue the captured request 400 times in rapid succession
1. Observe within the HTTP intercept proxy that all 400 of these requests generate a ‘HTTP 200 OK’ response, showing that there is no rate-limiting on the form

## Proof of Concept

The following screenshot shows a lack of rate limiting on the form:

{{screenshot}}
