# Version Selection Strategies

This guide explains the three supported version selection strategies used in the remediation system to help you choose the most appropriate approach for addressing your security vulnerabilities.

When vulnerabilities are detected in your dependencies, the remediation system can suggest updated versions to fix these security issues. The system offers three different strategies, each with its own approach to selecting the best candidate version from available options.

### Vulnerability Risk Scoring

Each candidate version receives a risk score based on its vulnerabilities using a weighted system that reflects the real-world impact of different severity levels:

| Severity | Score  |
| -------- | ------ |
| Low      | 1      |
| Medium   | 10     |
| High     | 100    |
| Critical | 10,000 |

The total score for a candidate is the sum of all its vulnerability scores. This scoring system ensures that critical vulnerabilities are treated with the urgency they deserve, while still accounting for the cumulative effect of multiple lower-severity issues.

### Strategy 1: Quickest Fix Strategy

Purpose: Chooses the nearest available secure version that resolves the vulnerability, requiring the smallest upgrade step from your current version.

#### How it Works

* Finds the closest semantic version that is newer than your current version.
* Prioritizes minimal version changes to reduce the risk of breaking changes.
* Only considers versions that are actually newer than your current version.

#### When to Use

* Development environments where you want to minimize disruption.
* Critical production systems where stability is paramount.
* Legacy codebases that may be sensitive to major version changes.
* When you need a quick, low-risk fix for security vulnerabilities.

#### Example

If you're using version 3.4.5 and have candidates 3.4.6, 3.4.7, and 3.4.8, this strategy will select 3.4.6 as it's the closest upgrade.

### Strategy 2: Least Vulnerable Fix Strategy

Purpose: Chooses the upgrade version that minimizes residual vulnerabilities, selecting the candidate with the lowest overall security risk.

#### How it Works

* Calculates a risk score for each candidate using the vulnerability scoring system described above.
* Among candidates with the same lowest score, selects the closest semantic version.
* Prioritizes security over version proximity.

#### When to Use

* Security-focused environments where vulnerability reduction is the top priority.
* Compliance requirements that mandate the lowest possible risk.
* When you have multiple versions with similar security profiles and want the safest option.
* Production systems where security takes precedence over minimal version changes.

#### &#x20;Example

You're currently using version 3.4.4 and have these candidates:

* Version 4.2.0: 1 Medium vulnerability (10 points) + 1 High vulnerability (100 points) = 110 points
* Version 3.4.5: 1 Critical vulnerability (10,000 points) = 10,000 points
* Version 5.3.1: 1 Medium vulnerability (10 points) + 1 High vulnerability (100 points) + 1 Low vulnerability (1 point) = 111 points
* Version 4.2.1: 1 Medium vulnerability (10 points) + 1 High vulnerability (100 points) = 110 points

The strategy will select Version 4.2.0 (110 points) because it has the lowest risk score, despite being a larger version jump than 3.4.5. If multiple versions had the same lowest score (like 4.2.0 and 4.2.1 both at 110 points), it would choose the one closest to your current version.

### Strategy 3: Best Version Strategy

Purpose: Chooses the upgrade version that provides the best overall balance of security improvement, compliance with organizational policies, and minimal risk of breaking changes.

#### How it Works

The Best Version Strategy uses a four-tier priority system to make intelligent decisions. It first looks for policy-approved, non-breaking versions and selects the least vulnerable among them. If none exist, it falls back to policy-approved breaking versions, then non-policy-approved non-breaking versions, and finally non-policy-approved breaking versions. Within each tier, it always chooses the version with the lowest vulnerability risk score. This approach ensures that your organization's policies are respected while maintaining security as the primary concern within each priority level.

#### When to Use

* Enterprise environments with established security policies.
* Complex applications where both security and stability matter.
* Organizations with compliance requirements that need policy adherence.
* Production systems that need to balance multiple competing priorities.

#### Example

If candidate versions are policy-approved and non-breaking, this strategy prioritizes them over policy-approved versions with breaking changes. Policy-approved versions are always preferred over non-policy-approved ones, regardless of their security scores

#### Detailed Example

You're currently using version 4.1.1 and have these candidates:

* Version 4.2.0: 1 High vulnerability (100 points), policy-approved, non-breaking
* Version 5.0.0: 1 Medium vulnerability (10 points), policy-approved, breaking
* Version 4.2.2: 2 Medium vulnerabilities (20 points total, including CVE-2025-12345), not policy-approved, non-breaking

Your organization's curation policy automatically rejects any version containing CVE-2025-12345, making version 4.2.2 non-policy-approved despite having a lower vulnerability score than 4.2.0. The strategy processes candidates in priority order:

Even though 4.2.2 has a lower vulnerability score (20 points vs 100 points), it's not policy-approved due to the forbidden CVE, so it's never considered. The strategy prioritizes policy compliance over perfect security scores.

### Important Notes

* Requires Policy Approval requires JFrog Curation
* All strategies only consider versions that are newer than your current version.
* The remediation mechanism only selects the latest 100 versions to prioritize from. If a package has more than 100 newer versions than the current one, partial results may happen.
* Policy Approval Check requires JFrog Curation Policies to be enabled, activated, and in full coverage of remote repositories.
