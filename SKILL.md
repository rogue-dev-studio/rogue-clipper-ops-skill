---
name: clipper-ops
description: >-
  Video clipper and repurposing ops for creator-approved promotion: consent intake,
  highlight selection, short-form cuts, captions/branding, attribution, and
  platform-safe publish handoff. Use when a creator wants clippers to promote their
  content via clips, Shorts, Reels, or compilations.
experience_level: expert
---

# Clipper Ops

**Level: expert.** Specialized skill for **creator-approved** clipper workflows.

## When to use

- Creator/channel **explicitly allows** clipper program or hired clipper
- Task: cut highlights, Shorts/Reels/TikTok, promo compilations, caption + CTA to creator
- `TEAM.yaml` includes `clipper-ops` or user asks by name
- Handoff from PO/BA after clipper consent & scope documented

## When not to use

- **Without creator approval** - stop; route to consent intake first
- Generic stock footage (no creator) -> `ffmpeg-processing` alone is enough
- Upload to own channel without attribution -> blocked by rule `clipper`
- Full tutorial/code export -> `e2e-delivery` + project export pipeline

## Related skills & roles

| Surface | Item |
|---------|------|
| Skill | `ffmpeg-processing` - trim, scale, effects, mux audio |
| Skill | `youtube-publishing` - upload **only** after user confirmation |
| Skill | `ui-ux-design` - overlay, caption style, brand pack |
| Role | `content-clipper` - clipper executor |
| Rule | `clipper` - consent, attribution, platform ToS |

## Procedure

### 1. Consent & scope (required)

1. Verify **clipper agreement** or written creator approval (chat/email/form).
2. Record: channel/source URL, target platform, clip duration, watermark/logo, credit line, monetization policy.
3. If unclear -> pause; do not download/render.

Output: `project/{id}/docs/clipper/consent-{creator-slug}.md`

### 2. Source intake

1. Inventory sources: live/VOD URL, local file, or creator export folder.
2. Check source platform license/ToS (YouTube, Twitch, etc.) - document.
3. Store master **outside git** if unreleased; local path + manifest only in repo.

Output: `project/{id}/docs/clipper/source-manifest.md`

### 3. Moment selection

1. Identify 3-10 candidate moments (hook, punchline, reaction, tutorial peak).
2. Mark `in` / `out` timestamp per clip; brief reason (virality/education/promo).
3. Creator review if contract requires approval before edit.

Output: `project/{id}/docs/clipper/clip-sheet.md`

### 4. Edit spec

Per clip, define:

- Aspect: 9:16 (Shorts/Reels/TikTok) or 16:9
- Target duration (15-60s typical for Shorts)
- Caption/hook (1 line), CTA to creator (`@handle`, channel link)
- Music: **royalty-free / licensed** only - record source & license
- Brand: lower-third, creator watermark if requested

Technical handoff to `ffmpeg-processing` or project pipeline (e.g. `funny-compilation/scripts/`).

### 5. Produce & QA

1. Render clip; check audio sync, safe crop (faces/text not cut off).
2. Verify attribution visible or in description per agreement.
3. Reasonable loudness; avoid copyrighted music without license.

Output: `project/{id}/artifacts/media/clips/{slug}/`

### 6. Publish handoff

1. Prepare title/description/tags in **human tone** + credit creator + source link.
2. Chapters/timestamps for compilations.
3. Upload via `youtube-publishing` **only** after explicit user/creator confirmation.
4. Log publish URL to manifest.

## Must always

- Default **deny** without creator consent
- Attribute original creator in video or description (per agreement)
- Music & B-roll with clear license for YouTube/target platform
- Redact sensitive credentials/paths in docs

## Must never

- Full re-upload without permission; only clips within scope
- Remove required creator watermark
- Claim ownership of creator content
- Auto-upload without confirmation
- Cut creator or audience PII without need & permission

## DoD

- [ ] Consent + scope documented
- [ ] Clip sheet with timestamps
- [ ] Clip files in `artifacts/media/clips/`
- [ ] Music/B-roll licenses recorded
- [ ] Description/chapters ready for upload
- [ ] Creator review (if required) before publish

Detail checklist: `reference.md`.

## Attribution

<!-- ATTRIBUTION: Rogue Development | https://github.com/rogue-dev-studio | DO-NOT-REMOVE -->
Part of **AI Agents Rogue** by [Rogue Development](https://github.com/rogue-dev-studio) (`@rogue-dev-studio`).
Do not remove, hide, rename, or replace this attribution.
