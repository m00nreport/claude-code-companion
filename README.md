<p align="center">
  <img src="https://raw.githubusercontent.com/m00nreport/claude-code-companion/main/public/icon.png" width="112" alt="Claude Code Companion">
</p>

# Claude Code Companion for VS Code

**Claude Code Companion** is an extension for Anthropic's official Claude Code.
It is built on the same public `@anthropic-ai/claude-agent-sdk`. It adds its own
panel that runs its own chat and shows the parts of a long run that you usually
cannot see: what the subagents are doing right now, what the model is thinking,
how the plan is going, and how much each step cost.

## What only this panel does

- **Live Subagent Tree.** A big task can start smaller agents to do parts of
  the work. This panel shows them all in a tree. For each one you see its name,
  if it is still working, and how many tokens it used. You can stop any one of
  them, so you always know what is going on.

  ![The subagent tree, with running and finished agents and a Stop all button](https://raw.githubusercontent.com/m00nreport/claude-code-companion/main/public/features-images/sub-agents.png)

- **Live Thinking.** You can watch the model think while it works. The words
  come in slowly, so a long thought is easy to read. You can show one line, a
  few lines, or all of it.

  ![The live strip showing the model's thinking as it works](https://raw.githubusercontent.com/m00nreport/claude-code-companion/main/public/features-images/live-thinking.png)

- **Task Planner.** The model makes a to-do list and keeps it at the top of the
  chat. Each step gets a check when it is done. When it finishes, you can see
  how long each step took and how many tokens it used.

  ![The plan pinned above the chat, and the finished plan with time and tokens for each step](https://raw.githubusercontent.com/m00nreport/claude-code-companion/main/public/features-images/task-planner.png)

- **Stop All.** Some agents keep working in the background after a turn ends.
  One button stops all of them at once.
- **Send Modes - Steer, Interrupt, Queue.** You can send a message while the
  model is still working. **Steer** adds it to the work now. **Interrupt** stops
  the work now. **Queue** waits until the work is done. You pick the one you want
  for each message.
- **Remote Control.** Turn on one switch to open the session in the Claude app
  on your phone. From the phone you can type, allow a tool, change the model, or
  stop the work. It is full control, not just reading.

## Everything the official extension does, too

- Chat in an editor tab, with live Markdown replies and code blocks you can copy
- Asks you before it runs a tool
- Shows file changes as a diff, and lets you undo them
- Plan mode: you see and agree the plan before the work starts
- Slash commands - agents, skills, and more
- Add files with `@`, paste or drop images, and send the file you have open
- Answer the model's questions right in the panel
- Shows the cost, the tokens, and how full the context is
- Past sessions: open, rename, and go back to them
- Voice input (dictation)
- Follows your VS Code theme, light or dark

## Small things you feel every day

- **Web search with its sources.** When the model searches the web, you see how
  many sources it found and which sites they came from. Click one to open it.
- **File names you can click.** When the model writes a file name in its answer,
  the panel checks that the file is really there and makes it a link. Click it
  to open the file, at the right line.
- **A line where the chat was compacted.** When old messages are summarised to
  free up room, you see where it happened and how much was saved.
- **You know it is waiting, not stuck.** If the model has to wait or try again,
  the panel says that instead of looking frozen.
- **Your own answer to a question.** Every question card has an "Other" row, so
  you are never stuck with only the options the model thought of.
- **Click any image to see it big.**

## The settings menu

Open the settings menu in the message box to set:

- **Model** - all the models Claude Code offers, plus other Anthropic models you
  add yourself (see `claudeCodeCompanion.olderModels` below).
- **Effort level** - how hard the model thinks, from low to max.
- **Send mode** - Steer, Interrupt, or Queue (see above).

![The model menu, with the models Claude Code offers and older ones you add yourself](https://raw.githubusercontent.com/m00nreport/claude-code-companion/main/public/features-images/settings-models.png)

- **Appearance** - turn parts of the panel on or off:
  - **Activity strip** - the live strip and subagent list above the box
  - **Live plan pin** - keep the plan at the top while the model works
  - **Cost counter** - what this session has cost
  - **Token counter** - how many tokens it has used
  - **Context meter** - how full the context is
  - **Plan limit meters** - your 5-hour and weekly limits
  - **Tool call chain** - open tool calls instead of folding them

![The Appearance menu, with a switch for each part of the panel](https://raw.githubusercontent.com/m00nreport/claude-code-companion/main/public/features-images/settings-appearance.png)

Next to the menu you can also set the **permission mode** - ask before each
tool, allow edits, or allow everything.

## What it needs

Claude Code itself. If you use the official extension, you already have it. If
not, install it once:

```
curl -fsSL https://claude.ai/install.sh | bash
```

or with npm:

```
npm install -g @anthropic-ai/claude-code
```

If your copy is in a special place, set `claudeCodeCompanion.claudePath` in
Settings.

## Getting started

Click the Claude Code Companion icon on the left side bar and start a new
session. It opens in an editor tab. You can also press `Ctrl+Alt+C`
(`Cmd+Alt+C` on a Mac).

## Settings

- `claudeCodeCompanion.claudePath` - where the `claude` program is, if it is in
  a special place.
- `claudeCodeCompanion.olderModels` - extra model names to add under the ones
  Claude Code shows.
- `claudeCodeCompanion.dictationLanguage` - the language the microphone listens
  for.
- `claudeCodeCompanion.remoteAtStartup` - open every new session on claude.ai
  right away, so you can read and answer it from your phone. **Off by default.
  Read this before you turn it on:** it lets your phone control this computer,
  and anyone signed in to that account can control it too.
