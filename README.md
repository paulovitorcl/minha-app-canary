# minha-app-canary

Important note: When using header-based routing like X-Canary-Version: canary, the weight-based traffic
splitting works in addition to header routing:

- Requests with the canary header → Always go to canary (regardless of weight)
- Requests without the header → Follow the weight distribution between stable/canary

This gives you dual control:
1. Deterministic access via headers for testing
2. Gradual traffic shift via weights for real user traffic