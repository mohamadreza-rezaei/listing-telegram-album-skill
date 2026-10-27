# listing-telegram-album

Cursor skill that publishes a stay/property **listing promo as one Telegram media album** (hero + two supporting photos + structured caption) so a teammate can forward a single message.

## Install

Copy `.cursor/skills/listing-telegram-album/` into your project’s `.cursor/skills/`, or point your agent at this repo’s skill path.

## What it does

- Picks a listing from criteria you supply
- Writes a fixed-order caption (title → amenities → optional positive guest comment → link → location → price → capacity → rating → footer)
- Chooses **three** photos after visual review (hero = most inviting showcase; skip weak amenity shots)
- Sends **one** `sendMediaGroup` message — never separate text + photos

Brand details (chat IDs, phone, site, channel handle, APIs) belong in the **calling routine**, not in the skill.

## License

MIT
