# Contributing

Issues and pull requests are welcome. A few things keep the workbook usable for everyone who runs it:

- Keep guardrail IDs stable. The Tool Function Mapping, Compliance Mapping and the skill all join on them. Add new guardrails at the end of a family with the next number; retire one by setting Active to Off rather than deleting the row.
- A function change carries its guardrail IDs. The names and families on the Tool Function Mapping tab are generated from the IDs when the workbook is built, so edit the IDs in `build/content_functions.py` (or the Guardrail IDs column in a workbook you maintain by hand) and the rest follows.
- Landscape updates name a public source and a date. An acquisition, a rename or a new product goes in with where it was reported and when; vendor marketing copy does not.
- Compliance mapping changes cite the framework's own identifier (a control ID, an article, a technique ID). No cell is left blank; write "No direct mapping" with a reason if nothing applies.
- Records and examples are written in the third person and name no real organization as a customer. The worked examples use fictional vendors.
- Style: no em dashes, no typographic arrows, plain practitioner language. `scripts/build_record.py` rejects a record that breaks the style rules, and the same rules apply to the workbook text.

By contributing you agree that your contribution is licensed under the Apache License, Version 2.0, the same license as the project, and that you have the right to contribute it.
