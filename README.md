# BoringAccountants site

React/Vite site for BoringAccountants.com.

## Skill listings on the Bots page

The Bots page is generated from OpenClaw user skills instead of being maintained by hand.

Source of truth:

```text
/Users/asendant/.openclaw/workspace/skills/<skill-name>/SKILL.md
```

When adding or changing a public skill:

1. Create or update the skill's `SKILL.md` in the shared skills folder.
2. Keep the front matter useful:

   ```yaml
   ---
   name: xero-bank-statement-import
   displayName: Xero Bank Statement Import
   description: Short customer-facing summary.
   category: Accounting automation
   status: live
   tags: xero, csv, reconciliation
   public: true
   ---
   ```

3. Run:

   ```bash
   npm run sync:skills
   npm run lint
   npm run build
   npm run check:skills
   ```

4. Commit the updated skill and generated `src/data/skills.json` with the website changes.

Visibility rules:

- `public: false` hides a skill.
- `status: draft`, `internal`, `private`, or `hidden` hides a skill.
- Missing `status` defaults to `live`.
- Missing `category` defaults to `Automation`.

## Development

```bash
npm run dev
npm run lint
npm run build
```
