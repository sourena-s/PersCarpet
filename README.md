# نقشه‌کش فرش · PersCarpet

A browser-based designer that turns an image into a Persian carpet map (naqsheh) ready for weaving. The interface is in Persian (right-to-left), with English in parentheses for technical terms.

It is a single static page (`index.html`) with no build step. Open it in a browser, or serve the folder with any static host such as GitHub Pages.

## Features

- **Sample library:** 17 traditional designs, filterable by region (Kashan, Tabriz, Isfahan, Nain, Kerman, Heriz, Bijar, Saraband, Qashqai, Bakhtiari, Baluch, Turkmen, Qom, Sarouk) and design type (lachak-toranj medallion, shah abbasi, floral, garden and panel, geometric, herati, boteh, prayer and tree of life, gabbeh, pictorial). Sixteen are drawn procedurally; one is a detailed pictorial Isfahan-style medallion carpet with birds and landscape cartouches (`samples/isfahan-pictorial.js`, loaded on demand). Its image was rebuilt as a true quarter map: the top half was aligned left-right (dense optical flow, a few pixels) and averaged into an exact left-right consensus with crisp detail, and the bottom half is that top half inverted, so the carpet is exactly four-way symmetric. It was colour-graded (local contrast, deeper indigo, richer reds and golds, clean warm ivory), then upscaled with an EDSR super-resolution network to the knot grid of a 200 × 293 cm carpet at raj 50 (6.5 cm gereh): 1538 × 2254 px, one pixel per knot, loaded uncropped so no resampling happens in the app. Guard stripes and frame lines were detected and straightened individually (position wobble along each line reduced to about one knot) without warping the scenes. Each sample sets suitable size, raj, palette, symmetry and border.
- **Open-access museum carpets:** search the public-domain (CC0) collections of [The Metropolitan Museum of Art](https://www.metmuseum.org/hubs/open-access) and the [Cleveland Museum of Art](https://openaccess-api.clevelandart.org/) for historic carpets (by keyword or quick chips such as Kashan, Heriz, garden carpet, prayer rug). A chosen carpet loads with its real dimensions and photo-suited filters, and its source is credited. Images without CORS headers are fetched through the open-source [images.weserv.nl](https://images.weserv.nl/) proxy.
- **Image:** upload, drag-and-drop or paste; rotate by 90°, straighten, mirror, and crop with the frame locked to the carpet's proportions.
- **Size and density:** traditional size presets (Pushti, Zaronim, Dozar, 6- and 12-metre); knot density in *raj* per 7 cm or 6.5 cm *gereh*; adjustable row-to-knot ratio. Shows knot counts, KPSI, knot size, weaving-time, wool and cost estimates.
- **Colours:** a library of 43 traditional dye colours with Persian names and 15 regional palettes (Kashan, Tabriz, Isfahan, Nain, Kerman, Heriz, Qashqai, Baluch, Qom, Bijar, Sarouk, Senneh/Saraband, Bakhtiari, Turkmen, Gabbeh). Colours that end up unused after a palette fit are removed automatically. Use a whole palette, pick the best N colours for the image, or extract exact colours (k-means). Matching uses CIELAB ΔE or weighted RGB.
- **Image processing:** brightness, contrast, saturation, gamma; median denoise; Kuwahara simplification; Gaussian blur; unsharp mask; Floyd–Steinberg, Atkinson and Bayer dithering; despeckle (removes isolated knots); automatic dark outlines around motifs.
- **Knot analysis:** weaving difficulty, colour changes per row, average run length, isolated single knots, left-right and top-bottom symmetry (with a suggestion to print a half or quarter map), and warnings for near-identical colours with a one-click merge.
- **Pattern tools:** per-sample symmetry masks (four-way / left-right / free per knot) for image samples that ship one, repeat layout (tile the cropped motif across and down, with optional mirroring), half and quarter-map symmetry, a border generator (guard stripes and six mirror-symmetric motifs), and abrash simulation in the rug preview.
- **Row reader (رج‌خوان):** steps through the map row by row with knot counts per colour, and can read a row aloud.
- **Saving and continuing later:** every change is saved automatically in the browser (IndexedDB), and reopening the page restores the last session: the image, crop and rotation, size and raj, palette, filters, pattern and export options. Under «پروژه‌های من» you can keep several named projects with thumbnails, open or delete them, and save a copy as a new version. A project can also be exported to a JSON file and opened on another computer.
- **Guided tutorial (راهنمای گام‌به‌گام):** a 39-step Farsi walkthrough that opens on the first visit and from the header button. It switches tabs by itself and points a bouncing yellow arrow at each control while explaining what it does, from uploading an image to exporting the weaving map.
- **Export:**
  - Printable PDF sheets (A4/A3) with 10-knot grid lines, rows numbered from the bottom, a centre axis and symbols for black-and-white printing.
  - A cover page with the colour and wool key and an index of the sheets.
  - Full map PNG and rug preview PNG.
  - Row-by-row *ta'lim* instructions (TXT), colour/wool list (CSV) and raw knot grid (CSV).
  - A project file (JSON) you can save and reopen.

## Developer

Designed and developed by **سورنا سهیلی‌نژاد** (Sourena Soheili-Nejad).

## Dependencies

Loaded from CDNs at runtime: [jsPDF 2.5.1](https://github.com/parallax/jsPDF) for PDF export, and the Vazirmatn and Lalezar fonts from Google Fonts.
