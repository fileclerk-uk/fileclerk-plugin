---
name: check-company-filings
description: Check public UK company filing deadlines, inspect filed accounts and validate iXBRL with FileClerk.
---

# Check UK company filings

Every step works with no key. Use the MCP tools at `https://fileclerk.co.uk/mcp` (Streamable HTTP) or the REST calls; both give the same answers.

1. Find the company number. With only a name, call `search_companies` with `name`, or request `GET https://fileclerk.co.uk/api/v1/companies/search?q=<name>`. When several companies match, confirm with the user which one they mean before you report dates.
2. Read the deadlines. Call `get_company_deadlines` with `company_number`, or request `GET https://fileclerk.co.uk/api/v1/companies/{number}/deadlines?view=summary`.
3. Report `nearest` first, then every overdue and upcoming obligation with its due date and its source. Say which dates are estimates: an obligation with `basis` `estimate` or `inferred` is not a register fact, and its `estimate` text says why. `coverage.cannot_see` lists what FileClerk cannot read.
4. For filed figures, call `get_company_finances` with the same number, or request `GET https://fileclerk.co.uk/api/v1/companies/{number}/finances`. Report the period, the source and any figure that is `null`.
5. For a company that is not formed yet, call `calculate_deadlines` with its type and incorporation date.
6. To check an iXBRL document before filing, call `validate_accounts` with the XHTML text. Report the rejections and risks with their rules.

FileClerk is independent of Companies House and HMRC. A validation report does not submit a filing. More: [llms.txt](https://fileclerk.co.uk/llms.txt) and the [API documentation](https://fileclerk.co.uk/docs/api).
