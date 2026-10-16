# Quiet Paper

The design system for Crumpet’s own look (`system`, `light` and `dark` — `data-look="crumpet"`). Named themes (Classic, Vapor, Desktop and the rest) keep their own frames. Quiet Paper is the default.

Content is the hero. Chrome is quiet and supportive. Power is available, not constantly present.

## Philosophy

- **Calm.** Nothing shouts. No thick rings, no heavy type, no decorative gradients on controls.
- **Content first.** The open note is a sheet of paper. Sidebar, list and toolbar recede so the writing can be read.
- **Progressive disclosure.** Everyday actions stay in reach. Styles, comments, outline, research, snapshots and the rest of the inspector stay closed until asked for. Multi-pane layouts are opt-in.
- **Apple-level restraint.** One accent, two materials, a short spacing scale, two corner sizes. If a treatment needs a third idea, it is probably too much.

## Materials

Two materials, used the same way everywhere.

| Material | Where | Light | Dark |
| --- | --- | --- | --- |
| Ambient wash | The screen behind the window | Honey glow at the top left, cool blue at the bottom right, over `#E7E8ED` | The same shapes, quieter, over `#101114` |
| Frost | Sidebar and icon rail | White at about 58% opacity, 28px blur | Near-black at about 55% opacity, 28px blur |
| Paper | Note list cards, the open note, dialogs, menus | `#FFFCF8` | `#221F1C` |
| Ink | Text on paper | `#1C1E23` | `#F3EFE8` |

The wash is atmosphere, not a picture. It must stay soft enough that a white sheet still feels like the brightest thing on screen.

## Colour tokens

Honey `#D4A257` is the only accent. It marks selection, the New Note plus, links and focus. It is never a large filled area except a small plus or a primary action on an empty page.

| Token | Light | Dark | Use |
| --- | --- | --- | --- |
| `--accent` | `#D4A257` | `#D4A257` | Honey |
| `--accent-ink` | `#6A5130` | `#E3C48A` | Text and icons in honey |
| `--accent-soft` | `#F8F1E4` | honey at 16% over paper | Selected washes, active toolbar buttons |
| `--on-accent` | `#2A1F0E` | `#2A1F0E` | Text on a solid honey control |
| `--wash` | honey radial + `#8FB3E8` radial + `#E7E8ED` | honey radial + deep blue radial + `#101114` | Screen background |
| `--side-bg` | `rgba(255, 252, 248, 0.58)` | `rgba(28, 26, 24, 0.55)` | Frost fill |
| `--page` / paper | `#FFFCF8` | `#221F1C` | Sheets, cards, menus |
| `--text` | `#1C1E23` | `#F3EFE8` | Primary ink |
| `--muted` | `#6E7380` | `#A39A90` | Secondary ink |
| `--line` | `rgba(28, 30, 35, 0.08)` | `rgba(255, 248, 240, 0.08)` | Hairlines |

Do not introduce a second accent for selection, status or links. Status on index cards (draft, revised, done) may keep a thin stripe because it carries meaning, not decoration.

## Spacing

Only these steps. Combine them; do not invent 6, 10, 14, 18 or 20.

| Token | Size | Typical use |
| --- | --- | --- |
| `--space-1` | 4px | Icon gaps, hairline stacks |
| `--space-2` | 8px | Inside a row, between cards |
| `--space-3` | 12px | Card padding, group gaps |
| `--space-4` | 16px | Section padding, sidebar groups |
| `--space-5` | 24px | Between regions |
| `--space-6` | 32px | Note title block, sheet padding |

## Corner radius

Two sizes. Nothing larger.

| Token | Size | Use |
| --- | --- | --- |
| `--r-control` | 8px | Buttons, rows, fields, menus, toolbar buttons |
| `--r-sheet` | 12px | Cards, the note sheet, the window, dialogs |

Circles are allowed for avatars and the New Note plus. They are not a third radius; they are round because the control is round.

## Typography

- **UI:** Onest (system UI as fallback), 13px. Weight 500 for names and controls, 400 for secondary lines. Do not use 700 or 800 in chrome.
- **Section labels:** 11px, weight 600, muted, no shouty tracking.
- **List title:** 22px, weight 600, slight negative tracking.
- **Note title:** 32px, weight 600, tracking about −0.03em, the same family as the note. One step of hierarchy above the body, not a poster.
- **Card title:** 15px, weight 600. Preview text 13px, muted, two lines.
- **Note body:** the person’s note font, 18px unless they choose otherwise. Line height stays comfortable (about 1.5).

