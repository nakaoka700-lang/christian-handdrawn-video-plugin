---
name: create-christian-handdrawn-video
description: Create polished Christian hand-drawn narrative videos from audio and SRT subtitles, optionally matching a supplied reference image. Use when Codex must turn Chinese narration, sermons, devotionals, Bible teaching, gospel content, or faith-based scripts into an animated MP4 with GPT-generated illustrations of Jesus and expressive people, mandatory AI and user illustration approval gates, synchronized varied captions, cinematic image motion, and Remotion rendering.
---

# Create Christian Hand-Drawn Video

Produce a complete editable Remotion project with a browser-based preview first. Do not render or export an MP4 by default. Let the user review, adjust, and polish the project in the web preview, and render/export only after the user explicitly requests it. Use the `imagegen` skill for illustrations and the `remotion-best-practices` skill for implementation. Read [production-guide.md](references/production-guide.md) before designing scenes.

## Workflow

1. Inspect the working folder for audio, SRT, reference images, and an existing Remotion project.
2. Measure the audio duration and parse the SRT into the `Caption` JSON format required by Remotion.
3. Divide the narration into narrative beats. Change the illustration after every 3–4 subtitle entries by default; use fewer only when a single sentence is unusually long and semantically complete.
4. Write a scene plan that maps exact subtitle ranges and timestamps to subjects, emotions, symbolic details, and camera motion.
5. Generate one distinct GPT illustration for every planned beat. Use any supplied image as a style reference, not an edit target, unless explicitly requested otherwise.
6. Run the mandatory AI illustration self-review on every generated image. Reject and regenerate any image that fails subtitle-safe blank space, script-to-image fidelity, visual logic, anatomy, or style checks.
7. Present the complete AI-approved image set to the user for review and pause. Do not copy images into `public/`, build the Remotion timeline, or continue video production until the user explicitly approves the blank space, people, and related visual elements.
8. Apply every requested correction non-destructively, rerun AI self-review on each revision, and resubmit revised images for user approval. Approval applies only to the exact reviewed version; never treat approval of an earlier version as approval of a revision.
9. After explicit user approval, copy every approved image into the project's `public/` folder. Never leave project assets only in the generated-images directory.
10. Build or update the Remotion composition, synchronize audio and subtitles, add image motion and scene transitions, then launch a browser-based Remotion Studio/web preview.
11. Inspect at least the opening, one middle scene, a transition, and the ending in the preview at full resolution. Fix text collisions, weak storytelling, mismatched art, abrupt motion, or empty frames.
12. Type-check and deliver the working web preview plus editable source. Do not render or export a video unless the user explicitly requests it after review.
13. When export is explicitly requested, render H.264/AAC, verify codec, dimensions, audio stream, and duration, and use versioned filenames such as `video-v2.mp4`.

## Preview-first delivery

- Treat browser preview as the default completion state.
- Start Remotion Studio or an equivalent local web preview and provide the preview URL.
- Keep scene timing, captions, motion, and assets editable so the user can adjust and polish them before export.
- Never begin a full video render merely because the composition is ready.
- Render stills only when needed for quality assurance; they do not authorize a full MP4 export.
- Export only after an explicit user instruction such as “渲染”, “导出”, or “生成成片”.

## Non-negotiable illustration rules

- Use GPT image generation for every character-based narrative scene.
- Unless the narration is explicitly historical or biblical, depict Chinese believers as unmistakably contemporary people with modern hairstyles, ordinary present-day clothing, and contemporary settings. Do not let Jesus' biblical clothing cause surrounding Chinese characters to be rendered in hanfu, robes, topknots, or other ancient-Chinese styling.
- Show a complete, recognizable Jesus where the script calls for Jesus: shoulder-length hair, gentle beard, expressive face, natural hands, flowing robe, and context-appropriate posture.
- Include expressive people, believable anatomy, facial emotion, clothing folds, props, setting, and symbolic details grounded in the exact lines being narrated.
- Prefer refined warm ivory paper, sepia/brown pen-and-ink line art, delicate hatching, graceful composition, and restrained red accents when matching this established style.
- Preserve generous negative space in the subtitle zone.
- Never substitute crude SVG people, stick figures, thick geometric icons, or generic symbolic diagrams for requested narrative illustration.
- Use SVG/CSS only for supporting accents such as masks, brush strokes, glows, particles, or simple transition elements.
- Generate each distinct scene separately. Do not reuse one image for a long passage merely by changing captions.

