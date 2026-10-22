# DonationValues.org

A free, community-maintained dataset of reference fair market value ranges for donated clothing and household goods, for donors, nonprofits, and tax preparers.

Our goal is to help people value donations accurately and encourage more giving. We plan to publish a free website at [donationvalues.org](https://donationvalues.org) and free mobile apps that use the same dataset.

## Status

Project setup and source-permission outreach. No donation values, website, or mobile apps have been published from this repository yet. No permission from Goodwill or any other third-party source has been obtained or is implied.

## Data and attribution

The intended dataset license is [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/), allowing reuse and adaptation, including commercial use, with appropriate attribution, a license link, and an indication of changes.

Third-party data will be included only after its rights and compatibility with CC BY 4.0 have been confirmed. Permission to display a guide alone is not enough: permission must cover extraction, normalization, adaptation, and public redistribution of the data under CC BY 4.0, including reuse by others.

Each published value should identify:

- The source organization, guide title, edition or publication date (or explicitly unknown), and source URL.
- The original item name, low/high values, currency, and any condition, geographic, or unit assumptions supplied by the guide.
- The date the source was accessed, permission reference, and any normalization or other changes.

Source organizations do not endorse or maintain this project unless they explicitly agree otherwise. Source names are used for attribution; logos are not included by default.

We can correct or remove data from future releases and the website on request. We cannot revoke CC BY 4.0 rights already granted to compliant recipients or recall previously distributed copies.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Please open an issue to suggest a source, identify an error, or discuss the dataset structure before submitting values.

## Planned delivery

Maintain the reviewed dataset in Git and publish versioned JSON/CSV downloads that the website and mobile apps can consume. Firebase Hosting is the current recommendation for the website, consistent with Foothill AI's existing website infrastructure. Hosting has not been provisioned; a live database is not required for the initial read-only dataset.

## Valuation context

Guide ranges are estimates, not appraisals or guarantees of a tax deduction. An item's actual fair market value depends on its condition and relevant market. Donors remain responsible for their valuations and applicable tax requirements.

## License

See [LICENSE](LICENSE). The planned dataset license does not grant rights to source guides, trademarks, or other third-party material. A software license will be selected when application code is introduced.
