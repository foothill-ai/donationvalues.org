# DonationValues.org

Free, community-maintained donation value dataset with a planned website and mobile apps. Read README.md and CONTRIBUTING.md before making changes.

- This is a new project. No third-party values or source permissions have been accepted yet.
- Dataset licensing is intended to be CC BY 4.0. Confirm rights to redistribution under that license before adding third-party data; never treat a public guide as permission.
- Keep each value traceable to its original source, edition, condition assumptions, and permission record. Do not invent or silently combine source values.
- Do not commit private correspondence, personal information, or secrets.
- Keep the initial architecture simple: Git-maintained data and static downloads. Firebase Hosting is recommended but has not been provisioned.
- Update this file when the project adopts implementation tools and validation commands.

## Hosting setup

- Static landing page: `public/`. Firebase configuration: `firebase.json`.
- See `docs/HOSTING.md` for verified setup status, admin prerequisites, and deployment checks. Infrastructure has not been provisioned yet.
- Always specify `--project` explicitly until the actual project ID is verified.
- Local check: `firebase emulators:start --only hosting --project demo-donationvalues`.
