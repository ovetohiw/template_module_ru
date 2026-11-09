# Layer payload: security

```text
must: []                 # блокирующие; также пишутся в FEATURE Security must
should: []               # также пишутся в FEATURE Security should
feature_security_updated: true|false
blocked_reason:          # если verdict=blocked
refs: []                 # только пути артефактов кейса — никогда modules/*/conventions
```

Conventions остаются в модуле security. Case SoR для downstream = секция FEATURE Security + этот payload, не relay convention-файлов.
