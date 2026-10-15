<!-- markdownlint-disable MD007 -- Unordered list indentation -->
<!-- markdownlint-disable MD010 -- No hard tabs -->
<!-- markdownlint-disable MD033 -- No inline html -->
<!-- markdownlint-disable MD055 -- Table pipe style [Expected: leading_and_trailing; Actual: leading_only; Missing trailing pipe] -->
<!-- markdownlint-disable MD041 -- First line in a file should be a top-level heading -->
# Requirements

This is a product backlog just for pre-v1.0.0 release. After that, bugs, features, and enhancements will be managed in Github Issues.

<!-- TOC ignore:true -->
## Table of contents

<!-- TOC -->

- [Issues](#issues)
- [Template](#template)

<!-- /TOC -->

## Issues

Sorted per the notes in [Template](#template).

- tukzclip: our own clipboard program. Keeps the clipboard after the app that copied closes, and bridges the Wayland and X11 clipboards.
	- ID: 2026101509021629
	- Type: Feature
	- Status: Queued
	- Opened: 20261015-090216
	- Opened by: t00mietum
	- Requirements:
		- A separate project under the tukzedo umbrella.
		- Named 'tukzclip'.
		- A program that shows up as an icon in the system tray.
		- By default, it does two things:
			- Keeps the clipboard contents in memory for a predefined length of time (default 60m).
			- Bridges Wayland and X11 clipboard.
		- Additional optional features, off by default:
			- Convert the contents to (UTF-8) text-only.
			- Run a command-line with the clipboard contents as the argument.
			- Keep a history a user-adjustable X slots long, and for at most Y minutes each.
			- Persist history between runs. (With a warning about secrets being on storage.)
	- Note: we need a clipboard bridge anyway, even if we weren't using Wayfire, because X11 has a "feature" (bug), where if you copy contents from say a text editor, then close that editor before pasting it somewhere, the clipboard contents disappear. This is "surprising", to say the least. Since a clipboard is "global" to a user's session and works between apps, you'd expect that closing the program doesn't clear it. I get that it might be due to "security concerns", but that is a total half-measure.
	- Note: Wayland does the same. The clipboard belongs to the app that set it, and is gone when that app exits.
	- Note: moved here from the lxqtukz backlog, where the paste bug (2026101417551800) led to it.

**Stop here for a next release**

## Template

- Notes:

	- Only use rows that you actually need or expect will be filled in. Always fill in the title, ID, Type, Status, Opened and Created by.

	- The ID is the local time to the hundredth of a second. Opened is when it was written down, which may differ. (Use a keyboard macro and possibly something like project 'zuid' to generate.)

	- Status values meaning: Testing means the fix is in and checks are running or still to run. Waiting on signoff means automated testing passed. Moot means something else changed that made it irrelevant. Canceled means it still applies but was decided against. Waiting for testing means the fix is in and waits on a long CI run or an outside test host. Can't reproduce means a real attempt to reproduce it failed.
		- An item with nothing left for a person to judge skips Waiting on signoff and goes straight to Done. `Clean up the backlog` in the directives says when.

	- As issues are worked, and statuses change, place them in correct sorting order within the list:
		- First by status: Waiting for answers, Waiting on signoff, Testing, Waiting for testing, Can't reproduce, Stalled, Started, Queued, Done, Deferred, Canceled, Moot
		- Then by severity|priority: Critical, High, Avg, Low
		- Then by type: Bugs, [not bugs together]

	- Rows marked [Bug] are for bugs only, and rows marked [Feature] for features and enhancements. Priority and Severity share one row and one scale. Priority is for a Feature or Enhancement, and Severity for a Bug. Children are not nested. They sit at the top level and point back with Parent ID.

Template:

- Title
	- ID: YYYYmmDDHHMMSSNN
	- Type: [Bug|Feature|Enhancement|Task]
	- Status: [Queued|Waiting for answers|Waiting on signoff|Waiting for testing|Started|Testing|Stalled|Can't reproduce|Moot|Canceled|Deferred|Done]
	- Needs local test suite run?:
	- Needs external testing:
	- Priority [Feature|Enhancement] | Severity [Bug]: [Critical|High|Avg|Low]
	- Opened:
	- Opened by:
	- Assigned to:
	- Parent ID:
	- Prereq IDs:
	- Related IDs:
	- Target OS:
	- Test environment:
	- Version and build:
	- Requirements  [Feature]:
		- Hierarchical bulleted list.
	- Steps to reproduce [Bug]:
		- …
	- Incorrect behavior [Bug]:
	- Expected behavior [Bug]:
	- Reproduced [Bug]: [No, or when, where and how]
	- Possible cause [Bug]:
	- Actual cause [Bug]:
		- …
	- Estimated effort: [High|Avg|Low]
	- Actual effort: [High|Avg|Low]
	- Progress log:
		- …
	- Decisions:
		- …
	- Actual fix [Bug]:
	- Branch:
	- Commit:
	- Test case: [Reason not applicable, or CI test case #]
	- Acceptance signoff:
	- Superseded by ID:
	- Closed:
