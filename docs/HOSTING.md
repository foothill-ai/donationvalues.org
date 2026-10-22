# Firebase Hosting setup

## Live checks — 2026-10-22

- Repository: `foothill-ai/donationvalues.org`.
- Cloudflare nameservers: `otto.ns.cloudflare.com` and `zoe.ns.cloudflare.com`.
- No apex A or AAAA answers were returned during the check.
- Firebase CLI 15.29.0 can list existing projects using Application Default Credentials, even though `firebase login:list` shows no accounts.
- Creating a project under organization `873181806774` as `neil@foothill.ai` was denied: `resourcemanager.projects.create`.
- This identity cannot list secrets in `foothill-secrets`. No Cloudflare credential was read or DNS changed.
- No project, Hosting release, or custom-domain mapping has been created by this setup attempt.

## Admin prerequisite

Use the admin browser as `neil.admin@foothill.ai`, consistent with company vault note 23. Do not sign the admin identity into the agent host.

1. Firebase console → **Add project** (or **Create a project**). Name: **Donation Values**. Set the project ID to **donationvalues-org**, if available. Project IDs are permanent; do not accept a different generated ID without updating subsequent commands. Select the **foothill.ai** organization. Disable optional Analytics and AI assistance for this static landing page.
2. Keep the project on **Spark** for now; do not attach billing, create Firestore, or enable Authentication for this landing page.
3. Google Cloud console → select **donationvalues-org** → **IAM & Admin → IAM → Grant access**. Principal: **neil@foothill.ai**. Roles: **Firebase Hosting Admin**, **Firebase Viewer**, and **Service Usage Consumer**. These grants are limited to this new project. Save.

This grants the agent the project-specific Hosting access needed to finish the requested initial setup, without organization administration or access to company secrets. Revisit the grants when production CI is established.

## Finish Hosting

From a reviewed checkout containing this configuration, after the admin prerequisite:

```sh
firebase projects:list
firebase hosting:sites:list --project donationvalues-org
# Only if Firebase did not create its default Hosting site:
firebase hosting:sites:create donationvalues-org --project donationvalues-org
firebase deploy --only hosting --project donationvalues-org
```

Use the explicit `--project` flag; no default project is configured until the actual project ID is verified. Read back the deployed page at `https://donationvalues-org.web.app` before configuring DNS.

## Connect Cloudflare DNS

Firebase console → select the project → **Build → Hosting → Add custom domain** → **donationvalues.org**. Complete the ownership verification using the exact records returned by Firebase. Add **www.donationvalues.org** as a second custom domain and choose to redirect it to **donationvalues.org**.

Cloudflare dashboard → **donationvalues.org → DNS → Records → Add record**. Copy each record's type, name, and value from Firebase. Use **DNS only** (gray cloud) for Hosting address/CNAME records. Keep the Firebase ownership TXT record for certificate renewal. Inspect existing records before replacing conflicting website A/AAAA/CNAME records; preserve mail and other unrelated DNS records. Do not change the nameservers.

Do not guess DNS values or publish the configuration from another project. Certificate issuance can take up to 24 hours after DNS points to Firebase. Verify both custom-domain status and HTTPS, including the www redirect, before declaring setup complete.

## Verification

```sh
python3 -m json.tool firebase.json >/dev/null
git diff --check
curl -I https://donationvalues-org.web.app
dig +short A donationvalues.org
dig +short TXT donationvalues.org
curl -I https://donationvalues.org
curl -I https://www.donationvalues.org
```

Local routing can be checked with `firebase emulators:start --only hosting --project demo-donationvalues` (no live project changes). The page is a static HTML/CSS landing page with no build step or external assets.

## Context

Consulted company vault notes 02 (Firebase setup), 12 (repo hygiene), 22 (Secret Manager), and 23 (identity and access). Linear was not connected in this session.

Official references: [custom domains](https://firebase.google.com/docs/hosting/custom-domain), [Hosting custom-domain API](https://firebase.google.com/docs/reference/hosting/rest/v1beta1/projects.sites.customDomains/create).
