# Changelog

## 0.5.13

### Added

- **The folder and branch row follows the repository you are working in.** In a
  workspace that holds several repositories, it names the one your session is
  writing to rather than the folder the session started in.

### Fixed

- A reopened session was missing every message from a turn a connection error
  had interrupted, and its plan came back a step behind.
- A question left unanswered when the VS Code window reloaded now says so in
  the conversation.

## 0.5.12

### Added

- **A session says where it is working.** A row above the message box names the
  folder and the branch, and follows a checkout you make in Source Control
  while the tab is open. Switch it off under Settings, Appearance.
- **A session can move into a git worktree of its own.** Before you have said
  anything, press the worktree pill: the session carries on in the same tab and
  the same window, working in a fresh tree beside your repository. It turns
  orange once you are in one.

### Fixed

- The subagent card grew a line while an agent was running and shrank again
  when it stopped.

## 0.5.11

### Fixed

- The plan pin names the step being worked on - `Step 3 of 5` - instead of
  counting the ones behind it.
- The live pin and the line below it gave different numbers of working
  subagents while a workflow was running.

## 0.5.10

### Added

- **The extension is now on Open VSX.** It installs in Cursor, Windsurf and
  VSCodium as well as in VS Code.

### Changed

- The listing shows the subagent tree, a workflow and the plan filling in as an
  animation instead of a still picture.

## 0.5.9

### Changed

- **The extension is now called Companion for Claude Code.** Same extension and
  the same settings; only the name on the Marketplace listing changed. In
  VS Code the side bar icon still reads Claude Code Companion.

## 0.5.8

### Added

- **The panel keeps up while subagents work.** A background agent reporting
  progress no longer rebuilds the whole conversation, so a long session stays
  as smooth as a short one.

## 0.5.7

### Added

- **The panel keeps up while Claude writes.** The streamed reply no longer
  redraws the whole conversation on every word, so typing, scrolling and the
  panel itself stay smooth on a long session.

### Fixed

- The start of a long answer vanished while a subagent was working, and came
  back only when the answer finished.
- Scrolling stuttered while background work was running.

## 0.5.6

### Added

- **Claude can run a command in a VS Code terminal you watch.** It opens a
  terminal of its own in the editor panel, so a test run or a dev server is on
  screen as it happens. Your own terminals are never used.
- **A memory that did not fit is named.** Claude is told which ones were left
  out of the budget and where they are, instead of only how many.
- **A memory can be pinned.** Add `pinned: true` to its front matter and it is
  carried first, whatever its size. There is no opposite.

### Fixed

- Closing a session tab threw "Webview is disposed", once per tab closed.
- A memory whose front matter ran long was sorted by file date instead of its
  own.

## 0.5.5

### Added

- **Messages between Claude sessions show up in the chat.** One session can
  message another on your machine, and both sides are now cards saying who it
  came from or went to. Each is one line until you click it.

### Fixed

- Memories were only found on Windows, so on macOS and Linux none loaded.

## 0.5.4

### Changed

- **The README shows the panel rather than describing it.** Seventeen more
  pictures, one for each feature that had none, each cropped to the thing it
  is about.

## 0.5.3

### Added

- **A compaction says so while it happens.** When the conversation is folded
  into a summary, a line says so where it happens and the strip above the
  message box reads Compacting. If the fold fails, the reason stays on screen.

### Fixed

- A question card opened with its first option looking already chosen.
- The Appearance menu scrolled on a short window instead of opening as tall
  as the room above it.
- Hints disappeared while Claude was working, several times a second.
- Long hints ran as one block of prose; they are paragraphs now.
- The context meter promised auto-compaction at 97%, which is not where it
  happens.
- A Russian message often got an English tab title, and a title could carry
  a typo through from the message it named.

## 0.5.2

### Fixed

- The usage warning claimed you were close to a limit while printing a
  number that said otherwise. It now states the share and leaves the
  judgement to you.
- That same warning was repeated once per turn, so it stacked up the
  transcript.
- A message still in the queue offered Rewind, which had nothing to undo
  yet. Its “in queue” note now sits where that button was.

## 0.5.1

### Fixed

- The Device button did not say that a folder Claude has never been run in
  needs its trust prompt accepted in a terminal first, so the first press
  there failed instead of explaining itself.

## 0.5.0

### Added

- **Your machine, offered to your other devices.** A Device button beside
  Remote in the composer: switch it on and you can start a session in this
  folder from claude.ai or the Claude app. It stays on across a window
  reload.
- **Session History says which sessions were started somewhere else**, so the
  ones that came from elsewhere are not lost among the rest.
- **A switch to hide the Remote and Device buttons**, under Appearance. One
  that is connected stays on screen either way.

### Fixed

- Sessions started from another device did not appear in Session History.
- The Remote hover named the session by an id instead of its title.
- Sending a message shifted the transcript when Claude picked it up.

## 0.4.0

### Added

- **Claude can read your VS Code terminals.** It sees what is running there and
  what it printed, so it stops starting a service that is already up and stops
  asking you to paste a log. Only terminals inside VS Code; one it could not
  follow is reported as unreadable rather than as idle. New `terminals`
  setting, on by default.
