# Rewards Tiers Section

Shopify Liquid section displaying ninja-themed loyalty tiers with logged-in/logged-out states.

## Files

| File | Purpose |
|------|---------|
| `rewards-tiers.liquid` | Production Shopify section (drop into `sections/`) |
| `index.html` | Local HTML prototype (logged-out view) |
| `logged-in.html` | Local HTML prototype (logged-in view, Yellow Belt) |
| `ninjas/` | Ninja character images per tier + keychain/plushie previews |

## Shopify Integration

1. Copy `rewards-tiers.liquid` into your theme's `sections/` directory
2. Upload ninja images + `eye.png` to theme assets
3. Add section via Theme Customizer > Add Section > "Rewards Tiers"

## Customer Metafields

Logged-in behavior requires two Klaviyo metafields on the customer:

| Metafield | Example | Description |
|-----------|---------|-------------|
| `klaviyo.swell_vip_tier_name` | `Yellow Belt` | Current tier name (White Belt, Yellow Belt, Blue Belt, Black Belt) |
| `klaviyo.loyalty_nt_amount_cents` | `24101.0` | Cents remaining to reach next tier (displayed as $241.01) |

## Section Settings

**Top-level:**
- Section heading (text)
- Max width (range: 900–1600px, default 1400)
- Preview eye icon (image picker — used next to perks with preview images)

**Per tier block (up to 4):**
- Belt name, cash back %, requirement text
- Ninja image
- Header gradient start/end colors
- Header text color (dark/light)
- Perk icon background/color
- Up to 6 perks, each with optional preview image

## Logged-In Behavior

- **Current tier**: "CURRENT RANK" black banner, gradient outline ring with glow animation, card grows taller, "Spend $X more to reach [next tier]" text
- **Unlocked tiers** (below current): greyed out at 45% opacity, "Unlocked" label
- **Higher tiers**: standard appearance with requirement text
- **Mobile**: auto-scrolls to current tier card on load

## Active Card Styling

The active card uses:
- Full-width black banner at top
- `outline` with CSS variables `--ring-color` / `--ring-color-bright` set from the tier's gradient colors
- `@keyframes` pulse animation on the outline
- Negative margins to grow above/below adjacent cards while keeping body content aligned
- `:has()` selector boosts z-index on cards with active preview popups

## Mobile Carousel

- Horizontal scroll with snap
- Dot indicators below
- Lightbox overlay for preview images (full-screen dark overlay, tap anywhere to close)
- Hover effects disabled via `@media (hover: hover)`

## Color Palette

| Tier | Gradient | Text |
|------|----------|------|
| White Belt | `#F1F1F1` | Dark |
| Yellow Belt | `#FADD1D` | Dark |
| Blue Belt | `#2098F0` | Light |
| Black Belt | `#3A414A` | Light |
