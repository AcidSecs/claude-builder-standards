---
name: builder-standards
description: Set a build style and house rules before Claude builds an app or game for the user. Use when the user starts building an app or game, says "how should my buttons / icons look", "set my build style", "build standards", or asks about licences, reusable code or read-aloud buttons for something they build.
---

# Builder Standards

Goal: every app or game Claude builds for this user follows THEIR choices, not Claude's guesses. All rules are defaults the user can change or switch off. Apps and games are asked separately, because they usually want different looks.

## Step 0: settings
Read `Documents\ClaudeSetup\settings.json`. If `modules.builder_standards` is not true, say "Builder Standards is off" and stop. Saved choices live in `builder.apps` and `builder.games`. If a choice for the thing being built is already saved, use it silently.

## The quick questions (ask ONE at a time; offer "choose for me" every time)
Ask about **apps** or **games** first. Then:
1. **Icons:** flat and simple, outlined, rounded and soft, 3D, or hand-drawn? (Show the examples in STYLE_EXAMPLE.md.)
2. **Buttons:** square, softly rounded, fully round (pill), or 3D? Big or small?
3. **Colours:** a few words ("calm and blue", "warm and bright") or "match my logo".
4. **Text size and font feel:** comfortable, large, or compact?
5. **Match everything else?** Should new screens copy the look already in the app? (default yes)
Then offer "more detail?" for: icon sizes, corner roundness, shadows, spacing, light or dark mode, animation level. Save the answers to settings after the user says OK.
The user can skip the questions and fill in STYLE_EXAMPLE.md themselves; read it if it exists.

## House rules (each one on/off, default shown)
- **Read-aloud button** (on): any screen with more than a paragraph of text gets a Read aloud button.
- **Licence check** (ask once: "Will you sell what you build?"): if yes, use only code, fonts, images and tools that are free for commercial use, follow each licence's conditions (credit, keep the licence text), and keep licences that force you to share your own code out unless the user says otherwise. Tell the user only when something blocks the work, in plain words. If no (personal project), say nothing about licences.
- **Reusable modules** (on): anything with code is built as a module the user can reuse in other apps, with a file saying exactly what must be installed and how (or install automatically, for example from a requirements file).
- **Tick-box guides** (on): whenever the user must do a multi-step job themselves, give a detailed tick-box guide page instead of a long reply; about five small steps for every real step, with the reason in brackets, and a copy button for anything to type.
- **Plain-English summary** (on): every build ends with a short summary: what was done, what is open, and the order to do it in.
- **Docs tell the truth** (on): README and how-to text must match the current build; every new feature is easy to find and easy to turn off.

## Health check
On request: settings readable; saved choices present for apps and games; STYLE_EXAMPLE.md present. If something fails, search Anthropic's current docs, PROPOSE a fix, ASK before changing anything.

## Safety
Nothing is sent anywhere. This skill only reads and writes the settings file and the style sheet.

## Guides for steps the user must do
Whenever the user must do a multi-step job themselves (connect an app, install something, request a download), do not write a long reply. Make a tick-box guide: copy `guide/GUIDE_TEMPLATE.html` (in this plugin's folder) to a new file in the user's Documents folder, change only the GUIDE object near the bottom, and follow the instructions at the top of the template. Make it extremely detailed: about five small steps for each real step, plain English, the reason in brackets, a copy chip for anything to type, and only the steps a human must do. Keep the chat reply short and point to the guide.
