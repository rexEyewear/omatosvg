# UGC plan — black gold-flake frame (top frame from sketchbook photo)

**Status:** waiting on Arcads API key (`./scripts/setup.sh`). Everything below is ready to run.

## Product

Oversized matte-black acetate eyeglasses, bold aviator-style silhouette. Lower third of
the front is transparent clear resin filled with gold-leaf flakes (black-to-clear fade).
Small round keyhole cutout at the bridge. Matte-black flat temples with silver pin rivets.

Reference images (local-only, gitignored except these force-added copies):
- `references/products/omato-black-goldflake-topframe.jpg` — cropped hero (use this)
- `references/products/omato-frames-sketchbook.jpg` — full original upload

## Phase 1 — UGC selfie still (Nano Banana 2)

Reference stack (order matters — identity anchor first):
1. `references/influencers/lena-brunette-long-straight-beauty-mark-brown-eyes-fair/01-hero-front.jpg`
2. `references/products/omato-black-goldflake-topframe.jpg`
3. `references/aesthetics/ugc-selfie/videoframe_4268.jpg`
4. `references/aesthetics/ugc-selfie/videoframe_5451.jpg`
5. `references/aesthetics/ugc-selfie/videoframe_9922.jpg`

### Prompt (drafted per ugc-product-selfie template)

```
Raw iPhone front-camera selfie video frame grab. A woman in her mid-20s with long
straight dark-brown hair and a small beauty mark, fair skin with visible pores, slight
unevenness in skin tone, minor undereye shadows, a hint of shine on the nose and
forehead from natural oils — the kind of skin you see on a real person's unfiltered
front camera. She is wearing oversized matte-black acetate glasses with a bold
aviator-style silhouette: the lower third of the frame is transparent clear resin
filled with visible gold-leaf flakes, and there is a small round keyhole cutout at the
bridge. The glasses match the product reference exactly — same black-to-clear gold-fleck
fade, same shape. She holds the phone with one extended arm, other hand lightly touching
the temple of the glasses as if she just put them on, mouth open mid-word with a genuine
excited expression, wearing an oversized ribbed beige sweater. Behind her a slightly
messy bedroom: unmade bed, string lights off, a jacket over a chair, charging cable on
the nightstand. Slight motion blur on hair strands, slightly overexposed highlights on
forehead and nose, visible image grain and noise, iPhone front camera wide-angle lens
distortion on the extended arm, slightly off-center framing tilted a few degrees, washed
out flat color grading, soft focus — nothing is tack sharp, uneven ambient indoor
lighting with one side of face slightly in shadow. No retouching, no beauty filter, no
studio lighting, not a professional photo, not overly polished, not perfectly composed,
not tack sharp. No airbrushed skin, no flawless complexion.
```

### Command

```bash
.claude/skills/nano-banana-image-ad/scripts/generate_image.py \
  --prompt "<prompt above>" \
  --aspect-ratio 9:16 \
  --n 3 \
  --image-ref references/influencers/lena-brunette-long-straight-beauty-mark-brown-eyes-fair/01-hero-front.jpg \
  --image-ref references/products/omato-black-goldflake-topframe.jpg \
  --image-ref references/aesthetics/ugc-selfie/videoframe_4268.jpg \
  --image-ref references/aesthetics/ugc-selfie/videoframe_5451.jpg \
  --image-ref references/aesthetics/ugc-selfie/videoframe_9922.jpg \
  --out ./generated/ugc-black-goldflake \
  --env-file .env
```

**Estimated cost:** 3 × ~0.03 credits ≈ **0.09 credits** (estimate from logged past calls —
confirm exact pricing in the Arcads platform).

Then: visual QA each variant (garbled detail, extra fingers, frame-shape drift vs the
product ref, identity drift), retry up to 2× if needed, user picks the winner.

## Phase 2 — animate approved still (Veo 3.1, startFrame)

Per the prompt library, UGC stills → video should use **Veo 3.1 `startFrame`** (Seedance/
Sora do not preserve the approved frame). Upload the approved still via presigned URL,
then `POST /v1/veo31/generate/video`, 720p, 9:16, with human-motion cues:

```
She talks excitedly to the camera about her new glasses: briefly breaks eye contact,
glances down as she taps the gold-flake lower rim of the frames, then looks back at
camera; slight head tilts while talking, raises eyebrows for emphasis; adjusts grip on
the phone; leans toward camera for emphasis. Handheld selfie shake throughout. No
subtitles, no captions, no text overlays.
```

**Cost:** not in the shipped log for veo31 — present the estimate at run time and confirm
in the Arcads platform before generating.

## Notes

- Character is swappable: any folder under `references/influencers/` (hero-front image
  first in the ref stack).
- If the gold-flake fade or keyhole detail drifts in generation, add the full sketchbook
  photo as a second product ref and name the details again in the retry prompt.