- **Sessions name themselves.** The tab and the history list get a real title
  instead of the first line you typed. `aiSessionTitles` turns it off.
- **The history list is wider**, so titles are no longer cut off.
- **The command menu shows what each agent is for.**
- **Editor menus and keyboard shortcuts reach the composer.** Right-click a
  selection for Ask, Explain or Add tests; right-click a file to start a
  session with it; shortcuts to send the selection and to jump to the
  conversation.
- **The live status line says what Claude is doing** - thinking or writing -
  instead of only that it is busy.
- **Dictation languages are listed by name**, with a field for a language code
  that is not on the list.

### Fixed

- A message sent while Claude was working could disappear after a reload.
- The "Recalled from memory" line landed in the wrong place, or out of sight.
- Recent Sessions showed six rows instead of ten.
- Time-ago labels were rounded twice and could be off by an hour.
- Reopening a session is faster.
- Turning the terminals setting off now stops collection, not just the tools.

## 0.3.0

Three things the panel could not show you before, and one file that was being
loaded after you had told it not to be.

### Added

- **A slash command that runs on its own now shows its work.** Commands like
  `/code-review` do their thinking in a session of their own, and the panel
  used to show nothing at all while they did it - no row, no progress, not even
  a spinner - so a review that took a minute was indistinguishable from a panel
  that had stopped. There is a box for it now, named after the command you
  typed, and it fills in as the work happens: what it is reading, what it is
  running, what it is thinking. It says `running` with a count of steps while it
  goes and `done` when it lands, and it is drawn differently from the agents
  Claude starts for itself, because one is something you asked for by name.
- **A message you send while Claude is working says whether it is waiting.**
  You can type while a turn is in flight, but the message looked the same
  whether it had been picked up or was still sitting in line. It now says
  `in queue` until the moment it is actually taken into the work, and stops
  saying it then rather than when the whole turn ends.
- **Hints that fit what they are describing.** Every hover hint in the panel is
  drawn by the panel now. They wrap onto several lines, so the ones that carry
  a whole prompt or an agent's answer are readable rather than a single line
  running off the edge - and they appear on macOS, where the system ones were
  reported missing.

### Fixed

- **A CLAUDE.md you excluded was loaded anyway, if you wrote the drive letter
  in capitals.** On Windows, a pattern written `C:/work/CLAUDE.md` never
  matched, so the file it named went on loading every session while the setting
  looked correct. Measured on this workspace: 32,753 instruction tokens with
  the exclusion silently doing nothing, 5,931 with it working. Written either
  way, it works now.
- **The context hover now adds up to the whole window.** It listed the three
  biggest things in the context and stopped, so a fresh session reading 23%
  full showed 38k of a 45k total and simply did not say where the other 7k had
  gone. Every category is listed now, smallest included.
- **Your session list no longer fills with sessions you never opened.** Work
  Claude runs in the background leaves its own record beside yours, and the
  list was showing those too - five of eleven rows on a new tab, in one case.
  Only sessions somebody actually opened are offered now.
- **The history list offers ten sessions instead of hiding five behind a
  scroll.** It said fifteen, which pushed the message box down and put the last
  rows below the fold on a laptop or in a narrow side panel.
- **The plan-limit meter switch turns the meter off.** Unticking it did nothing
  once a limit passed 80%, which is exactly when anyone opens that menu. Off
  means off now, at any percentage.
- **A collapsed plan is no longer one stray click from being thrown away.** The
  x that dismisses it is gone entirely while the pin is collapsed, rather than
  merely invisible - it could still be clicked, and still be reached with Tab.
- **Removing an attachment puts the cursor back in the message box.** Removing
  a chip, clearing them all, or waving away the file you have open used to drop
  focus onto the page, so the next thing you typed went nowhere.

## 0.2.1

The numbers above the message box used to stand still for as long as Claude was
working, and jump the moment it stopped.

### Fixed

- **"The limit is reached" is now red, and readable.** It was the hardest line
  on screen to read while being the most important one on it: it shared a
  colour with the line that only says the limit is CLOSE, and that colour came
  from a theme setting almost no theme sets, so on many themes it landed
  somewhere dim. The two now look different, because they mean different
  things - one is advice while your work still goes through, the other means
  nothing goes through until the window resets.
- **The cost, the token count and the context bar now move while Claude works.**
  They only ever updated when a turn finished, so a long piece of work showed
  the same figures from beginning to end - and on a session that had been quiet
  for a while, that reads as a panel that has stopped. They are read from Claude
  Code itself every couple of seconds now, and they are the same numbers it
  would report at the end, only sooner. Nothing is estimated.

### Changed

- **Both plan limits are shown, not whichever one is fuller.** The pill showed
  a single percentage with no way to tell which limit it was about, so a weekly
  limit filling up behind a quiet five-hour one had nothing on screen to say
  so. It reads `H 84% - W 46%` now: **H** for the five-hour window, **W** for
  the weekly one, each always in the same place. Hover it for when each one
  resets. It still appears on its own once either window passes 80%, and the
  "Plan limits" switch still keeps it visible all the time.

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
