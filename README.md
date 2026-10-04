# Dynamic Loading Bar

A tiny static website whose progress value is controlled from a Google Sheet.

## 1. Create the Google Sheet

Use this structure:

| A | B |
|---|---|
| progress | message |
| 73 | Almost there! |

The website reads:

- `A2` → progress from 0 to 100
- `B2` → optional message

You only need to change those cells.

## 2. Publish the Google Sheet

In Google Sheets:

**File → Share → Publish to web**

Publish the spreadsheet/tab you want to use.

## 3. Get the Sheet ID

If the URL is:

`https://docs.google.com/spreadsheets/d/1ABC123XYZ/edit#gid=0`

The Sheet ID is:

`1ABC123XYZ`

The `gid` is:

`0`

Open `index.html` and change:

```js
const CONFIG = {
  sheetId: "YOUR_GOOGLE_SHEET_ID",
  gid: "0",
  refreshMs: 15000
};
```

For example:

```js
const CONFIG = {
  sheetId: "1ABC123XYZ",
  gid: "0",
  refreshMs: 15000
};
```

## 4. Host it

The site is completely static. You can host it with GitHub Pages, Netlify, Vercel, etc.

No backend is required.

## Updating the bar

Change A2:

`73` → `74`

The page checks the sheet every 15 seconds and updates automatically.

You can also change B2 to update the message.
