---
name: sbom-license-compliance
description: Generates Software Bill of Materials (SBOM), audits open-source dependency licenses (GPL, AGPL, MIT, Apache), and prevents commercial licensing violations.
---

# SBOM & Open-Source License Compliance

This skill guides the automated generation of Software Bill of Materials (CycloneDX / SPDX formats) and audits dependency licenses to safeguard commercial software from copyright violations.

## 1. License Classification & Copyleft Detection

1. **Viral / Strong Copyleft (High Commercial Risk)**:
   - GPL-2.0, GPL-3.0, AGPL-3.0: Flag immediate alerts if used as linked dependencies in proprietary, closed-source commercial applications.
2. **Weak Copyleft (Conditional)**:
   - LGPL, MPL-2.0: Verify that modifications to library source code are published or dynamically linked.
3. **Permissive (Low Risk)**:
   - MIT, Apache-2.0, BSD-2/3-Clause, ISC: Verify standard copyright notice attribution in distribution bundles.

## 2. SBOM Generation & Pipeline Integration
- Generate machine-readable SBOM files (`bom.json` / `bom.xml`) compliant with CycloneDX 1.5 standards.
- Run license scanning checks in CI/CD before packaging production distribution builds.
