# Production Guide

## Scene-plan fields

Create a compact table with:

- scene number;
- SRT entry range;
- start/end time;
- narrative purpose;
- characters and expressions;
- setting and symbolic props;
- illustration prompt summary;
- camera motion;
- transition.

Aim for `ceil(subtitle_count / 3.5)` scenes, then adjust at semantic boundaries. For 40 subtitle entries, expect roughly 10–13 illustrations rather than four long scenes.

## GPT illustration prompt pattern

Use one built-in `image_gen` call per scene:

```text
Use case: illustration-story.
Asset type: 16:9 animated-video scene in a cohesive Christian hand-drawn series.
Input image: supplied image is a style reference only.
Narrated lines: "<exact relevant subtitle text>"
Primary scene: <translate the lines into a concrete character action>.
Characters: <Jesus and/or people, expressions, gestures, relationships>.
Setting and props: <details grounded in the narration>.
Contemporary character rule: unless the lines are explicitly historical,
Chinese believers must have modern hairstyles, present-day clothing, and
contemporary settings; Jesus alone keeps first-century biblical clothing.
Style: refined editorial sepia pen-and-ink on warm ivory textured paper,
expressive faces and hands, delicate hatching, elegant clothing folds.
Composition: landscape 16:9, upper subtitle zone mostly empty.
Palette: dark brown/sepia with tiny restrained muted-red accents.
Avoid: text, letters, watermark, logo, photorealism, stick figures,
crude SVG-like icons, thick geometric lines, malformed anatomy, duplicated
arms or hands, extra fingers, hanfu, topknots, ancient-Chinese styling.
```

Do not ask the image model to render subtitles. Render text in Remotion.

## Remotion composition pattern

- Put audio, SRT, and scene images in `public/`.
- Reference all assets with `staticFile()`.
- Use `<Img>` for illustrations and `<Audio>` from `@remotion/media`.
- Drive all motion from `useCurrentFrame()` plus `interpolate()`.
- Do not use CSS animations or CSS transitions.
- Crossfade images with overlapping opacity ramps.
- Apply gentle Ken Burns motion with separate `scale` and `translate` properties.
- Keep caption logic in its own component.

## Recommended motion ranges

- Scene crossfade: 15–30 frames.
- Slow image scale: approximately 1.02→1.08 over a scene.
- Horizontal pan: approximately 15–35 px at 1920×1080.
- Subtitle entrance: 8–18 frames.
- Subtitle exit: 4–8 frames.
- Keyword overshoot: approximately 0.85→1.08→1.
- Brush underline draw: 10–20 frames.

Treat these as starting points, not mandatory constants.

## Caption distribution

Use a calm repeating sequence such as:

1. character writing;
2. simple mask reveal;
3. soft slide;
4. stable scale settle;

Then insert a brush underline only on a theological turning point, quotation, or final conclusion. Avoid strong effects on consecutive short cues.

## Verification

Render stills near:

- the first spoken line;
- every major scene transition;
- the strongest red-keyword treatment;
- the final line.

Check that each frame has one obvious focal point, readable subtitles, accurate narrative imagery, consistent line-art style, and no important detail beneath the text.

After rendering, inspect with FFprobe and confirm H.264 video, AAC audio, expected 1920×1080 dimensions unless otherwise requested, and duration matching the audio/SRT endpoint.
