# Pic to Grid

Turn any image into a filled/empty grid layout for puzzle levels. Upload a picture, preview its silhouette, and copy the result as plain text to paste into the Unity Grid Manager tool.

**Live:** https://YOUR-SITE.pages.dev

A [NovaBytes](https://github.com/Harsh-Nova-190) tool.

## How it works

1. **Choose an image** (or drag and drop, or paste one).
2. **Step 1: Silhouette.** Adjust the threshold, invert, or click **Cut out subject (AI)** for normal photos. Click **Use this silhouette** when it looks right.
3. **Step 2: Grid.** Set the width and height (5 to 90). Click or drag on the preview to fix cells by hand.
4. **Copy grid text** or **Download .txt**.
5. In Unity, paste the text into **Import Layout from Text** and click **Import Layout**.

## Output format

Plain rows of `1` and `0`, one row per line. `1` is filled (cyan), `0` is empty (gray). The top line is the top row of the grid.

```
0001000
0011100
0111110
```

## Tips

- Dark shapes on a light background work best (silhouettes, logos, icons).
- For photos, use **Cut out subject (AI)**, then fine-tune the threshold.
- Crop the photo tightly around the subject before uploading for cleaner results.
- Keep "Match image proportions" on to avoid stretching. The Unity tool supports non-square grids.

## Running locally

The AI cutout needs a real web address, so opening `index.html` by double-click will not work. Run a local server instead:

```
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Tech

Single-file HTML, CSS, and JavaScript with no build step. The AI cutout runs fully in your browser using [Transformers.js](https://github.com/huggingface/transformers.js) (Apache 2.0) and the RMBG-1.4 model. The model downloads once (about 45 MB) and your images are never uploaded anywhere.

## License

Source code is private. The RMBG-1.4 background-removal model is licensed by BRIA AI for non-commercial use only. Check its [license](https://huggingface.co/briaai/RMBG-1.4) before using this tool commercially.
