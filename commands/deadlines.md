---
description: Show the filing deadlines of a UK company
argument-hint: <company name or number>
---

Show the filing deadlines of this UK company with the FileClerk tools: $ARGUMENTS

1. If the text is not a company number, call `search_companies` with the name. If more than one company matches, ask which one the person means.
2. Call `get_company_deadlines` with the company number.
3. Give the nearest date first. Then give each overdue and each upcoming deadline with its due date and its source.
4. Say which dates are estimates. A deadline with `basis` `estimate` or `inferred` is not a register fact.
5. End with the link to the company's FileClerk page (`url` in the answer).
