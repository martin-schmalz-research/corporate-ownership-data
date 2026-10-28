# Corporate ownership data

Who owns U.S. public companies, quarter by quarter, 2000 Q4 – 2020 Q4: institutional managers,
insiders and blockholders, from SEC filings. By Amel-Zadeh, Kasperk and Schmalz.
Website: <https://corporateownershipdata.com/>

> **Status: draft.** This repository tracks data problems and releases. The **full panel is not in
> this repository**; it needs the data request (see [Get the full data](#get-the-full-data)).

## What the data is

A quarterly time series of every ownership stake that must be reported to the SEC, for firms
incorporated and publicly traded in the U.S., **2000 Q4 – 2020 Q4** (81 quarters). The full panel has
58,365,351 owner-firm-quarter observations, 7,156 companies and 117,166 owners. It combines:

- **13F** filings: institutional investment managers with more than $100m under management;
- **13D/13G** filings: blockholders owning more than 5% of a company;
- **Forms 3/4/5**: corporate insiders, executives, directors and 10% owners.

For each owner, company and quarter it gives **β** (the share of the company's shares owned) and **γ**
(the share of its voting rights owned), summed over all share classes. Holdings are as of quarter end.
Details: [variables and definitions](docs/variables.md), [coverage](docs/coverage.md),
[investor types](docs/investor-types.md).

**Read the [known problems](docs/known-problems.md) before relying on a number.** The data are not
guaranteed to be accurate; check the SEC filings when a stake looks out of proportion.

## Get the full data

The full panel is free for academic research, subject to the website's terms. Submit the data request
at <https://corporateownershipdata.com/> ("Data request"; direct link:
<https://corporateownershipdata.com/datasets/request_download/>). You get a link to a download window
where you can filter by period or firm. See [`DATA-TERMS.md`](DATA-TERMS.md): this repository grants no
rights to the data.

## Report a data problem

Open a [data correction issue](../../issues/new?template=data-correction.yml): say which company or
investor, which quarters, what is wrong, and link the SEC filing. Reporters will be credited in a
public changelog by the name or GitHub account you give. For now you can also use the website's
[feedback page](https://corporateownershipdata.com/feedback/). Reports never edit the published data
directly; confirmed problems are listed on the website and fixed in a later data release.

## Known problems

See [`docs/known-problems.md`](docs/known-problems.md). The explorer on the website shows a red
"Known data problem" note on affected companies and investors, and shades outlier quarters.

## What is here

| path | what |
|---|---|
| [`docs/`](docs/) | variables, investor types, coverage, known problems, citing |
| [`CITATION.cff`](CITATION.cff) | citation metadata |

## If you use this data, please cite

- Amel-Zadeh, A., Kasperk, F., Schmalz, M. C. *Mavericks, Universal, and Common Owners - The Largest
  Shareholders of U.S. Public Firms.* <https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4059513>
- Amel-Zadeh, A., Kasperk, F., Schmalz, M. C. *Common Ownership, Incentives & Productivity.*
  <https://www.ssrn.com/abstract=4941701>
