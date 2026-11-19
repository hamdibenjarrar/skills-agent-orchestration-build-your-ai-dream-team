# Project Pulse implementation plan

## Goal

Build Project Pulse, a small static dashboard that shows Mona's team projects at a glance: name, owner, status, recent activity and priority, in a polished card layout.

## Phases

1. Data: define the project data model and sample data.
2. Design: Designer sets the layout, hierarchy, status badges, colors and accessibility rules.
3. Build: Coder implements the markup, styles and data loading.
4. Run: Coder adds the VS Code launch configuration.
5. Validation: Orchestrator checks every file against the brief.

## File assignments

| File | Owner | Purpose |
| --- | --- | --- |
| `app/project-data.json` | Coder | Top level `projects` array. Each project has `name`, `owner`, `status`, `recentActivity` and `priority`. |
| `app/index.html` | Coder, with Designer guidance | Page titled Project Pulse. Links `styles.css`, fetches `project-data.json` and renders one `project-card` per project. |
| `app/styles.css` | Coder, with Designer guidance | `.dashboard` grid, `.project-card` cards with rounded corners, shadows, status badges and a responsive layout. |
| `.vscode/launch.json` | Coder | Launch configuration "Run Project Pulse Dashboard" that serves the `app` directory with `python3 -m http.server 5500` and opens `index.html`. |

## Designer responsibilities

- Card based layout with clear visual hierarchy.
- Status and priority badges that do not rely on color alone.
- Accessible markup: landmarks, headings, readable contrast and focus styles.
- Responsive grid that works on small and large screens.

## Coder responsibilities

- Implement the three app files and the launch configuration.
- Keep `launch.json` strict JSON with no comments.
- Show a friendly message if the data cannot be loaded.

## Dependencies

- `app/project-data.json` defines the fields that `app/index.html` renders, so the data shape comes first.
- `app/styles.css` depends on the class names in `app/index.html` (`dashboard`, `project-card`).
- `.vscode/launch.json` depends on the final location of `app/index.html`.

## Parallel work decisions

- The Designer can write the visual guidance while the Coder writes `app/project-data.json`, since they do not touch the same file.
- `app/index.html` and `app/styles.css` are built after the design guidance, and can be written in parallel once the class names are agreed.
- `.vscode/launch.json` can be created in parallel with the styling work.

## Validation expectations

- `app/project-data.json` parses as JSON and has a top level `projects` key with all five fields per project.
- `app/index.html` contains the title Project Pulse, references `styles.css` and `project-data.json`, and renders `project-card` elements showing status, recentActivity and priority.
- `app/styles.css` contains `.dashboard`, `.project-card`, `border-radius` and `box-shadow`.
- `.vscode/launch.json` parses as JSON and the "Run Project Pulse Dashboard" launch opens `http://localhost:5500/index.html`, not a directory listing.
