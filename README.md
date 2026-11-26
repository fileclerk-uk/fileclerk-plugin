# FileClerk plugin

UK company filing deadlines, filed figures, tax calculators and iXBRL checks, from the public registers, for an AI
assistant.

This repository holds the public files of the plugin only: the plugin manifest, the address of the MCP server, one
skill, one command, and the entry of the server in the MCP registry. The server itself runs at
`https://fileclerk.co.uk/mcp`.

## What it gives an assistant

- The MCP server `fileclerk` (Streamable HTTP, `https://fileclerk.co.uk/mcp`) with its public tools:
  - register lookups: a company by name, its filing deadlines, its filed figures, its officers, a list of companies
    by filters and the link to that list as a CSV file, and how the companies people looked up filed their last
    accounts;
  - checks on one company: strike-off, the 2028 software filing rule, every check in one call;
  - calculators: first deadlines from an incorporation date, late filing penalties, Corporation Tax, s455 tax on a
    director's loan, take-home pay, a director's salary and dividends, company size;
  - before a filing: a check of iXBRL accounts, a dry run of annual accounts, with a PDF of them as they go to
    Companies House on request, or a CT600, and a community interest company's accounts package (its accounts and
    CIC34 report in one ZIP to upload at Companies House). Nothing is filed;
  - email alerts for a company's deadlines;
  - FileClerk's guides to filing rules and tasks, found by a question, each with its page to cite;
  - writing to FileClerk: an error report, feedback or a question.
- The skill `check-company-filings`: how to find a company, read its deadlines and report them.
- The command `/deadlines <company name or number>`.

Examples: [examples/prompts.md](examples/prompts.md). Full guide: <https://fileclerk.co.uk/developers/mcp>.

## Install

In Claude Code:

```sh
/plugin install fileclerk --marketplace fileclerk-uk/fileclerk-plugin
```

## Use it without the plugin

Add `https://fileclerk.co.uk/mcp` as a remote MCP server in your client. In Claude Code:

```sh
claude mcp add --transport http fileclerk https://fileclerk.co.uk/mcp
```

## Not advice

FileClerk gives general information from the public registers and the published rules of Companies House and
HMRC. Its deadlines, tax figures and checks are not professional tax, accounting or legal advice. FileClerk is
independent of Companies House and HMRC.

## Access and limits

No account is needed. Each tool works with no key, at 60 lookups an hour for one address. A free FileClerk API key
in the `x-api-key` header raises that to 1,000 an hour.

## Privacy Policy

<https://fileclerk.co.uk/legal/privacy>

The server gets the inputs of a tool call: a company number or name, the figures for a calculator, the text of a
document to check or to package, or the words of a guide search. It does not get the conversation. `follow_companies` stores the email address that the person
gives, to send deadline alerts, until the person unsubscribes. `send_feedback` stores the message, the text and
company number it names, and the email address when the person gives one, for 12 months, to reply.

## Data and independence

The data comes from Companies House, The Gazette and other public registers. It contains public sector information
licensed under the [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).

FileClerk is an independent service. It is not part of HMRC or Companies House. How each date is worked out:
<https://fileclerk.co.uk/methodology>.

## Support

support@fileclerk.co.uk

## Licence

The files in this repository are under the [MIT licence](LICENSE).
