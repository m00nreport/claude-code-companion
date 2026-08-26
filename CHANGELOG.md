# Changelog

## 0.1.1

The first release.

### Added

- An **Output panel** ("Claude Code Companion") that shows errors you can read
  and copy, instead of hiding them where nobody looks.
- The plan now reports where it stands on every turn, so the pin no longer sits
  on an old step while the work moves on.
- A LICENSE (MIT).

### Changed

- **The context meter is always on screen.** It used to appear only when the
  window was nearly full, which left you with no way to see it coming. It turns
  amber at 80% and red at 90%, and you can switch it off in Settings.
- **A new panel opens with the strips folded**, so it starts quiet.
- The plan limit meter no longer turns amber. It fills as you use your plan and
  empties on its own, so there is nothing to warn about.
- The extension does not run in untrusted folders, because a session can run
  shell commands in the folder you have open.

### Fixed

- **Reads are now limited to the folder you have open.** Before, the panel could
  read any file on the machine without asking first.
- **The panel no longer writes your conversation to a log file.** Old log files
  are left where they are and can be deleted by hand.
- Your phone can no longer put a session into "Allow everything", and a
  permission set from the phone no longer carries over to other sessions.
- Closing a tab while the session was still starting left a `claude` process
  running.
- Questions and plans from a closed session stayed on screen, where they could
  be answered into the wrong conversation.
- An image sent from the phone reached the model but did not show in the panel.
- Enter did nothing on the questions card.
- Sending a message made the plan disappear while the work was unfinished.
- The microphone forgot its language after a stop or an error.
- The panel was slow while the model was thinking.
