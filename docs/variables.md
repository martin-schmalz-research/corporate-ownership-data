# Variables and definitions

Source: the all-firms data set's README, which is the reference. The data are at the **company**
level, not the security level: an owner's holdings in all share classes of a company are summed into
one stake. Holdings are as of quarter end.

## In the full panel

| variable | meaning |
|---|---|
| `coname` | company name |
| `ownercik` | owner identifier (SEC central index key) |
| `ownername` | owner name as reported on filings |
| `beta` | fraction of shares outstanding owned, over all share classes |
| `gamma` | fraction of voting rights outstanding owned, over all share classes |
| `rdate` | end of the quarter when the shares are owned |
| `fdate` | actual date when the ownership is reported |
| `filed_13f`, `filed_13d`, `filed_13g`, `filed_f345` | the owner filed a 13F / 13D / 13G / Form 3-4-5 report this quarter (see the warning below) |
| `source` | the filing type on which the stake was reported |
| `is_dual` | the company had more than one class of stock this quarter |
| `is_sp500` | the company was in the S&P 500 this quarter |
| `sic` | SIC industry code of the company |
| `outlier` | firm-quarter with implausible aggregate voting ownership |

The download carries a few further company-identifier columns; its README describes them. Binary
flags are stored as the text `True` / `False`.

## Ownership β, voting control γ

- **β (ownership):** the cash-flow share. The shares an owner holds in a company, over all its share
  classes, divided by all shares outstanding across those classes.
- **γ (control):** the voting share. The votes those same shares carry, divided by all votes
  outstanding.

In a single-class company one share is one vote, so γ = β. They differ only in dual-class companies:
most often one class with no vote and one with a vote per share, or one vote against ten votes per
share; in extreme cases the ratio is 1:10,000. Traded and non-traded classes are both included, so β and
γ are the owner's full economic and voting stake. The number of votes per class was collected by hand
and checked quarter by quarter against the company's filings (10-K, 10-Q and proxy statements).

Both are fractions: 0.05 is 5%.

## Profit weight κ (kappa)

The profit weight from company A to company B says how much A's owners care about B's profits
relative to A's own. It is the owners' control in A times their ownership in B, added up over all
owners and divided by the same sum for A with itself:

    κ(A→B) = Σᵢ γ(i,A) · β(i,B)  /  Σᵢ γ(i,A) · β(i,A)

where i runs over the owners. It is not symmetric: κ(A→B) differs from κ(B→A). A value of 1 means A's
owners weigh B's profit as much as their own. The explorer's averages are equal-weighted means of κ
over ordered pairs of firms, using each owner's γ. They are computed from the current data release, so
they differ slightly from the published papers.

## `source` and the `filed_` flags

`source` takes the values `13f`, `f345` and `13dg`. Where one holding's share classes were reported on
different filing types, the types are joined with `*` (for example `13f*f345`). Where several filing
types report the same holding, the highest priority is kept (13F, then Forms 3/4/5, then 13D/G).

> **Warning: classify owners by `source`, not by `filed_13f`.**
> The `filed_` flags say that *the owner* filed that kind of report this quarter. They are recorded
> before duplicate reports are dropped, so they show every filing type that reported the holding,
> even where only the highest-priority report survives in `source`. `filed_13f` is therefore also
> true on some insiders' Form 3/4/5 holdings. Counting `filed_13f == True` as "institutional
> investor" will mislabel those stakes.

## Carrying holdings forward

13F filings are made every quarter, but 13D/G and Form 3/4/5 filings only when holdings change. No
report therefore does not mean no holding. These holdings are carried forward from one filing to the
next, and the last holding is extrapolated for at most 12 quarters (3 years) beyond the final report.
An empty quarter for an investor does not always mean no position.

## Outliers

`outlier` marks firm-quarters in which the sum of γ over all the firm's owners is more than 1.96
standard deviations from that firm's own average over the sample. Such jumps are usually data errors
but sometimes real changes in the stock structure, so they are marked, not dropped. 1,907,493 of the
58,365,351 rows are flagged. Re-run results without them as a robustness check; dropping them removes
55 of the 7,156 companies entirely.
