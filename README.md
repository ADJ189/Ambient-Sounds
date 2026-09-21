# Ambient Sounds
-----------------------

Recorded ambient audio for [Session Clock](https://github.com/ADJ189/Session-clock) —
kept in this separate, lightweight repo instead of the main app's git
history so the app repo itself doesn't carry ~17MB of binary audio.

## Setup (one-time)

1. Push this repo to GitHub as a public repo (a fork/rename of this one is fine).
2. Tag a release: `git tag v1 && git push origin v1`.
3. In the main app's `src/soundfiles.ts`, set:
   ```ts
   export const AUDIO_CDN_BASE =
     'https://cdn.jsdelivr.net/gh/<you>/session-clock-sounds@v1';
   ```
   (jsDelivr auto-mirrors any public GitHub repo — no account, no billing
   tier, and it already sends `Access-Control-Allow-Origin: *` on every
   file, so there's no CORS configuration to do either.)

## Updating a file later

jsDelivr caches by tag, and an already-published tag's content is
permanently cached at the CDN edge — pushing new commits to `v1` won't
update what's served. Bump the tag (`v2`, `v3`, ...) and update
`AUDIO_CDN_BASE` to match whenever a file changes. Using `@main` instead
of a tag avoids the version bump, but jsDelivr can take up to 24h to
reflect a push to a branch reference, so a tag is the more predictable
choice for anything you want to see live quickly.

## Credits

These recordings are sourced from the [Moodist](https://github.com/remvze/moodist)
project's sound catalog (MIT-licensed code; audio assets are third-party),
re-encoded to Opus (~96kbps) for this app. Per Moodist's own README, its
sounds are licensed either under the
[Pixabay Content License](https://pixabay.com/service/license-summary/)
or [CC0](https://creativecommons.org/publicdomain/zero/1.0/) — both permit
commercial use with no attribution required, which is why no per-file
attribution list is included here (Moodist doesn't provide one either).

| Track id  | Source file            |
|-----------|-------------------------|
| rain      | rain/heavy-rain         |
| fire      | nature/campfire         |
| wind      | nature/wind             |
| forest    | nature/jungle           |
| cafe      | places/cafe             |
| library   | places/library          |
| waves     | nature/waves            |
| river     | nature/river            |
| waterfall | nature/waterfall        |
| thunder   | rain/thunder            |
| night     | animals/crickets        |
| birds     | animals/birds           |
