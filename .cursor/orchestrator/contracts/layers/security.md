# Layer payload: security

```text
must: []                 # blocking; also written into FEATURE Security must
should: []               # also written into FEATURE Security should
feature_security_updated: true|false
blocked_reason:          # if verdict=blocked
refs: []                 # case artifact paths only — never modules/*/conventions
```

Conventions stay in security module. Case SoR for downstream = FEATURE Security section + this payload, not convention file relay.
