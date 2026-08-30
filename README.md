# Octals To-Do App

A single-file, browser-based student dashboard. It started as a to-do list and grew into a small customizable workspace: a drag-and-drop grid of widgets (to-do, priority matrix, pomodoro timer, class schedule, quick links, clock, and a couple of countdowns) that autosaves to your browser.

<img width="1920" height="1080" alt="Screenshot 2026-07-11 172321" src="https://github.com/user-attachments/assets/b321c2d5-634b-4883-8e9b-448e964c7080" />

Open `StudentDashboard.html` in any modern browser and it just works. No install, no server, no build step.

## Tech stack

- **HTML**: the whole app lives in one `.html` file.
- **CSS**: plain CSS3, no framework. Uses custom properties (CSS variables) for a consistent color/spacing system and a light grid/flexbox layout.
- **JavaScript**: vanilla ES6+, no libraries or frameworks. Handles the widget system, drag/resize logic, timers, and rendering.
- **Google Fonts**: Inter (UI text) and Lora (headings/numbers), loaded via a CDN link.
- **Storage**: `localStorage`, with an in-memory fallback if the browser blocks it (e.g. private/incognito edge cases), so your layout and data persist between visits without a backend.

That's it. No npm, no bundler, no dependencies to install.

## Getting started

```bash
git clone https://github.com/MisterOctal/Octals-To-Do-App
cd "Octals-To-Do-App"
```

Then just open `StudentDashboard.html` in your browser. There's nothing to build or install.

## Design decisions

I made this app with Claude, few choices worth calling out:

- **One HTML file instead of a split project.** No `src/` folder, no separate CSS/JS files, no build tooling. It can be sent to a friend as a single file, or dropped into any static host, and it works immediately with zero setup.
- **No frameworks.** The app's complexity is small enough that a framework would add overhead (build step, dependencies, bundle size) without real benefit. Vanilla JS keeps it fast and keeps the single-file approach possible.
- **`localStorage` instead of a backend/database.** This is a personal, local-first tool. There's no login system and nothing that needs to sync across devices, so a server would be unnecessary complexity.
- **A widget-grid system instead of a fixed layout.** Different people want different things visible, so the dashboard lets you add, remove, resize, and rearrange widgets rather than hardcoding one layout.
- **Multi-theme customization.** The app evolved from a simple dark/light toggle to a named theme system, allowing users to choose between a clean light mode, a high-contrast "ITS" dark mode, a "Sci-fi teal" mode, and a soft "Claude-inspired" palette.

## Features

- **Customizable widget grid**: add, remove, drag, and resize widgets on a snapping grid; layout is saved automatically. Compact widgets like the to-do list and dailies can be squashed down to 2×2.
- **Edit / view modes**: a "Customize" mode for arranging widgets, and a clean "view" mode for daily use. On small screens it stays in view mode.
- **To-do list widget**: add tasks, check them off, see a live remaining count.
- **Priority matrix widget**: a 2x2 Eisenhower-style matrix (urgent/important quadrants) for sorting tasks by priority.
- **Sticky note widget**: a free-text ruled notepad for quick notes.
- **Pomodoro timer widget**: configurable focus/break lengths with a running countdown.
- **Timer widget**: a continuous productivity stopwatch: start it and it runs until you press stop. It also logs your hours per day and shows a Mon-Sun breakdown for the current week (with a weekly total), so you can see e.g. Monday 7.5 h, Tuesday 5.4 h at a glance. Hovering over the weekly summary reveals a basic visual bar chart of your progress. A running timer survives page reloads and accidental tab closes; it keeps counting and the closed time is credited to your weekly hours.
- **Class schedule widget**: a simple time-sorted list of the day's events/classes.
- **Quick links widget**: shortcuts to frequently used sites (e.g. Gmail, Calendar, Drive).
- **Calendar widget**: a monthly calendar with day selection and dot markers, which automatically pulls in dates from your deadlines.
- **Deadlines widget**: track upcoming due dates with names and dates, sorted by how soon they're due.
- **Dailies widget**: a daily habit tracker with running streaks and a "best streak" record for each habit.
- **Water tracking widget**: track your daily water intake with a customizable goal and a quick-add button.
- **Daily quote widget**: a curated library of over 100 motivational and philosophical quotes to start your day.
- **Widget settings**: a per-widget settings panel for configuring individual widgets.
- **Export / import backup**: save your whole dashboard to a JSON file and restore it later or on another machine.
- **Clock, countdown, and "new year" widgets**: a live clock, a configurable countdown to any date, and a running countdown to next New Year.
- **Editable dashboard title**: rename the dashboard inline.
- **Autosave**: all widget data and layout persist to `localStorage`, with a subtle "saved" indicator. Saves are debounced, and the app also flushes state immediately when the tab is hidden or closed so the last edit is never lost.
- **Delete confirmations**: deleting a task, daily, event, deadline, or link asks "are you sure" first, so a stray click can't wipe something out. This can be turned off with the "Ask before deleting items" checkbox in customize mode (the preference is saved).
- **Reset to default**: one-click reset back to the starter layout/content.
- **Responsive fallback**: customize/drag mode is disabled on narrow screens to avoid a broken mobile editing experience; the dashboard still renders and functions in view mode.
