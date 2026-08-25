# MRI Safety Resolver v0.6

Federated MRI implant/device safety search and presentation tool.

## Architecture

- FDA/openFDA UDI/GUDID live search for device identity.
- Manufacturer/FDA primary-source adapters for supported device families.
- Live parsing of current MRI manuals/labeling for structured conditions.
- Manufacturer MRI portal links for unsupported families.
- Restricted official-source URL analyzer for manufacturer/FDA MRI manuals.
- Conflict handling: unresolved or conflicting evidence requires human review.

## Current primary-source adapters

- Boston Scientific ImageReady brady pacing systems, including ACCOLADE MRI L310/L311/L331.
- eCoin Model UUI using FDA-hosted labeling.

## Manufacturer portals linked

- Boston Scientific
- Medtronic
- Abbott
- BIOTRONIK

## Safety

This is decision support, not automatic clearance. Exact implanted system/components, current manufacturer labeling/IFU, facility MR policy, MRSO/MRMD review, and medical physics remain controlling. Do not enter patient PHI.
