# Advanced HTML5 QR Code Generator

This project is a **single-page HTML5 QR code generator** that runs entirely in the browser. It supports multiple content types, high‑resolution output suitable for printing, and download in **PNG** and **JPG** formats.

## Features

- Works fully offline in a modern browser (no server required)
- Uses pure HTML, CSS, and JavaScript
- Generates QR codes for:
  - Link (URL)
  - Text
  - E-mail (mailto with subject & body)
  - Phone Call (tel:)
  - SMS (sms: with message)
  - V-card (vCard 3.0)
    - Name (first/last)
    - Organization
    - Title
    - Phone
    - E-mail
    - Website
    - **Home address**
    - **Work address**
  - WhatsApp link (wa.me with pre-filled message)
  - Wi-Fi (WIFI: format, with encryption and hidden flag)
  - PDF link
  - App link (store / deep link)
  - Image URL
  - Video URL
  - Social Media URL (profile / post)
  - Event (ICS / VCALENDAR / VEVENT)
  - Generic “2D Barcode” (raw data)
- Configurable QR parameters:
  - Size: 256–2000 px (good for screen and print)
  - Error correction level: L / M / Q / H
- Preview area shows the exact encoded content (debug/verification)
- Buttons to download QR as:
  - **PNG**
  - **JPG**

## Files

- `qr_generator.html` – main and only file you need. Open it directly in your browser.

## How to Use

1. Save the HTML file (for example as `qr_generator.html`).
2. Open it with any modern browser (Chrome, Edge, Firefox, etc.).
3. In the **Content type** dropdown, select what kind of QR you want:
   - Link, Text, E-mail, V-card, Wi-Fi, Event, etc.
4. Fill in the fields for the selected type.
   - For **V-card**, you can use:
     - Home address only
     - Work address only
     - Or both (both will be encoded into the same vCard).
5. Choose:
   - **Size (px)** – for printing, values like 800–1500 px work well.
   - **Error correction** – `M` or `H` is recommended for print (more robust).
6. Click **Generate QR**.
   - The QR code appears in the **QR Preview** panel.
   - The exact text payload appears in the **Generated content** box (optional verification).
7. Click **Download PNG** or **Download JPG** to save the QR image.

## Notes on Printing Quality

- For labels, stickers, and business cards:
  - Use **800–1500 px** size.
  - Use **ECC H** when you expect damage / dirt / low contrast.
- When placing in another design (e.g., on a flyer):
  - Do not stretch or blur the QR.
  - Keep strong contrast between QR and background.
  - Ensure quiet zone (white margin) is preserved around the code.

## Technical Details

- QR generation handled by [`qrcodejs`](https://github.com/davidshimjs/qrcodejs) via CDN:
  - `https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js`
- QR image is rendered on an HTML `<canvas>` element, then exported with `canvas.toDataURL()` as:
  - `image/png`
  - `image/jpeg`
- V-card format: `VERSION:3.0` with:
  - `N:`, `FN:`, `ORG:`, `TITLE:`, `TEL;TYPE=CELL:`, `EMAIL;TYPE=INTERNET:`
  - `ADR;TYPE=HOME:;;...`
  - `ADR;TYPE=WORK:;;...`
  - `URL:`
- Event format: basic `VCALENDAR` + single `VEVENT` with `SUMMARY`, `DTSTART`, `DTEND`, `LOCATION`, `DESCRIPTION`.

## Browser Compatibility

- Designed for modern browsers that support:
  - ES5+ JavaScript
  - `<canvas>` element
- No special server, frameworks, or build tools are required.

## Customization

You can easily modify:

- **Default size** – change the `value` of `#sizeInput`.
- **Default error correction** – change selected option of `#eccSelect`.
- **Styling / colors** – adjust the CSS in the `<style>` section.
- Add or remove QR content types by editing:
  - The HTML blocks under `#fieldsContainer`
  - The `buildContent()` function in the `<script>` section.

---

Enjoy using your standalone **Advanced HTML5 QR Code Generator** for links, business cards, Wi-Fi access, events, and more.
