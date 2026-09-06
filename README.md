# Daily Report Tables

One YAML file per platform defining its daily report table — the metrics in display order,
each with the exact `label`, a raw `field` or a `formula`, and `headline: true` on the
platform's native efficiency metric.

| File | Headline metric | Notes |
|---|---|---|
| [amazon.yaml](amazon.yaml) | **ACOS** | ROAS shown as its reciprocal |
| [flipkart.yaml](flipkart.yaml) | **ROI** (includes indirect sales) | Direct ROI beside it; impressions are called Views. No ACOS, no ROAS label |
| [meta.yaml](meta.yaml) | **ROAS** | Meta has no ACOS. Clicks = link clicks; CTR/CPC on the link basis |
| [google.yaml](google.yaml) | **Conv. Val / Cost** | Google's own label — no column named ROAS, no ACOS |
| [shopify.yaml](shopify.yaml) | **CVR** | store ledger, all channels — no ad-efficiency metrics |

Rules: each platform keeps its own vocabulary — never mix. Total rows recompute every rate
from summed counts, never averaged.
