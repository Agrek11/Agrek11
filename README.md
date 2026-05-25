# Hi, I'm Abhi

Backend / distributed-systems engineer, 7 years. Currently SSE at Guidewire.

Spending personal time on confidential computing — Confidential Containers, Kata, Trustee — as the wedge into confidential AI infrastructure.

---

## Open source

Contributing to CNCF Sandbox **Confidential Containers** and related projects from this account on personal time. Differentiator: I run POCs on a personal AWS scratch with AMD SEV-SNP enabled, so I hit real bugs that pure issue-scrapers miss.

### Merged

| Project | PR | What it does |
|---|---|---|
| `confidential-containers/cloud-api-adaptor` | [#3058](https://github.com/confidential-containers/cloud-api-adaptor/pull/3058) | IMDSv2 token fallback for AWS PodVM bootstrap. Unblocks SEV-SNP peer-pods on AWS orgs with SCP-enforced IMDSv2-only. Independently reproduced by another user in `#3068`. |
| `confidential-containers/cloud-api-adaptor` | [#3083](https://github.com/confidential-containers/cloud-api-adaptor/pull/3083) | Blacklist `vmgenid` driver init in mkosi kernel cmdline to fix AWS SEV-SNP boot hang on Fedora-based PodVMs. Zero-comment merge in same-day cycle. |

### In review

| Project | PR | What it does |
|---|---|---|
| `confidential-containers/guest-components` | [#1484](https://github.com/confidential-containers/guest-components/pull/1484) | Emit a `tracing::warn!` from `ocicrypt-rs::OcicryptConfig::from_env` when `OCICRYPT_KEYPROVIDER_CONFIG` is unset — closes a silent-failure gap that misroutes operators away from the actual root cause. |

[All merged PRs (auto-updating)](https://github.com/search?q=is%3Apr+author%3AAgrek11+is%3Amerged&type=pullrequests)

---

## Reach me

- GitHub: [Agrek11](https://github.com/Agrek11)
- Email via GitHub profile

<!--
Update protocol: after every merge, add the entry to the "Merged" table within 24h.
Source of truth for backstories: ../../obsidian-vault/Personal/Study/AI/CoCo/OSS-portfolio.md
-->
