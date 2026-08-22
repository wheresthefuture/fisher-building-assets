# Fisher Buildings Map — Data Entry Cheat Sheet

A quick reference for adding photos, clippings, and permits to each building in `data.js`.

---

## 1. Where images live

All files go in your GitHub repo's `main` folder. In `script.js`, this line points to it:

```js
const IMAGE_BASE =
  'https://raw.githubusercontent.com/USERNAME/REPO/main/';
```

> In `data.js` you only ever type the **filename** (e.g. `'savery-a.jpg'`).
> The code adds the full URL for you.

---

## 2. Ways to list an image

You can methods inside the same `images: [ ]` array.

### A) Simplest — just a filename (image only)
```js
images: ['savery-a.jpg']
```

### B) Rich image — add a caption and type
```js
images: [
  { file: 'schuyler-a.jpg', type: 'photo',    caption: 'The Schuyler, 1925' },
  { file: 'schuyler-b.png', type: 'clipping', caption: 'KC Star, Aug 1926' }
]
```

### Full example (mixed)
```js
images: [
  { file: 'schuyler-a.jpg',  type: 'photo',    caption: 'The Schuyler, 1925' },
  { file: 'schuyler-b.png',  type: 'clipping', caption: 'KC Star, Aug 1926' },
  { file: 'permit-4471.png', type: 'permit',   caption: 'Permit No. 4471' }
]
```

---

## 3. Field reference

| Field     | Required?         | What it does                                        |
|-----------|-------------------|-----------------------------------------------------|
| `file`    | ✅ Yes            | Filename in your `main` folder                   |
| `type`    | Optional          | `photo`, `clipping`, or `permit` (color-codes border)|
| `caption` | Optional          | Shows on hover + under the enlarged view            |

Border colors by type:
- **photo** → grey (default)
- **clipping** → olive green
- **permit** → mahogany red

---

## 4. Quick checklist for each building

- [ ] Upload the image/PDF files to GitHub `main`
- [ ] Add the `images: [ ]` array to that building in `data.js`
- [ ] Filenames match exactly
- [ ] Save / reload — hover the pin and click a thumbnail to test
