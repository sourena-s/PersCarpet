# نقشه‌کش فرش · PersCarpet

A browser-based designer that turns an image into a Persian carpet map (naqsheh) ready for weaving. The interface is in Persian (right-to-left), with English in parentheses for technical terms.

It is a single static page (`index.html`) with no build step. Open it in a browser, or serve the folder with any static host such as GitHub Pages.

## Features

- **Image:** upload, drag-and-drop or paste; rotate by 90°, straighten, mirror, and crop with the frame locked to the carpet's proportions.
- **Size and density:** traditional size presets (Pushti, Zaronim, Dozar, 6- and 12-metre); knot density in *raj* per 7 cm or 6.5 cm *gereh*; adjustable row-to-knot ratio. Shows knot counts, KPSI, knot size, weaving-time and wool estimates.
- **Colours:** a library of 32 traditional dye colours with Persian names and 10 regional palettes (Kashan, Tabriz, Isfahan, Nain, Kerman, Heriz, Qashqai, Baluch, Qom, Bijar). Use a whole palette, pick the best N colours for the image, or extract exact colours (k-means). Matching uses CIELAB ΔE or weighted RGB.
- **Image processing:** brightness, contrast, saturation, gamma; median denoise; Kuwahara simplification; Gaussian blur; unsharp mask; Floyd–Steinberg, Atkinson and Bayer dithering; despeckle (removes isolated knots); automatic dark outlines around motifs.
- **Pattern tools:** half and quarter-map symmetry, a border generator (guard stripes and six motifs), and abrash simulation in the rug preview.
- **Row reader (رج‌خوان):** steps through the map row by row with knot counts per colour, and can read a row aloud.
- **Saving and continuing later:** every change is saved automatically in the browser (IndexedDB), and reopening the page restores the last session: the image, crop and rotation, size and raj, palette, filters, pattern and export options. Under «پروژه‌های من» you can keep several named projects with thumbnails, open or delete them, and save a copy as a new version. A project can also be exported to a JSON file and opened on another computer.
- **Guided tutorial (راهنمای گام‌به‌گام):** a 36-step Farsi walkthrough that opens on the first visit and from the header button. It switches tabs by itself and points a bouncing yellow arrow at each control while explaining what it does, from uploading an image to exporting the weaving map.
- **Export:**
  - Printable PDF sheets (A4/A3) with 10-knot grid lines, rows numbered from the bottom, a centre axis and symbols for black-and-white printing.
  - A cover page with the colour and wool key and an index of the sheets.
  - Full map PNG and rug preview PNG.
  - Row-by-row *ta'lim* instructions (TXT), colour/wool list (CSV) and raw knot grid (CSV).
  - A project file (JSON) you can save and reopen.

## Dependencies

Loaded from CDNs at runtime: [jsPDF 2.5.1](https://github.com/parallax/jsPDF) for PDF export, and the Vazirmatn and Lalezar fonts from Google Fonts.
