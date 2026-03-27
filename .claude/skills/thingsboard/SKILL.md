---
name: thingsboard-conventions
description: Development conventions and patterns for thingsboard. Java project with freeform commits.
---

# Thingsboard Conventions

> Generated from [dyzmj/thingsboard](https://github.com/dyzmj/thingsboard) on 2026-03-27

## Overview

This skill teaches Claude the development patterns and conventions used in thingsboard.

## Tech Stack

- **Primary Language**: Java
- **Architecture**: hybrid module organization
- **Test Location**: mixed
- **Test Framework**: jest

## When to Use This Skill

Activate this skill when:
- Making changes to this repository
- Adding new features following established patterns
- Writing tests that match project conventions
- Creating commits with proper message format

## Commit Conventions

Follow these commit message conventions based on 200 analyzed commits.

### Commit Style: Free-form Messages

### Message Guidelines

- Average message length: ~56 characters
- Keep first line concise and descriptive
- Use imperative mood ("Add feature" not "Added feature")


*Commit message example*

```text
UI: Use explicit null check in onOptionSelected to handle falsy values
```

*Commit message example*

```text
fix: license headers
```

*Commit message example*

```text
Merge pull request #15316 from thingsboard/rc
```

*Commit message example*

```text
Merge remote-tracking branch 'origin/lts-4.3' into rc
```

*Commit message example*

```text
Merge remote-tracking branch 'origin/lts-4.2' into lts-4.3
```

*Commit message example*

```text
Merge pull request #15309 from thingsboard/fix/tb-dockerfiles
```

*Commit message example*

```text
Merge pull request #15315 from thingsboard/fix/cves
```

*Commit message example*

```text
Bump netty-bom from 4.1.131.Final to 4.1.132.Final to fix CVE-2026-33870 and CVE-2026-33871
```

## Architecture

### Project Structure: Single Package

This project uses **hybrid** module organization.

### Configuration Files

- `.github/workflows/check-configuration-files.yml`
- `.github/workflows/license-header-format.yml`
- `docker/docker-compose.yml`
- `msa/edqs/docker/Dockerfile`
- `msa/js-executor/docker/Dockerfile`
- `msa/js-executor/package.json`
- `msa/js-executor/tsconfig.json`
- `msa/monitoring/docker/Dockerfile`
- `msa/tb-node/docker/Dockerfile`
- `msa/tb/docker-cassandra/Dockerfile`
- `msa/tb/docker-postgres/Dockerfile`
- `msa/transport/coap/docker/Dockerfile`
- `msa/transport/http/docker/Dockerfile`
- `msa/transport/lwm2m/docker/Dockerfile`
- `msa/transport/mqtt/docker/Dockerfile`
- `msa/transport/snmp/docker/Dockerfile`
- `msa/vc-executor-docker/docker/Dockerfile`
- `msa/web-ui/docker/Dockerfile`
- `msa/web-ui/package.json`
- `msa/web-ui/tsconfig.json`
- `ui-ngx/package.json`
- `ui-ngx/tailwind.config.js`
- `ui-ngx/tsconfig.json`

### Guidelines

- This project uses a hybrid organization
- Follow existing patterns when adding new code

## Code Style

### Language: Java

### Naming Conventions

| Element | Convention |
|---------|------------|
| Files | PascalCase |
| Functions | camelCase |
| Classes | PascalCase |
| Constants | SCREAMING_SNAKE_CASE |

### Import Style: Relative Imports

### Export Style: Named Exports


*Preferred import style*

```typescript
// Use relative imports
import { Button } from '../components/Button'
import { useAuth } from './hooks/useAuth'
```

*Preferred export style*

```typescript
// Use named exports
export function calculateTotal() { ... }
export const TAX_RATE = 0.1
export interface Order { ... }
```

## Testing

### Test Framework: jest

### File Pattern: `*.spec.ts`

### Test Types

- **Unit tests**: Test individual functions and components in isolation


*Test file structure*

```typescript
import { describe, it, expect } from 'jest'

describe('MyFunction', () => {
  it('should return expected result', () => {
    const result = myFunction(input)
    expect(result).toBe(expected)
  })
})
```

## Error Handling

### Error Handling Style: Try-Catch Blocks


*Standard error handling pattern*

```typescript
try {
  const result = await riskyOperation()
  return result
} catch (error) {
  console.error('Operation failed:', error)
  throw new Error('User-friendly message')
}
```

## Common Workflows

These workflows were detected from analyzing commit patterns.

### Feature Development

Standard feature implementation workflow

**Frequency**: ~3 times per month

**Steps**:
1. Add feature implementation
2. Add tests for feature
3. Update documentation

**Files typically involved**:
- `**/*.test.*`
- `**/api/**`

**Example commit sequence**:
```
Add per-format packaging skip flags (pkg.skip.bootjar/deb/rpm/zip)
Replace Spotify dockerfile-maven-plugin with exec-maven-plugin
Fix black-box-tests docker-info dependency resolution
```

### Merge Release Branches

Synchronizes changes between release branches (e.g., merging lts-4.2 into lts-4.3, rc into master) to keep branches up to date.

**Frequency**: ~8 times per month

**Steps**:
1. Create a merge commit from source branch into target branch.
2. Resolve any conflicts if necessary.
3. Update common build files (e.g., pom.xml, build.sh, gradle files) and documentation if affected.
4. Push the merge commit.

**Files typically involved**:
- `pom.xml`
- `application/pom.xml`
- `build.sh`
- `edqs/pom.xml`
- `monitoring/pom.xml`
- `msa/*/pom.xml`
- `msa/transport/*/pom.xml`
- `msa/web-ui/pom.xml`
- `packaging/java/build.gradle`
- `packaging/js/build.gradle`
- `transport/*/pom.xml`
- `TEST_FAST.md`

**Example commit sequence**:
```
Create a merge commit from source branch into target branch.
Resolve any conflicts if necessary.
Update common build files (e.g., pom.xml, build.sh, gradle files) and documentation if affected.
Push the merge commit.
```

### Security Cve Fix Java Dependencies

Updates Java dependencies to fix reported CVEs (security vulnerabilities) by bumping versions in Maven POM files.

**Frequency**: ~4 times per month

**Steps**:
1. Identify affected dependencies (e.g., netty, jackson, Spring Boot, jedis, snakeyaml).
2. Update the version in pom.xml (and possibly module pom.xml files).
3. Commit with a message referencing the CVE(s).
4. Merge into relevant branches.

**Files typically involved**:
- `pom.xml`
- `common/transport/transport-api/src/main/java/org/thingsboard/server/common/transport/config/ssl/SslCredentialsWebServerCustomizer.java`

**Example commit sequence**:
```
Identify affected dependencies (e.g., netty, jackson, Spring Boot, jedis, snakeyaml).
Update the version in pom.xml (and possibly module pom.xml files).
Commit with a message referencing the CVE(s).
Merge into relevant branches.
```

### Feature Or Fix Across Ui And Backend

Implements a new feature or bugfix that requires coordinated changes across backend Java code, SQL schema, and Angular UI.

**Frequency**: ~2 times per month

**Steps**:
1. Update or add Java backend classes (e.g., data models, DAOs, services).
2. Update SQL schema or migration scripts if needed.
3. Update or add Angular UI components, models, and services.
4. Update UI assets and localization files.
5. Update or add tests (Java and/or Angular).
6. Update documentation/help files.

**Files typically involved**:
- `application/src/main/java/org/thingsboard/server/**/*.java`
- `common/data/src/main/java/org/thingsboard/server/common/data/**/*.java`
- `dao/src/main/java/org/thingsboard/server/dao/**/*.java`
- `dao/src/main/resources/sql/*.sql`
- `ui-ngx/src/app/**/*.ts`
- `ui-ngx/src/app/**/*.html`
- `ui-ngx/src/app/**/*.scss`
- `ui-ngx/src/assets/help/**/*.md`
- `ui-ngx/src/assets/locale/*.json`
- `ui-ngx/yarn.lock`

**Example commit sequence**:
```
Update or add Java backend classes (e.g., data models, DAOs, services).
Update SQL schema or migration scripts if needed.
Update or add Angular UI components, models, and services.
Update UI assets and localization files.
Update or add tests (Java and/or Angular).
Update documentation/help files.
```

### Dockerfile Improvement

Makes improvements or fixes to Dockerfiles for various microservices, such as adding dependencies or updating base images.

**Frequency**: ~2 times per month

**Steps**:
1. Edit Dockerfile(s) for the affected microservices.
2. Update installation scripts or base image references.
3. Commit with a message describing the Dockerfile change.

**Files typically involved**:
- `msa/tb/docker-cassandra/Dockerfile`
- `msa/tb/docker-postgres/Dockerfile`

**Example commit sequence**:
```
Edit Dockerfile(s) for the affected microservices.
Update installation scripts or base image references.
Commit with a message describing the Dockerfile change.
```

### Maven Plugin Or Build System Upgrade

Upgrades or replaces Maven plugins or build system logic across multiple modules to ensure compatibility or improve build reliability.

**Frequency**: ~2 times per month

**Steps**:
1. Identify affected Maven plugins (e.g., dockerfile-maven-plugin).
2. Update plugin configuration in all relevant pom.xml files.
3. Test build and packaging.
4. Commit and document the change.

**Files typically involved**:
- `msa/*/pom.xml`
- `msa/transport/*/pom.xml`
- `msa/vc-executor-docker/pom.xml`
- `msa/web-ui/pom.xml`
- `pom.xml`

**Example commit sequence**:
```
Identify affected Maven plugins (e.g., dockerfile-maven-plugin).
Update plugin configuration in all relevant pom.xml files.
Test build and packaging.
Commit and document the change.
```


## Best Practices

Based on analysis of the codebase, follow these practices:

### Do

- Write tests using jest
- Follow *.spec.ts naming pattern
- Use PascalCase for file names
- Prefer named exports

### Don't

- Don't skip tests for new features
- Don't deviate from established patterns without discussion

---

*This skill was auto-generated by [ECC Tools](https://ecc.tools). Review and customize as needed for your team.*