## Scene pacing

- Default to one new illustration per 3–4 subtitle entries.
- Read the full prose/script before grouping SRT entries. When one complete sentence has been split into many short SRT cues, treat the sentence's semantic unity as more important than the raw cue count and choose the illustration count flexibly.
- Let semantic boundaries determine the exact cut: problem, cause, turning point, promise, consequence, and conclusion should normally receive different images.
- When a passage contains ordered, contrasted, or cumulative clauses with distinct visual subjects—such as "first...second...", "child...servant...", "not...but...", or a sequence of actions—do not collapse them into one simultaneous illustration if that would reveal a later idea early. Create separate images or staged layers and synchronize each visual entrance to the exact clause it represents. The final combined image may appear only when the narration explicitly unites the ideas.
- Overlap adjacent scenes by roughly 0.5–1 second for a gentle crossfade.
- Within a scene, apply one restrained motion direction: slow push-in, slow pull-out, or horizontal pan.
- Alternate motion direction between nearby scenes. Avoid identical continuous zooms throughout the video.
- Keep movement subtle enough that line art remains readable.

## Subtitle motion

Use an upright, elegant Chinese regular-script typeface such as `Kaiti SC`, `STKaiti`, or `KaiTi`, following the refined calligraphic character of the supplied reference image. Keep the weight substantial enough for video readability without looking like a rigid Song typeface. Render text in dark ink with only a faint, soft natural shadow. Do not use text strokes, outlines, white edge glows, backing panels, or subtitle background gradients.

Treat subtitles as hero text, not small explanatory captions. At 1920×1080, use a conspicuous display scale comparable to the main visual headline. Keep each displayed subtitle on one line by default. When an original SRT cue is too long to remain both large and collision-free, divide it into consecutive semantically complete single-line display fragments inside the original cue timing; never solve the problem merely by shrinking it into ordinary caption text. Preserve all source words and punctuation. Break only at complete lexical and semantic boundaries. Never split a multi-character word, fixed expression, name, theological term, or grammatical unit merely to satisfy a character count; for example, `艰难` must never become `艰` / `难`. Read the complete sentence and neighboring cues before choosing every break.

Place every hero line wholly inside its scene's deliberately empty light region. Never overlap faces, hair, hands, bodies, Bibles, crosses, furniture, symbolic props, architecture, or other meaningful/high-contrast illustration details. Use a regular-script font, a restrained natural shadow, and muted-red color on genuinely important theological words. Keep unimportant words in dark ink and avoid excessive highlighting.

Treat subtitle placement as composition-aware art direction, not a fixed corner preset. Preserve the hero-text size baseline first, then position each line flexibly inside the actual negative space of its approved scene. Prefer a varied visual rhythm across scenes and keep the subtitle's visual center in the middle portion of the Y axis whenever the illustration permits; do not uniformly shrink or tuck captions into the four corners. The position may shift left, center, or right and move moderately above or below the exact vertical midpoint to suit the scene, but it must remain prominent, balanced with the illustrated focal point, and wholly clear of every meaningful visual element throughout camera motion and crossfades.

Rotate among these entrance treatments:

- progressive character writing;
- horizontal mask reveal;
- left or right slide-in;
- scale overshoot and settle;
- vertical reveal with a red brush underline.

Use at most one main entrance treatment per subtitle entry. Reserve the brush underline and stronger bounce for important lines or keywords. Keep most movement within roughly 8–18 frames and maintain a stable reading period. Do not animate every character aggressively or combine several strong effects in the same cue.

Highlight only semantically important words in muted red. Keep all subtitle text within video-safe margins and ensure contrast primarily through the illustration's negative space and a faint soft shadow.

## Quality gate

### Mandatory AI illustration self-review

Review every generated or revised image at full resolution before showing it to the user. Record a pass/fail result for each scene and reject the image if any item fails:

