# Attendance Mania

A single-page attendance tracker for the 75% rule. Add your subjects, log each class, and see how many classes you can skip, or how many you must attend in a row to get back to 75%.

## Run it

No build step. Open `index.html` in any modern browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

Tailwind CSS and the font load from CDNs, so you need an internet connection on first load.

## Features

- Add, edit and delete subjects with starting counts (classes held, classes attended)
- Present, Absent and Cancelled/Holiday buttons per subject, with undo and a recent-activity strip
- Exact percentage plus a safe-to-skip count (at or above 75%) or a classes-to-attend count (below 75%)
- Green "Safe" and red "Shortage" badges, a bar with a 75% marker, and an overall summary
- Light and dark theme (follows your system, remembers your choice)
- Everything is saved in your browser's `localStorage`

## The math

With `A` attended and `T` held:

- Safe to skip: `floor((100A - 75T) / 75)` when `100A >= 75T`
- Must attend: `ceil((75T - 100A) / 25)` when `100A < 75T`

To change the target, edit `TARGET` at the top of the script in `index.html`.
