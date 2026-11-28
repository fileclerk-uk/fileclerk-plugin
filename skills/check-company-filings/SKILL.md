---
name: check-company-filings
description: Check public UK company filing deadlines, inspect filed accounts and validate iXBRL with FileClerk.
---

# Check UK company filings

Every step works with no key. Use the MCP tools at `https://fileclerk.co.uk/mcp` (Streamable HTTP) or the REST calls; both give the same answers. A free FileClerk account (OAuth, or a FileClerk API key as the `x-api-key` header; see https://fileclerk.co.uk/auth.md) raises the limit and adds every other tool at `https://fileclerk.co.uk/mcp/account`.

1. Find the company number. With only a name, call `search_companies` with `name`, or request `GET https://fileclerk.co.uk/api/v1/companies/search?q=<name>`. When several companies match, confirm with the user which one they mean before you report dates.
2. Read the deadlines. Call `get_company_deadlines` with `company_number`, or request `GET https://fileclerk.co.uk/api/v1/companies/{number}/deadlines?view=summary`.
3. Report `nearest` first, then every overdue and upcoming obligation with its due date and its source. Say which dates are estimates: an obligation with `basis` `estimate` or `inferred` is not a register fact, and its `estimate` text says what it assumes. A payroll row (`applies_if`) holds only if the company runs a payroll; `nearest_conditional` holds its next date. When a payment has `effective_due_on`, it must reach HMRC by that working day, though a Faster Payment or a card payment still counts on `due_on`. `coverage.cannot_see` lists what FileClerk cannot read.
4. For filed figures, call `get_company_finances` with the same number, or request `GET https://fileclerk.co.uk/api/v1/companies/{number}/finances`. Report the period, the source and any figure that is `null`.
5. For a company that is not formed yet, call `calculate_deadlines` with its type and incorporation date.
6. To check an iXBRL document before filing, call `validate_accounts` with the XHTML text. Report the rejections and risks with their rules.
7. For a community interest company's accounts package, call `prepare_cic_package` with the company number, the director-approved accounts as XHTML text and the CIC34 answers. Report each finding that is not pass to the person with its rule: a reject or not_evaluated finding stops the package (`ready` false), and a risk finding is one they should check before they upload. When `ready` is true, give the person the ZIP from `zip` and the `human_step`: they upload it at Companies House and pay the fee there.

FileClerk is independent of Companies House and HMRC. A validation report does not submit a filing. FileClerk's deadlines, tax figures and checks are general information, not professional tax, accounting or legal advice. More: [llms.txt](https://fileclerk.co.uk/llms.txt) and the [API documentation](https://fileclerk.co.uk/docs/api).
