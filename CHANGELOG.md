# Changelog

## 0.2.0

A release of small things you notice, and one whole class of bug: anything the
panel worked out for itself used to disappear when the window reloaded.

### Added

- **Dismiss a plan you have walked away from.** The plan pin only ever left on
  its own when every step finished, so a plan the task moved past sat above the
  message box with a spinner on a step nobody was doing. There is an x on the
  row now. It says `Plan dismissed` in the chat, and it tells Claude too - so
  the next step it takes is not spent putting the same plan back.
- **An arrow back to the newest message.** Scroll up a long way and it appears
  over the chat. Click it to come back; it goes away by itself once you are
  there.
- **A workflow's agents are a table.** They were eight lines of free text that
  lined up nowhere. Now each row has its own columns - what ran, which model,
  the tokens, the time - with a tick when it is done and a red cross when it
  failed. Hover a row and you also see **the prompt that agent was sent**,
  which the panel had never shown at all.
- **Custom answer styles are now offered.** The list used to be the four
  built-in ones, typed out. It is Claude Code's own list now, so a style you
  wrote yourself in `.claude/output-styles/` can be picked like any other.

### Changed

- **Your settings belong to the conversation, not to the extension.** Choose
  Opus in one tab and Haiku in another, reload the window, and each tab comes
  back the way you left it. A new tab still opens with whatever you chose last,
  which is the part that was always right. This is the model, the reasoning
  effort, the answer style, the sending mode, the permission mode and every
  switch.
- **A new tab no longer opens with the recalled memory over the top of it.**
  The list of sessions to reopen is the whole of the opening screen again. The
  memory is still there - it moves to the top of the chat as soon as you say
  something.

### Fixed

- **A link in an answer opened two browser tabs.** One was ours and one was the
  editor's. Now it opens one.
- **A workflow came back from a reload with no agents at all** - `workflow -
  done` over `No agents yet.` Nothing a run reports about itself is written to
  the session file, so the panel keeps its own copy. The phases, the rows and
  their figures all come back now.
- **A dismissed plan came back after a reload.** Same cause: the plan is rebuilt
  from the session file every time a tab reopens, and there is nowhere in that
  file for "the reader threw this away" to live.
- **A reopened session under-reported what it had cost, for the rest of its
  life.** Claude Code starts its own counter over when a session resumes, so
  the first answer after a reload replaced the figure with a smaller one. What
  was spent before is added to it now instead.
- **The answer style you chose was forgotten**, and the menu showed `Default`
  over a session that was running something else. It is remembered now, and the
  row says what is actually in force - including a style set in your own
  `~/.claude/settings.json`, which the panel had no way of knowing about.
- **A slash command came back from a reload as raw XML** in place of the
  command you typed.
- **A session that ran for a long time slowly grew a list it never emptied.**

## 0.1.5

### Added

- **An Answer style row in the settings menu**: Default, Concise, Explanatory
  or Learning. Concise trims the talking rather than the work, Explanatory
  says why as it goes, and Learning teaches while it works and asks you to
  write some of the code yourself. It is chosen as a session starts, so a
  change applies from the next one.

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
