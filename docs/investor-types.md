# Investor types (under review)

The explorer labels every investor with one of six types. **The types are inferred from the forms
each investor files with the SEC and are under review.** They are not in the downloadable panel; they
appear on the website.

| type | inferred when the investor |
|---|---|
| Big Three | is Vanguard, BlackRock or State Street. Barclays Global Investors counts before 2009, because its index business became BlackRock's |
| Asset manager | files 13F (an institutional investment manager) |
| Activist | files 13D (a stake held with intent to influence control), never 13F |
| Non-financial blockholder | files 13G (a passive stake of 5% or more), never 13F or 13D |
| Insider | files only Forms 3/4/5: officers, directors, 10% owners |
| Other | has no filing kind recorded |

The first rule that matches applies. Each investor has one type for the whole sample.
An investor that files both 13F and 13D, such as Carl Icahn, counts as an asset manager.

Why "under review": the label comes from the kind of form filed, not from who the investor is. An
"activist" here is any 13D filer without a 13F, which is not the same as a hedge-fund activist from an
activism list. Treat the types as a convenient grouping, and say they are inferred when you show them.

See also the `filed_13f` warning in [variables](variables.md).
