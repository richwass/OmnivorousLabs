# Email Migration Checklist (Provider → Provider)

**Goal:** keep `@omnivorouslabs.com` addresses stable while changing mail provider.

## 0) Prep
- Ensure you control DNS for omnivorouslabs.com (registrar or Cloudflare).
- Create desired mailboxes and aliases on the **new** provider (e.g., hello@, rich@).

## 1) Lower TTLs (3–6 hours before cutover)
- In your DNS, reduce TTL for MX/TXT records to ~300 seconds to speed propagation.

## 2) Add new provider DNS (in advance)
- Add new **MX** records (keep old MX for now).
- Add/adjust **SPF** TXT to include the new provider.
- Generate and add **DKIM** TXT (from new provider).

## 3) IMAP copy (optional: to preserve history)
- Use the new provider’s IMAP import tool, or an IMAP sync tool, to copy mail from old → new.
- Validate folders and labels look correct for key mailboxes.

## 4) Cutover window
- Update **MX** to point only to the new provider (remove old MX).
- Keep old provider active for 24–72h (just in case of straggler delivery).

## 5) Test
- Send/receive to and from external addresses (Gmail, Outlook).
- Validate SPF pass, DKIM pass, DMARC pass (check raw headers).

## 6) Tighten DMARC (after a week or two of clean delivery)
- Change DMARC to `p=quarantine`, then `p=reject` once confident.

## 7) Decommission old provider
- Export a final mailbox backup (optional).
- Terminate old plan only after you’ve confirmed all users are stable for a week.

---
**SPF Reference**: Keep it simple and specific. Example for Google: `v=spf1 include:_spf.google.com ~all`  
**DKIM**: Use your provider’s recommended selector (e.g., `google._domainkey`).  
**DMARC**: Start with `p=none` + reporting; move to enforcement later.