- **Subtitle-safe blank space:** Confirm the planned subtitle zone is genuinely plain and light, large enough for the longest assigned subtitle, and free of faces, hair, hands, props, bright highlights, high-contrast edges, or dense linework.
- **Script-to-image fidelity:** Compare the image with the exact assigned subtitle lines. Confirm the correct narrative beat, era, people, emotion, action, relationships, setting, and theological category are present, with no later clause or future action revealed early.
- **Visual-element logic:** Verify every object has a plausible purpose, scale, orientation, placement, and relationship to the people and setting. Reject impossible, malformed, floating, duplicated, merged, anachronistic, or semantically confusing props—even when human anatomy is correct.
- **People and anatomy:** Count visible people, arms, hands, fingers, legs, and faces. Confirm natural poses, gaze, grip, contact, and interaction with all nearby objects.
- **Series consistency and cleanliness:** Confirm the required illustration style, palette, contemporary-versus-biblical clothing rules, framing, and negative-space strategy. Reject unwanted text, watermarks, logos, and unexplained visual symbols.

Do not rationalize a questionable element as symbolism. If a reasonable viewer could mistake it for a generation error or illogical object, regenerate or precisely edit the image, then repeat the entire self-review.

### Mandatory AI hero-subtitle self-review

After building the timeline, render and inspect a full-resolution peak-opacity frame for every displayed subtitle fragment, including every fragment created from a long SRT cue. Reject and revise the subtitle layout if any item fails:

- **Hero scale:** Confirm the line reads as prominent headline text at normal video viewing size. Reject ordinary small-caption sizing.
- **Single-line integrity:** Confirm the displayed fragment occupies exactly one line with no wrap, orphan character, or punctuation-only line. If necessary, split the source cue into consecutive semantic fragments without deleting or rewriting its wording.
- **Semantic and lexical break integrity:** Recombine all fragments and confirm they reproduce the source exactly, then read every fragment in context. Reject any split that truncates a word, fixed phrase, name, theological expression, modifier-head unit, predicate-object unit, or other complete thought. Reject orphan characters, orphan words, punctuation-only fragments, and mechanically character-counted breaks. A fragment may be short only when the source itself is a complete deliberate utterance and the assigned illustration remains visible.
- **Zero visual overlap:** Confirm the complete glyph area and shadow remain inside plain negative space and do not touch or cover any person, face, hair, limb, Bible, cross, prop, architectural edge, or dense/high-contrast linework.
- **Typography:** Confirm an upright Chinese regular-script face (`Kaiti SC`, `STKaiti`, or `KaiTi`), substantial readable weight, and a restrained soft shadow are visibly present. Reject Song-style, sans-serif, outlined, glowing, boxed, or gradient-backed subtitles.
- **Keyword emphasis:** Confirm meaningful theological keywords are selectively differentiated in muted red while the remaining text stays dark ink. Reject missing emphasis on an obvious key phrase or indiscriminate coloring of ordinary words.
- **Safe margins and stability:** Confirm the line remains within video-safe margins throughout its entrance, stable reading period, exit, camera motion, and adjacent scene crossfade—not only in a single static frame.
- **Composition-aware position:** Confirm the position responds to the scene's real negative-space geometry, preserves the hero-text size baseline, and normally occupies the middle Y-axis band rather than being mechanically parked in a corner. Review visual balance and placement variety across adjacent scenes. Reject a position that is technically empty but visually cramped, corner-bound, weak, repetitive, or disconnected from the composition.
- **No blank-storyboard orphan:** Inspect the entrance, peak, stable, and exit frames of every fragment, especially at scene transitions. Reject any lone character, word, short clause, or sentence that appears on a blank paper wash, empty transition card, missing-image frame, or otherwise unillustrated storyboard. Keep the relevant approved illustration visibly present behind every subtitle fragment; if a transition or split creates an orphan, revise the split, timing, or transition and rerun the full gate before continuing.

Record pass/fail results by scene and subtitle fragment. Do not deliver the Studio preview while any fragment fails this gate.

### Mandatory user illustration approval

After all images pass AI self-review, show the complete generated image set to the user in scene order with scene numbers and assigned subtitle ranges. Ask the user to review at minimum:

- subtitle-safe blank regions;
- every person's face, limbs, hands, fingers, pose, clothing, and era;
- props, symbols, paths, furniture, architecture, and other visual elements;
- image-to-script meaning and overall series consistency.

Pause after presenting the images. Continue only when the user explicitly approves the image set or explicitly approves each remaining corrected image. Silence, partial feedback, approval of the scene plan, or approval of a previous image version does not authorize the next video-production step.

