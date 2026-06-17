# Mirai Partner LP — HubSpot custom module

This packages the landing page (`/index.html` at the repo root) as a **single self-contained
HubSpot custom module** so it can be placed on a HubSpot Landing Page, with the logo, images,
contact details, and form all editable from the page editor.

> ⚠️ **Authored, not yet tested inside HubSpot.** The HubL was written by hand and is correct as
> far as it can be verified outside a HubSpot account. Because the client's HubSpot account/domain
> isn't set up yet, the items in **"Setup checklist"** below should be walked through together
> before go-live (this matches the brief's request to consult on the HubSpot workflow).

## Folder contents

```
hubspot/
├─ README.md                    ← this file
└─ mirai-lp.module/             ← the HubSpot module (upload this folder)
   ├─ module.html               ← markup + inline CSS/JS + HubL fields
   ├─ fields.json               ← editable field definitions
   └─ meta.json                 ← module metadata
```

## Editable fields (set in the page editor, no code needed)

| Field | Type | What it controls |
|-------|------|------------------|
| `brand_logo` | image | Header + footer logo (falls back to the built-in mark) |
| `hero_image` | image | Hero background (中国都市景観). Default = the Shanghai photo |
| `strength_image` | image | 強み section photo (日本のものづくり) |
| `ceo_photo` / `cfo_photo` | image | Executive headshots (placeholder until set) |
| `contact_email` | text | Email — used in the contact card, footer, and `mailto:` |
| `contact_phone` | text | Phone — display + `tel:` (hyphens auto-stripped for the link) |
| `contact_form` | form | The HubSpot form embedded in the contact section |
| `footer_address` | text | Footer postal address |
| `site_url` | text | Footer site URL (display) |

Image defaults point at the GitHub Pages copies, so the module **previews correctly immediately**;
swap them for HubSpot-hosted files before launch.

## How to upload

**Option A — HubSpot CLI (recommended)**
```bash
npm install -g @hubspot/cli
hs init                       # authenticate to the portal once
hs upload hubspot/mirai-lp.module  "mirai-lp.module"
```
Then: create a blank **Landing Page**, drag the **"Mirai Partner LP"** module onto it.

**Option B — Design Manager (no CLI)**
Design Manager → **File → New → Module** (check "Pages") → switch the editor to the
HTML+HubL / CSS / JS views and paste from `module.html`, then recreate the fields from
`fields.json` in the right-hand **Add field** panel.

## Setup checklist (walk through before launch)

1. **Fonts (CDN).** The module loads Google Fonts (Noto Sans JP / Inter / Montserrat) via a
   `<link>`. Confirm your HubSpot domain doesn't block it; otherwise host the fonts or switch to
   the theme fonts. *(Brief Step 2: 依存関係の確認.)*
2. **Contact form.** Create a HubSpot form with: 会社名 / ご担当者名 / メール / 電話 /
   打ち合わせ希望日 / お問い合わせ内容, then select it in the module's **問い合わせフォーム** field.
   Set the auto-reply email (件名「お問い合わせありがとうございます｜株式会社Miraiパートナー」, 2営業日以内返信).
3. **Images.** Upload final logo + exec photos to the File Manager and set the image fields
   (or leave the hero/strength defaults).
4. **Domain.** Connect `mirai-partner.site` (brief notes the domain is still to be secured).
5. **Mobile preview.** Use HubSpot's preview to check the pricing table and roadmap on a phone
   (brief Step 2: モバイルレスポンシブの実機確認).
6. **SEO / OGP.** Title, meta description, and OGP image are set in **HubSpot page settings**,
   not in the module (the page-level `<head>` was intentionally removed).
7. **SSL / Analytics.** Enable SSL and add the Google Analytics tracking in the page/domain
   settings.

## Notes

- The whole LP lives in one module for simplicity (brief allows カスタムモジュール or ファイルマネージャー).
  If you'd prefer section-by-section modules later, this can be split.
- CSS/JS are inline in `module.html`. They can be moved to `module.css` / `module.js` if you want
  HubSpot to manage them as separate assets.
