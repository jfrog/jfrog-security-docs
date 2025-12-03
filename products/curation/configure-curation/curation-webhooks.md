# Curation Webhooks

Includes events that are triggered when certain events occur in Curation. \
For more information on Webhooks general configuration in the JFrog platform, see [Webhooks](https://jfrog.com/help/r/jfrog-platform-administration-documentation/webhooks).&#x20;

**Event: Package was blocked by Curation**

The Webhook is triggered when Curation blocks a package.

**Package was Blocked**

```
{
    "package_type": "npm",
    "package_name": "vm2",
    "package_version": "3.9.1",
    "package_url": "https://registry.npmjs.org/vm2/-/vm2-3.9.1.tgz",
    "reason": "Policy violations",
    "curated_repository_server_name": "",
    "curated_repository_name": "remote-npm-repo",
    "curated_project": "origin-project",
    "username": "John Doe",
    "user_mail": "johnd@example.com",
    "origin_repository_server_name": "origin-server",
    "origin_repository_name": "origin-repo",
    "origin_project": "origin-project",
    "public_repo_url": "https://registry.npmjs.org",
    "public_repo_name": "npm registry",
    "policies": [
      {
        "policy_name": "Vulns",
        "policy_id": 84,
        "dry_run": false,
        "result": "Blocked",
        "condition_name": "Block Sev High",
        "condition_category": "security"
      }
    ],
    "event_id": 1234
}
```

**Event: Curation Waiver Request Created**

The webhook is triggered when a waiver request is created.

**Waiver Request Created**

```
{
    "waiver_request": {
        "id": 5,
        "created_at": "1739697682644",
        "closed_at": "",
        "repo_key": "npm-remote",
        "pkg_type": "npm",
        "pkg_name": "vm2",
        "pkg_version": "3.9.3",
        "status": "pending",
        "decision_owners": [
            "readers",
            "group2"
        ],
        "requesters": [
            {
                "user": "anonymous",
                "email": "test@jfrog.com",
                "requested_at": "",
                "justification": "reasons"
            }
        ],
        "policies": [
            {
                "id": 5,
                "name": "aged",
                "scope": "all_repos",
                "policy_action": "block",
                "condition_id": "13",
                "condition_name": "Package version is aged (newer version available)",
                "condition_category": "operational",
                "can_approve": false,
                "pkg_types_include": null,
                "decision_owners": [
                    "readers"
                ]
            },
            {
                "id": 7,
                "name": "policy2",
                "scope": "all_repos",
                "policy_action": "block",
                "condition_id": "13",
                "condition_name": "Package version is aged (newer version available)",
                "condition_category": "operational",
                "can_approve": false,
                "pkg_types_include": null,
                "decision_owners": [
                    "group2"
                ]
            }
        ]
    },
    "pkg_url": "https://test-env/ui/catalog/packages/details/npm/vm2/3.9.3"
}
```

**Event: Curation Waiver Request Updated**

The webhook is triggered when a waiver request was updated.

**Waiver Request Updated**

```
{
    "waiver_request": {
        "id": 3,
        "created_at": "2025-02-15T22:14:58+02:00",
        "closed_at": "",
        "repo_key": "npm-remote",
        "pkg_type": "npm",
        "pkg_name": "vm2",
        "pkg_version": "3.9.3",
        "status": "pending",
        "decision_owners": [
            "group2",
            "readers"
        ],
        "requesters": [
            {
                "user": "anonymous",
                "email": "test@mail.com",
                "requested_at": "2025-02-15T22:14:58+02:00",
                "justification": "reasons"
            }
        ],
        "policies": [
            {
                "id": 5,
                "name": "aged policy 1",
                "scope": "all_repos",
                "policy_action": "block",
                "condition_id": "13",
                "condition_name": "Package version is aged (newer version available)",
                "condition_category": "operational",
                "can_approve": true,
                "pkg_types_include": null,
                "decision_owners": [
                    "readers"
                ]
            },
            {
                "id": 7,
                "name": "aged policy 2",
                "scope": "all_repos",
                "policy_action": "block",
                "condition_id": "13",
                "condition_name": "Package version is aged (newer version available)",
                "condition_category": "operational",
                "can_approve": false,
                "pkg_types_include": null,
                "decision_owners": [
                    "group2"
                ]
            }
        ]
    },
    "decision": {
        "created_by": "admin",
        "created_at": "",
        "justification": "not relevant",
        "status": "approved"
    },
    "pkg_url": "https://test-env/ui/catalog/packages/details/npm/vm2/3.9.3",
    "decided_policies": [
        {
            "id": 5,
            "name": "aged policy 1"
        }
    ],
    "pending_policies": [
        {
            "id": 7,
            "name": "aged policy 2"
        }
    ]
}
```

**Event: Curation Policy Changed**

This webhook is triggered whenever the configuration of Curation policies is updated, including any changes to the policy conditions.

**A policy with one waiver was changed from a malicious condition to a critical vulnerability condition**.

```
{
    "curation_event_type": "Policy Updated",
    "policy_before": {
      "id": "20",
      "created_by": "admin",
      "updated_by": "admin",
      "created_at": "2025-03-23T16:26:01+02:00",
      "updated_at": "2025-03-23T16:26:32+02:00",
      "enabled": true,
      "name": "some policy name",
      "scope": "all_repos",
      "policy_action": "block",
      "condition_id": "1",
      "condition": {
        "id": "1",
        "is_custom": false,
        "created_at": "2023-08-01T03:00:00+03:00",
        "updated_at": "2023-08-01T03:00:00+03:00",
        "risk_type": "security",
        "supported_pkg_types": [
          "npm",
          "PyPI",
          "Maven",
          "Go",
          "NuGet",
          "Conan",
          "Gems",
          "Gradle",
          "HuggingFaceML",
          "Docker"
        ],
        "condition_template_id": "isMalicious",
        "name": "Malicious package"
      },
      "waivers": [
        {
          "id": "7",
          "pkg_type": "npm",
          "pkg_name": "jQuery",
          "all_versions": false,
          "pkg_versions": [
            "1.7.4"
          ],
          "justification": "something",
          "created_by": "admin",
          "created_at": "2025-03-23T16:26:24+02:00"
        }
      ],
      "waiver_request_config": "forbidden"
    },
    "policy_after": {
      "id": "20",
      "created_by": "admin",
      "updated_by": "admin",
      "created_at": "2025-03-23T16:26:01+02:00",
      "updated_at": "2025-03-23T16:26:39+02:00",
      "enabled": true,
      "name": "some policy name",
      "scope": "all_repos",
      "policy_action": "block",
      "condition_id": "3",
      "condition": {
        "id": "3",
        "is_custom": false,
        "created_at": "2023-08-01T03:00:00+03:00",
        "updated_at": "2023-08-01T03:00:00+03:00",
        "risk_type": "security",
        "supported_pkg_types": [
          "npm",
          "PyPI",
          "Maven",
          "Go",
          "NuGet",
          "Conan",
          "Gems",
          "Gradle"
        ],
        "condition_template_id": "CVECVSSRange",
        "name": "CVE with CVSS score of 9 or above (with or without a fix version available)",
        "param_values": [
          {
            "param_id": "vulnerability_cvss_score_range",
            "value": [9, 10]
          },
          {
            "param_id": "apply_only_if_fix_is_available",
            "value": false
          }
        ]
      },
      "waivers": [
        {
          "id": "7",
          "pkg_type": "npm",
          "pkg_name": "jQuery",
          "all_versions": false,
          "pkg_versions": [
            "1.7.4"
          ],
          "justification": "something",
          "created_by": "admin",
          "created_at": "2025-03-23T16:26:24+02:00"
        }
      ],
      "waiver_request_config": "forbidden"
    }
}
```
