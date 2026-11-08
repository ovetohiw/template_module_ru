# Scenario: protected home

## Happy path

1. Authenticated user opens `/` (or home) → protected home content visible.

## Failures

- Anonymous user opens home → redirected to login; no protected content.
