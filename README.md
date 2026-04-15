# HubSpot Form Handler — Developer Brief
**Dedaub Ltd** · Prepared for web dev handoff · April 2026
 
---
 
## Account credentials
 
| Parameter | Value |
|---|---|
| HubSpot Portal ID | `139690943` |
| HubSpot data center | EU (`app-eu1.hubspot.com`) |
| Submission endpoint base | `https://api.hsforms.com/submissions/v3/integration/submit/139690943/` |
| API key required? | **No** — endpoint is unauthenticated |
| Auth only needed for | Direct Contacts API (Approach 2, not used here) |
 
---
 
## Files in this package
 
| File | Purpose |
|---|---|
| `hubspot.js` | Reusable submit utility — import in every handler |
| `api/audit-request.js` | Handler for Audit Request form (reference implementation) |
| `AuditForm.jsx` | React component for the audit form UI |
 
---
 
## Forms to build — priority order
 
Below is the complete cross-reference of every live form on dedaub.com with its HubSpot mapping.
**Forms marked ✅ ACTIVE are the ones the dev must build handlers for.**
Legacy forms (marked ⚠️) are still live in HubSpot but superseded — keep for compatibility, do not build new handlers.
 
---
 
## FORM 1 — Audit / Request a Quote ✅ ACTIVE (highest priority)
 
**Website URL:** `https://dedaub.com/form/request-an-audit/`
**Also appears on:** `dedaub.com/smart-contract-audit/`, `dedaub.com/smart-contract-audit-avs/` (via Google Ads)
**HubSpot form name:** Audit (Request a quote) (Dedaub.com 2.0)
**Form GUID:** `055edf7a-b0f5-400f-ae60-c12bc3248fcf`
**Submissions:** 158 (most active audit form)
 
### Field map
 
| Internal name | Label shown to user | Type | Required |
|---|---|---|---|
| `my_name_is` | My name is | Text | ✅ |
| `email` | Email | Email | ✅ |
| `telegramusername` | Telegram Username | Text | ✅ |
| `twitterhandle` | Twitter username | Text | ✅ |
| `company` | Project name | Text | ✅ |
| `code_repo` | Link to code repo (GitHub — share with @dedaub-auditors) | Text | ⬜ |
| `message` | Tell us more about your project | Textarea | ⬜ |
| `how_did_you_hear_about_us_` | How did you hear about us? | Dropdown (enum) | ⬜ |
| `lead_type` | Lead Type | Hidden dropdown | auto: `"Inbound"` |
| `hs_lead_status` | Lead status | Hidden dropdown | auto: `"New"` |
| `lead_owner` | Lead Owner | Hidden | auto: Giorgio Bonuccelli |
 
> **Note:** The legacy form (`b2b5f69d`) also required `authority`, `timeline`, `country` — the 2.0 version removed these as required. Use the 2.0 GUID above.
 
---
 
## FORM 2 — Contact Us ✅ ACTIVE
 
**Website URL:** `https://dedaub.com/form/contact-us/`
**HubSpot form name:** Contact Us (Dedaub.com 2.0)
**Form GUID:** `0a382995-1852-46d4-bf6e-41c91d48d185`
**Submissions:** 130
 
### Field map
 
| Internal name | Label shown to user | Type | Required |
|---|---|---|---|
| `my_name_is` | My name is | Text | ✅ |
| `email` | Email | Email | ✅ |
| `telegramusername` | Telegram Username | Text | ✅ |
| `message` | Brief overview of your needs or project | Textarea | ✅ |
| `company` | Project name | Text | ⬜ |
| `how_did_you_hear_about_us_` | How did you hear about us? | Dropdown (enum) | ⬜ |
| `lead_type` | Lead Type | Dropdown (enum) | ⬜ |
| `hs_lead_status` | Lead status | Hidden dropdown | auto: `"New"` |
| `lead_owner` | Lead Owner | Hidden | auto: Giorgio Bonuccelli |
 
---
 
## FORM 3 — Blog / Newsletter Subscribe ✅ ACTIVE
 
