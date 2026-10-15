<!-- markdownlint-disable MD007 -- Unordered list indentation -->
<!-- markdownlint-disable MD010 -- No hard tabs -->
<!-- markdownlint-disable MD033 -- No inline html -->
<!-- markdownlint-disable MD055 -- Table pipe style [Expected: leading_and_trailing; Actual: leading_only; Missing trailing pipe] -->
<!-- markdownlint-disable MD041 -- First line in a file should be a top-level heading -->
# Design

## Summary

On both X11 and Wayland, the clipboard belongs to the app that set it, and it's gone when that app exits. Under wlroots compositors such as Wayfire, an X11 app also can't use the clipboard unless an X11 window has focus. tukzclip takes a copy of the clipboard as it changes, holds it for a set time, and offers it to both sides.

The requirements are in the backlog item.

## Open questions

- Toolkit and tray: tukzedo's own apps lead with Rust. The tray icon would go through StatusNotifierItem, which the LXQt panel shows.
- How the Wayland side reads the clipboard without focus: the `ext-data-control-v1` protocol, or the older `wlr-data-control`, depending on what the compositor offers.
- The X11 side: Xwayland's selections, through an X11 connection of its own.
