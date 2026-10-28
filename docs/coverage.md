# Coverage

Source: the all-firms data set's README.

- **Period:** 2000 Q4 – 2020 Q4, quarterly, 81 quarters. Earlier quarters are too incompletely covered
  by the SEC archive. The data end in 2020 Q4: do not describe them as current ownership.
- **Firms:** companies incorporated and publicly traded in the U.S., common equity only: 7,156
  companies, single-class and dual-class. 911 of them are ever in the S&P 500.
- **Owners:** 117,166. **Rows:** 58,365,351 owner-firm-quarter observations.
- **Filings:** 13F (managers above $100m), 13D/G (blockholders above 5%), Forms 3/4/5 (insiders).

## Where it is thin

- **Insiders early on.** Electronic Form 3/4/5 filing became mandatory in 2003. Before 2004 the most
  significant insiders (above 5% of equity) are captured through their blockholder filings instead.
- **Dating.** 13F holdings are dated to the quarter end they report. Blockholder and insider holdings
  are dated to the quarter of the reported event and of the filing respectively.
- **S&P 500 firms are denser.** An S&P 500 firm-quarter has 691 distinct owners on average, against
  156 for a non-member. S&P 500 firm-quarters are about 46% of the rows (26,995,131) though only 911
  of the 7,156 companies are ever in the index.

## What was excluded

Stakes of 110% of shares outstanding or more are removed. So are firms in which a single owner is
recorded above 104% in more than one quarter; firms where all owners together reach 200% in any
quarter; and firms where the total exceeds 150% or falls below 30% in more than eight quarters or in a
fifth of their quarters. A firm's first or last quarter is dropped if less than 30% of it is captured.
S&P 500 firms are exempt from these exclusions and always retained.

Totals above 100% still occur, as at Factset and Capital IQ: mostly 13F managers reporting shares
lent out to other 13F managers who also report them. They cannot be identified automatically.
