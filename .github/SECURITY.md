# Security Policy

This is the **default security policy** for [@aaronjmars](https://github.com/aaronjmars)
projects. It applies to any repository that doesn't ship its own `SECURITY.md`.
Repos with a heavier threat surface (wallets and on-chain funds, browser
automation, autonomous agents with your secrets) override this with a tailored
policy — read that one if it exists.

## Reporting a vulnerability

**Please don't open a public issue for a security problem.** Use GitHub's
**Private Vulnerability Reporting (PVR)** on the affected repository:

➡️ Go to the repo → **Security** tab → **Report a vulnerability**
(`https://github.com/aaronjmars/<repo>/security/advisories/new`).

This opens a private advisory that only the maintainers can see — never a public
issue, so a fix can ship before the details are out.

Please include what you can:

- The repository and the file/route/component affected (a path is ideal).
- A minimal reproduction or proof of concept.
- The impact you can demonstrate — secret or key disclosure, loss or misdirection
  of funds, remote code execution, prompt injection that crosses a trust boundary,
  SSRF, or unauthorized access.
- The commit/version and environment you tested against.

**Response targets** — best effort; these are small projects:

| Stage | Target |
|-------|--------|
| Acknowledge the report | within 7 days |
| Initial assessment / severity | within 14 days |
| Fix or mitigation | as fast as the severity warrants |

We follow **coordinated disclosure**: please give us a reasonable window to ship a
fix before you disclose publicly. We'll credit you in the advisory unless you'd
rather stay anonymous.

## Supported versions

Security fixes land on the `main` branch (and the latest published release/package,
where one exists). Pull `main` to receive them; older tags are not maintained.

## Security model

A couple of principles hold across these projects:

- **Instructions are trusted; external data is not.** Anything fetched from the web,
  scraped, or received over a channel (issues, messages, feeds, API responses,
  model output) is **data, not commands**. Content that steers an agent or tool via
  embedded instructions ("ignore previous instructions…") into tool use, data
  exfiltration, or unbounded spend is a vulnerability.
- **Secrets live in the environment, never in code.** API keys, tokens, and wallet
  keys come from env / a secret store and must never be committed, logged, or
  shipped to a third party. Anything reachable client-side that shouldn't be, or a
  path that exfiltrates a secret, is in scope.
- **Money and code execution are the high-severity bar.** Loss or misdirection of
  funds, signature/authorization abuse, and arbitrary code execution get triaged
  first.

## Scope

**In scope:** secret/key disclosure or exfiltration, fund loss or misdirection,
remote code execution, prompt injection that crosses a trust boundary, SSRF, XSS,
authentication/authorization bypass, and supply-chain issues in a project's release
pipeline.

**Out of scope:** your own misconfiguration (committed secrets, over-broad
permissions, exposing a service with no auth); vulnerabilities in third-party
dependencies or platforms (report those to the vendor); and output-quality issues
(a wrong answer is a bug — open a regular issue, not a security report).

---

> **Maintainers:** the private-reporting flow only works once PVR is enabled —
> **Settings → Code security and analysis → Private vulnerability reporting →
> Enable** — on each repository.

Thanks for helping keep these projects and the people who run them safe.
