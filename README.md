# FileClerk plugin

UK company filing deadlines, filed figures, tax calculators and iXBRL checks, from the public registers, for an AI
assistant.

This repository holds the public files of the plugin only: the plugin manifest, the address of the MCP server, one
skill, one command, and the entry of the server in the MCP registry. The server itself runs at
`https://fileclerk.co.uk/mcp`.

## What it gives an assistant

- The MCP server `fileclerk` (Streamable HTTP, `https://fileclerk.co.uk/mcp`), free and with no key, with 9 tools:
  - register lookups: a company by name, its filing deadlines and current people with significant control, its filed
    figures, its officers, a list of companies by filters, and, among the companies on FileClerk, companies like it
    and the companies in which it has significant control;
  - checks on one company: strike-off, the 2028 software filing rule, every check in one call;
  - FileClerk's guides to filing rules and tasks, found by a question, each with its page to cite.
- The skill `check-company-filings`: how to find a company, read its deadlines and report them.
- The command `/deadlines <company name or number>`.

Examples: [examples/prompts.md](examples/prompts.md). Full guide: <https://fileclerk.co.uk/docs/developers/mcp>.

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

The plugin's tools need no account and no key, at 60 lookups an hour. Each answer has an `account` field that says
what a free FileClerk account adds: the calculators, deadline alerts, the checks before a filing, and 1,000 lookups an
hour. How to sign up: <https://fileclerk.co.uk/docs/developers/mcp>.

## Privacy Policy

<https://fileclerk.co.uk/legal/privacy>

The server gets the inputs of a tool call: a company number or name, an officer ID, filters for a company list, or
the words of a guide search. It does not get the conversation. The plugin's tools store nothing that a person sends.

## Data and independence

The data comes from Companies House, The Gazette and other public registers. It contains public sector information
licensed under the [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).

FileClerk is an independent service. It is not part of HMRC or Companies House. How each date is worked out:
<https://fileclerk.co.uk/methodology>.

## Support

support@fileclerk.co.uk

## Licence

The files in this repository are under the [MIT licence](LICENSE).
