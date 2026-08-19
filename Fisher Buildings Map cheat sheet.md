# Fisher Buildings Map — Data Entry Cheat Sheet

A quick reference for adding photos, clippings, and permits to each building in `data.js`.

---

## 1. Where images live

All files go in your GitHub repo's `/assets` folder. In `script.js`, this line points to it:

```js
const IMAGE_BASE =
  'https://raw.githubusercontent.com/USERNAME/REPO/main/assets/';
```

> In `data.js` you only ever type the **filename** (e.g. `'savery-a.jpg'`).
> The code adds the full URL for you.

---

## 2. The three ways to list an image

You can mix all three inside the same `images: [ ]` array.

### A) Simplest — just a filename (image only)
```js
images: ['savery-a.jpg']
```
Thumbnail = the image itself. Caption = the building name.

### B) Rich image — add a caption and type
```js
images: [
  { file: 'schuyler-a.jpg', type: 'photo',    caption: 'The Schuyler, 1925' },
  { file: 'schuyler-b.png', type: 'clipping', caption: 'KC Star, Aug 1926' }
]
```

### C) PDF (building permits)
```js
{ file: 'permit-4471.pdf', type: 'permit', caption: 'Building permit No. 4471',
  thumb: 'permit-4471-thumb.png' }   // optional preview image
```
- With `thumb:` → that image is the clickable thumbnail.
- Without `thumb:` → a clean "📄 PDF" tile appears instead.
- Clicking opens the PDF inline, plus an "Open / download PDF" link.

### Full example (mixed)
```js
images: [
  { file: 'schuyler-a.jpg',  type: 'photo',    caption: 'The Schuyler, 1925' },
  { file: 'schuyler-b.png',  type: 'clipping', caption: 'KC Star, Aug 1926' },
  { file: 'permit-4471.pdf', type: 'permit',   caption: 'Permit No. 4471',
    thumb: 'permit-4471-thumb.png' }
]
```

---

## 3. Field reference

| Field     | Required?         | What it does                                        |
|-----------|-------------------|-----------------------------------------------------|
| `file`    | ✅ Yes            | Filename in your `/assets` folder                   |
| `type`    | Optional          | `photo`, `clipping`, or `permit` (color-codes border)|
| `caption` | Optional          | Shows on hover + under the enlarged view            |
| `thumb`   | PDFs only, optional | Preview image for a PDF's thumbnail               |

Border colors by type:
- **photo** → grey (default)
- **clipping** → olive green
- **permit** → mahogany red

---

## 4. Image vs. PDF — which to use?

| Situation                                   | Best choice            |
|---------------------------------------------|------------------------|
| Single-page permit                          | Convert to PNG/JPG     |
| Multi-page permit                           | Keep as PDF            |
| Want fast loading + perfect mobile display  | Image                  |
| Want the true original to be downloadable   | Keep as PDF (+ `thumb`)|

**Making a PDF thumbnail:** screenshot the permit's first page, or export page 1
as PNG from any PDF viewer. Name it `something-thumb.png` and drop it in `/assets`.

---

## 5. File-naming tips

- Use lowercase, no spaces: `coronado-a.jpg`, not `Coronado A.jpg`
- Group by building with a consistent prefix: `schuyler-a`, `schuyler-b`, `schuyler-permit`
- Use `-thumb` suffix for PDF previews: `permit-4471-thumb.png`
- Match the filename in `data.js` **exactly** (capitalization counts on GitHub)

---

## 6. Quick checklist for each building

- [ ] Upload the image/PDF files to GitHub `/assets`
- [ ] For any PDF, optionally add a `-thumb.png` preview
- [ ] Add the `images: [ ]` array to that building in `data.js`
- [ ] Filenames match exactly (lowercase, no spaces)
- [ ] Save / reload — hover the pin and click a thumbnail to test
