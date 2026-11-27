---
description: Show the filing deadlines of a UK company
argument-hint: <company name or number>
---

Show the filing deadlines of this UK company with the FileClerk tools: $ARGUMENTS

1. Call `get_company_deadlines` with `company_number`, or with `company_name` when the text is a name. A name answers only when exactly one company has it.
2. If the call fails with `NameNotResolved`, show its `candidates` (name, number, town, incorporation date) and ask which one the person means. Then call again with that company number.
3. Give the nearest date first. Then give each overdue and each upcoming deadline with its due date and its source.
4. Say which dates are estimates. A deadline with `basis` `estimate` or `inferred` is not a register fact.
5. End with the link to the company's FileClerk page (`url` in the answer).
