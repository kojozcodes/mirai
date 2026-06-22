# Mirai Partner — Landing Page

Premium B2B landing page for **株式会社Miraiパートナー**, connecting Japanese
manufacturers with established Chinese retail networks ("sales-connection" model).

**Live preview:** https://kojozcodes.github.io/mirai/

## About

- Single self-contained `index.html` — vanilla HTML / CSS / JS, no build step.
- Light, photo-forward theme on a navy + blue base with warm amber-orange / brown
  accents; bold mincho (serif) headings, vertical-scroll, fully responsive (PC + mobile).
- Sections: hero, problem, sales-connection model, reasons to choose us, team,
  partner network, transaction roadmap, pricing, co-creation message, contact.
- Built to be portable to **HubSpot** (custom module / file manager): the contact form
  block and image placeholders (`[Brand Logo]`, `[Photo]`) are isolated for swapping.

## Local preview

```bash
python -m http.server 4321
# then open http://localhost:4321
```

## Notes

- Fonts load from Google Fonts CDN (swap to theme fonts if blocked on HubSpot).
- Placeholder content pending real assets: brand logo, executive photos, phone number.
- The original client brief documents are intentionally excluded from this repo.