**Website URL:** Appears on all blog pages (footer / inline subscribe widget)
**HubSpot form name:** Blog Subscriber (Dedaub.com 2.0)
**Form GUID:** `a9809d49-671b-419e-9005-d8e9f44455eb`
**Submissions:** 99
 
### Field map
 
| Internal name | Label shown to user | Type | Required |
|---|---|---|---|
| `email` | Email | Email | ✅ |
| `lead_type` | Lead Type | Hidden dropdown | auto: `"Subscriber"` |
 
> Simplest form — single email field. Submit button says "Subscribe".
 
---
 
## FORM 4 — Security Suite Trial  ⚠️ LEGACY 
 
**Website URL:** `https://dedaub.com/pricing/` and `https://dedaub.com/product/security-suite/`
**HubSpot form name:** Dedaub Security Suite Trial
**Form GUID:** `d1565925-5281-42cc-b017-5be026eb7843`
**Submissions:** 31
 
### Field map
 
| Internal name | Label shown to user | Type | Required |
|---|---|---|---|
| `firstname` | First name | Text | ✅ |
| `lastname` | Last name | Text | ✅ |
| `email` | Email | Email | ✅ |
| `telegramusername` | Telegram Username | Text | ✅ |
| `company` | Project name | Text | ✅ |
| `website` | Project website | URL | ✅ |
| `company_x__handle` | Project X @handle | Text | ✅ *(Company Property)* |
| `authority` | Involved in security software evaluation? | Dropdown (enum) | ✅ |
| `timeline` | Timeline for implementing security solution? | Dropdown (enum) | ✅ |
| `watchdog_need` | How do you plan to use the Security Suite? | Multi-checkbox | ⬜ |
| `message` | Details about your project | Textarea | ✅ |
| `country` | Country/Region | Dropdown | ✅ |
| `how_did_you_hear_about_us_` | How did you hear about us? | Dropdown (enum) | ⬜ |
| `lead_type` | Lead Type | Hidden | auto: `"Security Suite"` |
 
> **Note:** `company_x__handle` maps to a **Company Property** (not Contact). Pass `objectTypeId: "0-2"` for this field in the payload.
> `watchdog_need` is a multi-select checkbox — send comma-separated values.
 
---
 
## FORM 5 — Partner Registration ✅ ACTIVE
 
**Website URL:** `https://dedaub.com/partners/`
**HubSpot form name:** Partner Registration
**Form GUID:** `fc2c012d-d615-43c5-9fab-aabcaf2de6ae`
**Submissions:** 3
 
> Field names not yet pulled — open editor at:
> `app-eu1.hubspot.com/forms/139690943/editor/fc2c012d-d615-43c5-9fab-aabcaf2de6ae/edit/form`
 
---
 
## FORM 6 — Google Ads — Audit (paid traffic) ⚠️ LEGACY / AD-SPECIFIC
 
**Website URL:** `dedaub.com/smart-contract-audit/` (Google Ads landing page variant)
**HubSpot form name:** Google Ads Audit contact form
**Form GUID:** `e6946e3f-a1d9-45f0-952d-d7fa12551f47`
**Submissions:** 89
 
> This form is specifically for paid traffic landing pages. Keep it separate from the organic audit form so Google Ads conversion tracking stays accurate. Field names not yet pulled — pull from form editor if needed.
 
---
 
## FORM 7 — Google Ads — AVS Audit ⚠️ AD-SPECIFIC
 
**Website URL:** `dedaub.com/smart-contract-audit-avs/`
**HubSpot form name:** Google Ads AVS
**Form GUID:** `c78ffb0e-831b-48fc-87e9-df6a3dcacea6`
**Submissions:** 14
 
> Same as above — keep separate for AVS-specific ad attribution.
 
---
 
## Legacy / deprecated forms (do NOT build new handlers)
 
