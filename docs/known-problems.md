# Known problems

The data are not guaranteed to be accurate. Parsing is difficult, investors misfile reports, and the
SEC's reporting rules limit how accurate ownership data can be. Please check the original filings in
the SEC archive when a stake looks out of proportion.

## General

- **Totals above 100%.** In some firm-quarters the stakes sum to more than 100%, mostly from 13F
  managers reporting shares lent to other 13F managers.
- **Outliers.** `outlier` marks firm-quarters with implausible aggregate voting ownership: 1,907,493
  rows. Re-run results without them. See [variables](variables.md).
- **Classify owners by `source`, not by `filed_13f`.** `filed_13f` is also true on some insiders'
  Form 3/4/5 holdings. See [variables](variables.md).
- **Thin early insiders and carried-forward holdings.** See [coverage](coverage.md).
- **Investor types are inferred and under review.** See [investor types](investor-types.md).
- **The averages in the explorer differ slightly from the papers**, which used earlier releases and samples.

## Specific problems the website lists

The website's explorer marks these with a red "Known data problem, under review" note, as of
2026-10-05. Each is under review for the next data release. The site is the current list:
<https://corporateownershipdata.com/explorer/>.

| company or investor | quarters | what the data show |
|---|---|---|
| Bank of America | 2016 Q3 – 2019 Q3 | One holder, "ynoface holdings inc", is recorded with 40–45% of the company, from a single 2016 insider filing (Form 4) claiming 4.2 billion shares, which is very likely false |
| Alphabet | 2015 Q4 – 2020 Q4 | After Google became Alphabet, the founders' voting shares are miscounted (an old record counted twice until late 2018; after that their 10-vote shares count as 1 vote). Voting figures are unreliable |
| Walmart | 2004 Q2 – 2007 Q4 and 2010 Q1 – 2020 Q4 | The Walton family's combined stake, around 40–50%, is missing: only one family member's own shares (under 1%) are recorded |
| Coca-Cola | 2000 Q4 – 2011 Q4 | Berkshire Hathaway's stake, about 8–9%, is missing: its filings for those years are in a format the parser could not read |
| A. O. Smith | 2001 Q3 – 2002 Q2 | The voting weights of the two share classes are recorded the wrong way round |
| A. O. Smith | 2002 Q3 – 2020 Q4 | The Class A shares, which carry most of the votes, are missing, so every holder's voting share equals its ownership share and ownership adds up to more than 100% |
| Berkshire Hathaway (as an investor) | 2000 Q4 – 2011 Q4 | Its holdings are missing for most companies, for the same parsing reason |

## Report a problem

Use the [data correction issue form](../../../issues/new?template=data-correction.yml) or the
website's [feedback page](https://corporateownershipdata.com/feedback/).
