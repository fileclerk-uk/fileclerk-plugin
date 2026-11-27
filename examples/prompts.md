# Example prompts

Each prompt works with no account and no key.

| Prompt | Tools that answer it |
|---|---|
| When are the accounts of Tesco PLC due? | `search_companies`, `get_company_deadlines` |
| Who has significant control of company 15557917? | `get_company_deadlines` |
| What did company 00445790 report in its last accounts? | `get_company_finances` |
| My company was formed on 2 November 2026. What are its first deadlines? | `calculate_deadlines` |
| What is the Corporation Tax on a profit of £120,000 for the year to 31 March 2026? | `calculate_corporation_tax` |
| Our accounts were due on 30 September and went in today. What is the penalty? | `calculate_penalty` |
| Can company 00445790 apply for strike-off? | `check_strike_off` |
| Check this iXBRL file before I send it to Companies House. | `validate_accounts` |
| Prepare our accounts as a dry run and give me a PDF of them as they go to Companies House. | `prepare_accounts` |
| Make the CIC34 report and the Companies House ZIP for our community interest company from these accounts. | `prepare_cic_package` |
| Email me before each deadline of company 00445790. | `follow_companies` |
| How did the companies people looked up on FileClerk file their last accounts? | `get_accounts_route_counts` |
| What does HMRC error 3001 mean? | `search_help` |

`follow_companies` sends one confirmation email to the address that the person gives. `send_feedback` sends the
person's message to FileClerk, which keeps it for 12 months. No other tool sends or saves anything.