When the user reports an issue, identify the exact source image and exact revised image. Preserve the original, make a versioned non-destructive edit, explain precisely what changed, rerun AI self-review, and show the revised image—not the unchanged original—for approval. Do not replace project assets or resume Remotion work until the revised image is explicitly approved.

Reject and regenerate an illustration if it has malformed hands or faces, missing narrative subjects, inconsistent style, unwanted text, watermarks, crude anatomy, or insufficient subtitle space.

Before accepting every character illustration, inspect all visible arms, hands, fingers, faces, and character count at full resolution. Count limbs explicitly; a person with a duplicated arm, third hand, fused fingers, or other anatomy error must never enter the Remotion timeline.

Render a representative frame from every newly generated scene with its real subtitle, then run the hero-subtitle gate on every displayed fragment. Reject or recompose any scene where subtitle glyphs or shadows overlap a face, hair, hand, body, Bible, cross, prop, architectural edge, high-contrast object, or dense linework. Prompt for a completely plain light subtitle-safe region when positional adjustment or semantic cue splitting cannot produce clean readability.

For theological relationship language, preserve the script's category precisely. "God the Father and his children" is a spiritual covenant relationship, not an ordinary earthly parent-child scene unless the script explicitly uses a human-family analogy. Prefer a modern believer in prayer, Christ as mediator when appropriate, and reverent heavenly light or an open way to symbolize the Father's presence; do not anthropomorphize the Father casually or substitute sentimental human-family intimacy.

Reject the video draft if:

- any illustration remains unchanged across more than four ordinary subtitle entries;
- Jesus is represented only by a cross or abstract icon when the narration calls for a character scene;
- subtitles rely only on fade-in/fade-out;
- caption effects feel frantic or compete with narration;
- camera motion is static throughout or uses the same zoom repeatedly;
- subtitles overlap faces or key story details.

Deliver the browser preview URL, editable source path, generated scene assets, and a short summary of scene count and motion treatments. Deliver an MP4 and representative preview still only when the user explicitly requests export.

## Optional post-export disk cleanup

Offer disk cleanup only after an explicitly requested MP4 export has completed and the exported file has passed codec, dimensions, audio-stream, and duration verification. Cleanup is a separate optional phase; never let it alter, delay, or replace the existing illustration approval, preview, export, or quality-gate workflow.

Before changing any files, perform a read-only inventory limited to the current video project's exact resolved directory. Report candidate paths grouped by category, their sizes, the proposed retention set, and the estimated recoverable space. Never scan unrelated projects for deletion candidates and never use unresolved variables, broad globs, the home directory, a workspace root, or another ambiguous path as a deletion target.

Classify candidates conservatively:

- **Always retain by default:** the verified final MP4, original audio, original SRT or transcript, user-supplied reference images, approved final illustrations used by the composition, editable source code, lockfiles, package manifests, and project configuration.
- **Basic cleanup candidates:** rejected or superseded generated-image versions, disposable contact sheets, rendered QA stills, logs, temporary files, and caches that are demonstrably associated only with the current project.
- **Standard cleanup candidates:** basic candidates plus reproducible dependency folders such as `node_modules` and reproducible intermediate render artifacts. Explain that dependencies must be reinstalled before future editing or rendering.
- **Deep cleanup candidates:** any approved production asset or editable project material. Never include these by default; enumerate every exact path and require a distinct second confirmation immediately before deletion.

Present the inventory and ask the user to choose basic, standard, deep, or no cleanup. A request to render, export, finish, save space, or inspect disk usage is not deletion approval. Proceed only after the user explicitly approves the displayed cleanup level and exact current-project scope. If paths or candidate contents change after approval, stop, regenerate the inventory, and request approval again.

Prefer a recoverable move to the operating system's Trash when practical, and explain that disk space is not actually reclaimed until Trash is emptied. Permanent deletion requires explicit wording that authorizes permanent deletion. Never delete the verified final MP4, original user inputs, or the only copy of an asset. Never modify or delete this skill, any other skill, shared tooling, package-manager global caches, or files outside the current project as part of project cleanup.

After approved cleanup, verify that all promised retained files still exist, report the exact paths acted on and actual space affected, and record whether recovery is possible. If any retained file is missing or the final export no longer verifies, stop immediately and report the problem without attempting further cleanup.
