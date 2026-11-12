# GitHub Catch-Up Digest — Hezi Liu

> Generated after two weeks offline at a conference. Covers: account identity & teams, notifications, security check on the `requests` library, and a sweep of repositories under the `HeziLiu` account.

---

## 1. Account Identity & Organization Teams

- **Login:** `HeziLiu` (Hezi Liu) — https://github.com/HeziLiu
- **User ID:** 28861483
- **Name on profile:** Hezi Liu
- **Company:** BUPT/GZU · **Location:** Beijing/Guiyang
- **Email on profile:** tackic@icloud.com
- **Account created:** 2017-05-22 · **Public repos:** 4 · **Followers:** 6 · **Following:** 5
- **Organization membership:** `mcpmark-eval-liuhezi`
- **Organization teams:** **None.** The team membership list for this account is empty — you are a member of the org `mcpmark-eval-liuhezi` but are **not currently on any organization team**. Stated plainly: no team memberships exist at this time.

---

## 2. Notifications

The notifications API is not accessible with the current personal access token (`403 Resource not accessible by personal access token`), so the inbox could not be enumerated directly via API. What could be determined:

- **Auto/bot chatter to mute:** CI pings, Dependabot/security-alert notifications, and automated Copilot review requests are the typical automated noise. Since the inbox couldn't be listed, mute those thread subscriptions manually in the GitHub UI (watch → ignore) if they keep winding up.
- **What genuinely needs a human (found via search):**
  - **`mcpmark-eval-liuhezi/tooling-triage-sandbox-11` #2 — "Expand triage runbook"** (opened 2026-11-12): adds `docs/security-watch.md` extending the triage runbook with a real upstream code-scanning alert lookup. Has 1 conversation comment and is awaiting review. → **Needs human review.**
  - **`mcpmark-eval-liuhezi/copilot-review-pilot` #7 — "Add AUDIT.md recording Node.js v20.0.0 pin and target commit SHA"** (opened 2026-11-12): supplies chain-of-custody values (tag `v20.0.0`, commit `e7618fb5a5fc`, SHA-256 digest) for an upstream supply-chain pin audit. An automated Copilot review is requested here. → **Needs human + Copilot review.**
  - **`mcpmark-eval-liuhezi/release-security-audit` #26/#27/#28/#29 — "Add SECURITY_AUDIT.md"**: a security compliance audit report for the HeziLiu account (per-repo findings: no releases, no repository security advisories, no open PRs; secret scanning status flagged as unverified due to token scope). → **Needs human review before Friday.**
- **Bottom line:** treat org repo notifications as the human-actionable inbox; direct API inbox listing is blocked by token scope.

---

## 3. Security Check: `requests` Library Advisories

The lab pip-installs `requests` everywhere, and your half-memory is right — there *has* been a real flash of advisories. The global advisory database returns 8 reviewed advisories affecting `requests` (pip ecosystem). The **most severe** one is:

### Most Severe Advisory

| Field | Value |
| --- | --- |
| **Advisory ID** | **GHSA-x84v-xcm2-53pg** |
| **CVE** | **CVE-2018-18074** |
| **Severity** | **High** (CVSS 3.1 score: 7.5 — `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N`) |
| **CWES** | CWE-522 (Insufficiently Protected Credentials) |
| **Vulnerable version range** | **<= 2.19.1** |
| **First fixed version** | **2.20.0** |
| **Summary** | Insufficiently Protected Credentials in Requests: through 2.19.1, the package sent an HTTP `Authorization` header to an `http` URI upon receiving a same-hostname https-to-http redirect, letting remote attackers discover credentials by sniffing the network. |
| **Remediation** | Upgrade to `requests` >= 2.20.0. If stuck on older versions, avoid redirects to http origins and set `trust_env=False` on your Session. |
| **Link** | https://github.com/advisories/GHSA-x84v-xcm2-53pg |

### Other notable advisories (for context)

