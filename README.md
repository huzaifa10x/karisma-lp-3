# Karisma Hollywood Smile, Landing Page 3

Open `Landing Page 3.dc.html` in a browser (keep `support.js` and `assets/` next to it). `Landing Page 3 - standalone.html` is the same page as one self-contained file.
Arabic (RTL) is the default; the header toggle switches to English (LTR).

## Structure
1. Header (logo, language toggle, WhatsApp)
2. "كل الناس ممكن يطلبون Hollywood Smile…" with an 11-card patient slider (arrows + swipe). Each caption answers a common objection.
3. "قبل ما تختار ابتسامتك، اعرف إيش يناسبك" with the lead form inline (`id="lead"`)
4. Footer + sticky mobile CTA (scrolls to the form)

All copy (AR + EN) is in the `copy()` method of the logic class. Card captions: `s2caps`. All styles are inline.

## Lead form
Visible: full name (required), phone + country code (required), WhatsApp (optional), email (optional), service (required: ابتسامة هوليود / زراعة اسنان / تقويم اسنان / تبييض اسنان).

Hidden:
- `source`: button that sent the user to the form
- `campaign_source`: from `utm_source`; defaults to `google` when gclid present
- `campaign_medium`: from `utm_medium`; defaults to `cpc` when gclid present
- `gclid`, `gbraid`, `wbraid`: Google Ads click IDs
Values persist in sessionStorage for the visit.

Payload (JSON):
```json
{
  "name": "", "phone": "+9715xxxxxxxx", "whatsapp": "", "email": "",
  "department": "ابتسامة هوليود",
  "campaign_source": "google", "campaign_medium": "cpc",
  "gclid": "", "gbraid": "", "wbraid": "",
  "source": "Lead form", "page": "Landing Page 3", "lang": "ar", "ts": "ISO date"
}
```

## To wire up
- Form endpoint: `formEndpoint` prop (POSTs JSON). Currently leads only log to console as `[lead]`.
- WhatsApp number: `waNumber` prop (placeholder `971500000000`).
- Phone display: `phoneDisplay` prop.
- Footer address and license number are placeholders in `copy()`.
- Logo loads from https://www.karismamc.com/images/greemlogo_main.png
- Fonts: Google Fonts (Alexandria, IBM Plex Sans Arabic, Manrope).
- Add conversion tracking (GTM / Google Ads) on successful submit in `submitForm()`.
