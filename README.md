# Manager Class Schedules

Static site for the Virginia Tech basketball managers' weekly class schedules.
Hosted on GitHub Pages — no sign-in required to view.

**Live site:** https://vtmbb-stats.github.io/manager-schedules/

## How it works

- `index.html` — the whole app (one file, no build step). Fetches `schedule.json` on load.
- `schedule.json` — the data. **This is the only file you edit to update the schedule.**

The page shows:
- **Now** — who is in class at this moment (or any date/time you pick), plus a
  scrolling channel-guide timeline with a live "current time" line.
- **Find a window** — a free/busy heat grid and a search for open windows across the week.
- **By manager** — one manager's full week and totals.
- **All classes** — the plain list.

## Editing `schedule.json`

```jsonc
{
  "semester": "Fall 2026",
  "updated": "2026-09-02",          // bump this each edit — shows as "Schedule updated ..."
  "note": "",                        // optional line shown on the All classes tab
  "managers": [
    { "name": "First Last" },        // order here sets each manager's color
    { "name": "Other Name", "color": "#3F6DAB" }   // color optional
  ],
  "classes": [
    {
      "manager": "First Last",       // must match a name in "managers" exactly
      "course":  "FIN 4154",
      "days":    "MWF",              // any of M T W R F (R = Thursday), e.g. "TR", "MW"
      "start":   "10:10",           // 24-hour HH:MM
      "end":     "11:00",
      "room":    "Pamplin 1040"      // building + room, optional
    }
  ]
}
```

One entry per class meeting pattern. A class that meets MWF is a single entry with
`"days": "MWF"`. If a class meets at different times on different days, make two entries.

**Online classes:** synchronous (live) online classes count — enter them with
`"room": "Online (Zoom)"`. Asynchronous online classes are left out entirely.

**Rooms use full building names** (not HokieSpa abbreviations). Common ones:

| Abbrev | Full name |
|---|---|
| PAM | Pamplin Hall |
| HUTCH | Hutcheson Hall |
| LITRV | Litton-Reaves Hall |
| SURGE | Surge Building |
| CFA | Center for the Arts |
| DDS | Data & Decision Sciences Building |
| USLB | Undergraduate Science Laboratory Building |
| SQUIR | Squires Student Center |
| GLCDB | Graduate Life Center at Donaldson Brown |
| MCB | McBryde Hall |
| TORG | Torgersen Hall |
| WMS | Williams Hall |
| RAND | Randolph Hall |
| GOODW | Goodwin Hall |
| DAVID | Davidson Hall |
| HAHN | Hahn Hall |
| NCB | New Classroom Building |

After editing, commit and push (or edit on github.com) — GitHub Pages redeploys in
about a minute, and viewers get the new data on their next load.