| Advisory ID | CVE | Severity | Vulnerable range | First fixed |
| --- | --- | --- | --- | --- |
| GHSA-gc5v-m9x4-r6x2 | CVE-2026-25645 | Medium | < 2.33.0 | 2.33.0 (temp file reuse in `extract_zipped_paths()`) |
| GHSA-9hjg-9r4m-mvj7 | CVE-2024-47081 | Medium | < 2.32.4 | 2.32.4 (.netrc credential leak via malicious URLs) |
| GHSA-9wx4-h78v-vm56 | CVE-2024-35195 | Medium | < 2.32.0 | 2.32.0 (Session verify=False persistence) |
| GHSA-j8r2-6x86-q33q | CVE-2023-32681 | Medium | >= 2.3.0, < 2.31.0 | 2.31.0 (Proxy-Authorization header leak on redirects) |
| GHSA-cfj3-7x9c-4p3h | CVE-2014-1829 | Medium | < 2.3.0 | 2.3.0 (.netrc password leak) |
| GHSA-652x-xj99-gmcc | CVE-2014-1830 | Medium | < 2.3.0 | 2.3.0 (Proxy-Authorization leak) |
| GHSA-pg2w-x9wp-vw92 | CVE-2015-2296 | Medium | >= 2.1.0, < 2.6.0 | 2.6.0 (Session fixation) |

**Lab takeaway:** anything pinned at `requests` <= 2.19.1 should be bumped to at least 2.20.0; 2.32.4+ covers the later netrc/redirect classes of issues.

---

## 4. Repository Sweep (under `HeziLiu`)

Two non-fork repositories exist on the account: **Little-rookie** (Java, undergraduate coursework) and **Big-Buzzard** ("For future...."). Both were checked explicitly — not skipped.

### `HeziLiu/Little-rookie` (Java, default branch `master`, last updated 2019-06-02)
- **Open pull requests:** **None.** (`list_pull_requests` state=open returned empty.)
- **Workflow activity:** **None.** (`list_workflows` → total_count: 0. No CI configured.)
- **Status:** **nothing doing** — repo checked, no open PRs, no workflows.

### `HeziLiu/Big-Buzzard` (default branch `master`, last updated 2018-05-17, 1 fork)
- **Open pull requests:** **None.** (`list_pull_requests` state=open returned empty.)
- **Workflow activity:** **None.** (`list_workflows` → total_count: 0. No CI configured.)
- **Status:** **nothing doing** — repo checked, no open PRs, no workflows.

### Activity in your organization (`mcpmark-eval-liuhezi`) — repos you actually have open PRs in

| Repository | PR # | Title | Mergeable | Reviews | Latest workflow run on branch |
| --- | --- | --- | --- | --- | --- |
| `tooling-triage-sandbox-11` | #2 | Expand triage runbook | ✅ Yes (`mergeable: true`, state `clean`) | 0 review comments; 1 conversation comment — awaiting review | **No workflow** (total_count: 0) |
| `copilot-review-pilot` | #7 | Add AUDIT.md recording Node.js v20.0.0 pin and target commit SHA | ✅ Yes (`mergeable: true`, state `clean`) | 0 reviews yet; automated Copilot review requested | **No workflow** (total_count: 0) |
| `release-security-audit` | #26, #27, #28, #29 | Add SECURITY_AUDIT.md (security compliance audit report) | Newly opened, not yet evaluated | Not yet reviewed | **No workflow** (none defined) |

---

## 5) Highlights for the Group Sync

- **It's really your account:** `HeziLiu` (Hezi Liu), ID 28861483, https://github.com/HeziLiu. You're a member of org `mcpmark-eval-liuhezi` but **on zero organization teams**.
- **Inbox caveat:** the API token can't list notifications directly (403), so mute CI/bot threads manually in the UI; the human items are the open PRs in `tooling-triage-sandbox-11` (#2), `copilot-review-pilot` (#7), and `release-security-audit` (#26–#29).
- **Security:** the worst `requests` advisory is **GHSA-x84v-xcm2-53pg / CVE-2018-18074** (High, CVSS 7.5) affecting **<= 2.19.1**, fixed in **2.20.0**. Current 2.33.0+ covers everything since.
- **Your own repos:** `Little-rookie` and `Big-Buzzard` both have **no open PRs and no CI workflows** — nothing doing on either, confirmed by explicit checks.
- **Action items:** (1) bump any pinned `requests` <= 2.19.1 to >= 2.20.0 (ideally 2.32.4+); (2) review the 3–4 open PRs in the org repos; (3) grant a PAT with `security_events` scope to verify secret-scanning status manually.

---

*Digest generated via GitHub MCP tools. Posted as a private file (`github-catchup-digest.md`) in `mcpmark-eval-liuhezi/heziLiu-docs` since the token lacks the `gist` scope.*
