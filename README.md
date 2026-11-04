# LinkSkills

The Link QC skill set, and a worked example of applying it end to end to one user story.

> **Private repository — client material.** The evidence folder holds a real QA run against a
> client's staging environment: internal host names, purchase order and ASN numbers, customer and
> warehouse names, and screenshots of live screens. It carries no passwords, tokens or cookies.
> Keep this repository private and do not add collaborators who are not entitled to the client's
> data.

## `skills/`

The 15 skills of the QA pipeline, as they were used:

| Skill | Purpose |
|---|---|
| `link-qc-1-generate-update-testing-structure` | Creates and audits the project's QA folder structure and `qa-manifest.json` |
| `link-qc-2-review-requirements` | Reviews a user story for gaps, writes the REQ document and the open questions |
| `link-qc-3-generate-manual-test-cases` | Designs the manual test cases, the TEST-DATA file and the rendered review page |
| `link-qc-3b-validate-manual-test-cases` | Validates the test cases live through the Playwright MCP server |
| `link-qc-3c-validate-manual-test-cases-cli` | The same, driven through the `playwright-cli` command line |
| `link-qc-4-publish-test-cases-azure` | Beautifies the approved cases and publishes them to Azure DevOps, then verifies by read-back |
| `link-qc-5-test-run-automation` | Generates Playwright page-object automation from the approved document and runs it |
| `link-qc-5b-test-run-manual-cli` | Executes every test case manually through `playwright-cli` and writes the run report set |
| `link-qc-6-ui-testing` | Visual UI audit against a design reference |
| `link-qc-7-sync-tc-status-to-azure` | Writes run results back onto the published Azure DevOps test cases |
| `link-qc-8-sync-bugs-azure` | Pushes the bug report entries into Azure DevOps |
| `link-qc-9-retesting` | Retests open bugs after a fix |
| `link-qc-10-white-box-testing` | Audits the implementation in code against a requirement |
| `link-qc-11-discover-business-rules` | Exports business rules discovered in code as a spec gap list |
| `link-qc-12-adhd-output-style` | An output style for the assistant's responses |

## `evidence/`

One folder per story worked with the skills.

- [`US-234822-hajj-w2c1-6000-notification/`](evidence/US-234822-hajj-w2c1-6000-notification/) —
  a notice shown to suppliers when they choose a particular delivery destination. Taken from
  requirement review through test design, live validation, publication to Azure DevOps and a full
  manual test run.

Each story folder has its own README describing which skill produced which file, and what the
outcome was at each stage.
