# Changelog

## 0.1.5

### Changed

- **The microphone is now a switch under Settings > Appearance, and it is off
  until you turn it on.** Dictation is the one feature here that uses your
  Claude sign-in for a request the panel makes itself, rather than for one
  Claude Code makes, and Anthropic reserves that sign-in for Claude Code and
  its own applications. Nothing is removed: the switch is one click, and the
  row explains itself on hover.
- **The Remote button now says whose sign-in it opens the session under.** It
  always used the Claude sign-in already on your machine; the tooltip only
  described what the button did, not what it did it with.
- **The README has a section on what this does with your Claude account** - no
  account or server of its own, no telemetry or analytics of any kind, the
  whole list of what is kept on this machine, and every outbound connection it
  is capable of making.

### Fixed

- **The dictation connection no longer identifies itself as Anthropic's own
  client.** It had been sending two headers copied from the official
  extension, which made its traffic indistinguishable from the real thing.
  That was wrong however it is read, and it is gone.

## 0.1.4

### Changed

- **The bundled Claude Agent SDK is now 0.3.247**, six releases on from 0.3.241.
  Nothing in the panel changes; this is the machinery underneath it keeping up
  with Claude Code itself.

## 0.1.3

### Fixed

- **The model list could open past the bottom of the panel.** In a narrow panel,
  such as a side-by-side editor or a window sharing the screen, the menu that
  opens from Settings had nowhere to go sideways, so it covered Settings and ran
  off the bottom. The last models were cut off and nothing scrolled to them.
  Menus now stay above the message box, whichever way they open.
- **"Allow everything" would not take on a session already running.** Picking it
  showed a banner asking you to start a new session, and only worked once VS
  Code had been restarted. It applies to the session in front of you now.

## 0.1.2

### Fixed

- **The panel could freeze after Stop.** If you sent a message while Claude was
  working and then pressed Stop, the turn ended but the panel kept saying
  "Waiting for Claude" and never moved again.
- Pressing Stop when nothing was running left the spinner on screen.
- If Claude refused to stop, the panel said nothing and looked stuck.

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
