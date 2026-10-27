---
name: listing-telegram-album
description: Use when publishing a property or stay listing promo to Telegram as one forwardable media-album post with a structured caption and a carefully chosen hero photo.
---

# Listing Telegram album post

Build one Telegram **media album** (exactly three photos + caption on that same message) for a stay/property listing, ready for a human to forward to a public channel.

Keep brand names, chat IDs, phone numbers, and site URLs out of this skill. The calling routine or agent supplies those.

## Inputs the caller must provide

- Listing search/detail source (API, MCP, or scraped pages) and how to resolve: title, amenities with detail, guest reviews, price, capacity, rating, location (+ region if available), listing URL, photo URLs
- Selection criteria (e.g. fair price, high rating, enough reviews; weekday vs weekend city rules)
- Destination Telegram chat for staging (usually a private review group)
- Footer lines (phone, website, channel handle) exactly as the brand wants
- Recently used listing IDs to avoid repeats

## Select a listing

1. Search with the caller’s criteria and city rotation rules.
2. Prefer fair price + strong rating + enough reviews.
3. Skip IDs used recently.
4. Load full detail: features, comments, photos, pricing, capacity, rates.

## Caption (strict order)

Write the caption in the destination language. No meta preamble (“draft”, “preview”, template name). Only the post body.

1. **Title** — exact listing title; do not rewrite or shorten.
2. **Amenities** — detailed bullets (open vs covered parking, outdoor vs indoor/heated pool, etc.). Prefer a consistent bullet marker the brand uses.
3. **Guest comment** — only a clearly positive text review. Skip negative or empty. If none good, **omit the whole block**. Lightly rewrite for spelling/clarity; keep meaning.
4. **Listing link**
5. **Short location** including region when available (e.g. town, county)
6. **Price**
7. **Capacity**
8. **Rating** as `X.X / 5` (or locale equivalent like `X.X از ۵`) with one decimal

Then the caller’s footer lines exactly.

## Photos — exactly three

1. **Hero (showcase)** — the most attractive, inviting image after **visual** review of candidates. Amenities guide preference, but a weak amenity shot (bad pool photo, dark, cluttered) must not win hero. Hero is the product window display.
2. **Second and third** — next-best attractive shots of strong spaces/amenities named in the caption when quality allows.

Rules:

- Never bathroom, toilet, or kitchen-only shots.
- Reject weak, dark, or low-quality frames even if they match an amenity keyword.
- Optional light edit (brightness/contrast) only; do not fake the space.
- Order in the album: hero first, then the other two.

## Send — one message only

Send **one** Telegram `sendMediaGroup` / media-album message: three photos together, caption on the album (first item).

Do **not** send a separate text message plus individual photos. The point is one forwardable message.

If the connected Telegram tooling cannot send a media group, **stop and report**; do not fall back to multiple messages.

Do not post to the public channel unless the caller explicitly says so; default is the staging/review chat.

## Report back

Listing id/title/city, whether a comment was included, hero rationale in one line, destination message id(s), and confirm it was a single album message.

## Pitfalls

- Caption over Telegram’s caption length limit → shorten amenities first, never drop title or link.
- Photo URLs must be publicly fetchable HTTPS (or upload bytes the Bot API accepts); signed/expiring links fail.
- Rate limits: wait on `retry_after` before retrying.
- Never invent amenities, prices, ratings, or guest quotes.