| Form name | GUID | Submissions | Status |
|---|---|---|---|
| Audit (Request a quote) — legacy | `b2b5f69d-9937-4fc6-9178-2497666fea12` | 25 | Superseded by 2.0 |
| Contact Us — legacy | See page 1 of HubSpot forms | ~138 | Superseded by 2.0 |
| Blog Subscriber — legacy | `ddb6c865-11cf-4791-ae01-1f3df9bd8be3` | 21 | Superseded by 2.0 |
| Dedaub Security Suite Trial / ETHDenver 2024 | `b89384e7-35b6-430b-963e-2bd72d77561b` | 8 | Event-specific, archived |
| ETHDenver 2024 Audit Leads | `de6111e0-6dbd-423e-b3be-b7867f89d039` | 7 | Event-specific, archived |
| ETHDenver 2025 | `e986d89c-86bb-4d62-93bb-7f9fcfcff0bb` | 51 | Event-specific, archived |
| Dedaub tok{in} subscription | `ea05ae0e-e4dc-41b5-a1aa-03ab2f019d4d` | 5 | Replaced by Blog Subscriber 2.0 |
| Unique single form New website | `c7b6be97-8ad6-4eb9-8114-a786abd3e97e` | 0 | Never used, can delete |
| Dedaub Security Suite Trial Sales | `1e0f4735-df39-4535-8915-3fd11cd5aae3` | 0 | Never used |
| MSP Monitoring | See page 1 | 0 | Inactive |
| Security Suite Survey (Individual/Team) | See page 1 | ~2 | Surveys, not lead gen |
 
---
 
## Enum values — how to get them
 
For `authority`, `timeline`, `how_did_you_hear_about_us_`, `lead_type`, `hs_lead_status`:
 
1. Go to `app-eu1.hubspot.com/property-settings/139690943/contacts`
2. Search the internal property name (e.g. `authority`)
3. Click → "Options" tab shows all valid enum values
 
Or ask Giorgio to export them — they're visible in each form's HubSpot editor dropdown.
 
---
 
## Payload format (all forms)
 
```json
POST https://api.hsforms.com/submissions/v3/integration/submit/139690943/{FORM_GUID}
Content-Type: application/json
 
{
  "submittedAt": 1713175200000,
  "fields": [
    { "objectTypeId": "0-1", "name": "email",        "value": "dev@protocol.xyz" },
    { "objectTypeId": "0-1", "name": "my_name_is",   "value": "Alex" },
    { "objectTypeId": "0-2", "name": "company_x__handle", "value": "@protocolxyz" }
  ],
  "context": {
    "hutk":     "hubspotutk_cookie_value",
    "pageUri":  "https://dedaub.com/form/request-an-audit/",
    "pageName": "Request an Audit"
  }
}
```
 
**Object type IDs:**
- `"0-1"` = Contact property (use for all standard fields)
- `"0-2"` = Company property (only for `company_x__handle` in Security Suite form)
 
**`hutk`** = value of the `hubspotutk` browser cookie. Pass it when available — it links the submission to the HubSpot Analytics visitor session and fires workflow automations correctly.
 
---
 
## Spam protection
 
**Layer 1 — Honeypot** (already in `AuditForm.jsx`, replicate for all forms):
```html
<input type="text" name="website" style="position:absolute;left:-9999px;opacity:0"
  autocomplete="off" aria-hidden="true" tabindex="-1" />
```
Server rejects any submission where this field is non-empty.
 
**Layer 2 — CAPTCHA** (recommended):
- Cloudflare Turnstile (best if dedaub.com uses Cloudflare — free, invisible)
- hCaptcha (privacy-first, Web3-native, free tier)
- Full wiring code in `AuditForm.jsx` comments
 
---
 
## Testing
 
HubSpot Professional has no sandbox mode for form submissions. Test with `+alias` emails (e.g. `giorgio.b+test1@dedaub.com`) and delete the test contacts afterward.
 
- Check submissions: `app-eu1.hubspot.com/submissions/139690943/form/{GUID}/submissions`
- Check contacts created: `app-eu1.hubspot.com/contacts/139690943/objects/0-1/views/all/list`
 
---
 
## Questions?
 
Contact Giorgio Bonuccelli · giorgio.b@dedaub.com

