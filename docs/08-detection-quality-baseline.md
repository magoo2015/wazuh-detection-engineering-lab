# Detection Quality Baseline – macOS Persistence Control

## Test Scenario
Legitimate LaunchAgent creation using benign echo command.

## Observed Behavior
- Alerts generated: 1
- Rule IDs triggered: 554
- Alert levels: 5

## Stability Observations
Stable fields:
- path
- filename
- rule.description

Variable fields:
- timestamp
- syscheck.diff

## Noise Characteristics
- Expected alerts per modification: 1
- Analyst impact: Low / Moderate / High

## Engineering Notes
This control generates predictable alerts during legitimate system changes.
Noise level considered acceptable for investigative visibility.
