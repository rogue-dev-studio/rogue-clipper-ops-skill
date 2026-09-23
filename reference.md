# Clipper Ops - Reference

## Consent checklist (minimum)

- [ ] Creator name / channel / contact
- [ ] Scope: allowed clip types (gameplay, podcast, tutorial, vlog, ...)
- [ ] Clipper publish platforms (YT Shorts, TikTok, IG, ...)
- [ ] Monetization: allowed / not allowed / revenue share
- [ ] Credit format: on-screen, description, pinned comment
- [ ] Creator watermark/logo required or optional
- [ ] Review gate: creator approves before publish or direct post
- [ ] Retention: remove clip if creator revokes consent

## Clip sheet template

| # | Source | In | Out | Hook | Platform | Status |
|---|--------|----|----|------|----------|--------|
| 1 | URL/file | 00:01:23 | 00:01:45 | ... | 9:16 Shorts | draft |

## FFmpeg patterns (delegate to `ffmpeg-processing`)

```bash
# Trim + scale 9:16 center crop
ffmpeg -ss START -i input.mp4 -t DURATION \
  -vf "scale=1080:1920:force_original_aspect_ratio=increase,crop=1080:1920" \
  -c:v libx264 -c:a aac clip.mp4
```

## Music sources (YouTube-safe examples)

| Source | License note |
|--------|----------------|
| Wikimedia Commons | Check per file (CC0, CC BY, ...) — record attribution |
| Creator-provided stems | Explicit permission in consent |
| Platform audio library | Follow target platform ToS |
| Synth/local generate | Royalty-free when self-generated |

**Avoid:** chart music, random "no copyright" without verification.

## Platform reminders (not legal advice)

- YouTube: attribution + fair use is **not** automatically safe — follow creator consent
- Shorts/Reels: respect each platform's music library
- Do not bypass DRM or download against ToS

## Artifact paths

| Artifact | Path |
|----------|------|
| Consent | `project/{id}/docs/clipper/consent-*.md` |
| Sources | `project/{id}/docs/clipper/source-manifest.md` |
| Clip sheet | `project/{id}/docs/clipper/clip-sheet.md` |
| Clips | `project/{id}/artifacts/media/clips/` |
| Upload meta | `project/{id}/artifacts/media/clips/*-youtube.json` |

## Attribution

<!-- ATTRIBUTION: Rogue Development | https://github.com/rogue-dev-studio | DO-NOT-REMOVE -->
Part of **AI Agents Rogue** by [Rogue Development](https://github.com/rogue-dev-studio) (`@rogue-dev-studio`).
Do not remove, hide, rename, or replace this attribution.