Serif titles belong to the separate Paper and ink theme, not to Quiet Paper.

## Elevation

Shadows are soft and short. No black smudges, no coloured glows.

| Token | Use |
| --- | --- |
| none | Sidebar rows at rest, toolbar |
| `--elev-rest` | A card that needs to sit on the wash: `0 1px 2px` at 4% |
| `--elev-selected` | The selected card or row: rest shadow plus `0 8px 22px` at about 7% |
| `--elev-sheet` | The open note and dialogs: rest shadow plus `0 12px 32px` at about 8% |

Dark mode uses the same shapes with a little more opacity, still soft. A selected thing is known by a honey wash and this lift, not by a stroke around it.

## Selected state

The same treatment everywhere a thing is current:

- Background: honey mixed about 10% into the paper (`--accent-soft` on dark).
- Elevation: `--elev-selected`.
- No 1.5px ring. No invert. No bold jump heavier than weight 600.
- Focus for keyboard users stays a 2px honey outline on `:focus-visible` only.

## Sidebar

Frosted glass over the wash. Grouped, with 16px between groups.

Order of weight, heaviest first:

1. **New Note.** A quiet row. The plus is a small honey circle; the label is ink, weight 500. No filled bar, no shadow, no ring on hover — hover is a frost tint.
2. **Primary destinations.** All Notes, notebooks, projects. Weight 500. The current one uses the selected state.
3. **Secondary.** Recent notes, counts, tags, Trash, sync, foot links. Muted, weight 400, smaller. They must not compete with notebooks.

Group labels (Projects, Notebooks) are quiet 11px labels, not headings that shout.

## Note list

Cards, not rows with hairlines.

- 8px between cards.
- 12px radius, paper fill at rest only as a whisper; hover may warm the paper slightly.
- Padding 12px by 16px.
- Selected: honey wash plus soft elevation. The title does not change colour to honey; the card does the talking.
- Timestamps and tags stay muted. Tags may use honey ink, never a honey chip filling the row.

## Note and writing surface

The open note is a floating paper sheet, centred, max width about 720px, radius 12px, `--elev-sheet`.

- The pane behind it is clear, so the wash and the list remain the room and the sheet is the page.
- Title, then a quiet meta line, then the writing. 32px padding on the sheet, more below so the last line can breathe.
- Page view is already sheets. Do not wrap those pages in a second sheet.
- Focus mode hides chrome. The sheet remains.

## Formatting toolbar

Minimal by default.

- At rest, formatting floats over a selection. The pinned bar (Aa) is optional.
- The pinned bar shows only everyday controls: paragraph style, font, size, bold, italic, underline. Everything else — colour, lists, tables, layout, comments, references, design — lives under **More**.
- The bar itself is transparent. Icons are muted. The active control is a honey wash, not a raised white pill.
- Do not add a second toolbar row.

## Progressive disclosure

- The right-hand inspector is **closed by default**. One control opens it.
- When open, the first tabs are Outline, Styles, Review and Links. Pages, snapshots, writing checks, thesaurus, clipboard, selection and search sit behind **More tools** in that inspector.
- Research beside a chapter, comments, and snapshots are the same idea: present when opened, absent otherwise.
- A single writing pane is the default. Splits, extra tabs and “open beside” are choices. Do not start a session in a multi-pane layout.

## Project and writing mode

A project uses the same materials.

- The outline’s current chapter is the selected state (honey wash, soft lift), not a loud block.
- The chapter and the manuscript are the same floating sheet as a note, with the same title scale.
- Index cards are paper, radius 12px, soft shadow. The status stripe stays, because it means something.
- The corkboard sits on the wash, not on a second grey panel.

## Empty states and first run

- Say what is true in one sentence, then one action.
- The action is a quiet button, not a billboard.
- The welcome screen leads with the paper: a short title, one line, three ways to start. No extra chrome.

## What this system refuses

- Radii above 12px.
- A second accent colour.
- Selected states drawn as strokes around the whole object.
- Power tools pinned open “so people can find them”.
- Mixing a new feature into a visual pass.
