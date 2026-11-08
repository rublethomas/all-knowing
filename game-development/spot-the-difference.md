# Spot the Difference - parked idea

Status: parked until the shooter ships.

## Approaches for making the image pairs (best first)

1. Procedural SVG scenes. Claude writes cartoon/pencil-style scenes as vector code. Each difference is a programmatic change (remove, recolor, move, resize an element), so the answer coordinates are exact and files are tiny. Risk: flat, clean look instead of hand-drawn
2. Public-domain/CC0 images edited with scripts (Pillow/OpenCV): inpaint to remove objects, recolor regions, paste patches. An automatic diff check confirms every difference is real and findable
3. Image-generation API with the same diff check. Best art, but costs money and the license terms need checking

AI models are weak at precise image editing, so the pipeline must verify differences rather than trust the model.

## Notes

- About 200 levels at ~150 KB per image pair is roughly 60 MB, fine for an AAB
- Check licenses (Openverse, Wikimedia, Pixabay). Record the source of every image
- Weaker retention than the shooter. Content-heavy
- Same monetization: rewarded hints, one-time ad removal
